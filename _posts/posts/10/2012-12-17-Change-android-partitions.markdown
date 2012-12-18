---
layout: post
uri: /posts/10
permalink: /posts/10/index.html
title : 修改U88内部分区{转载}

---
[原文链接](http://bbs.hiapk.com/thread-1273024-1-1.html)

众所周知，U88 内部有2Gb的闲置用户空间，不插入TF 存储卡时才能用，放入TF卡后，这块存储空间就闲置无法使用了，比较可惜！
 
本人尝试将其中的1Gb划分出来做了 ext2 文件系统 （/dev/block/mmcblk0p15），成功做到了 App to ext2用上这块空间，遇到点小困难
 -----------------------------------
 2011-05-25,20:30更新：
 公司赶一个项目极忙，一个月来只能业余时间偶尔弄一下爱机，今天才有点时间来“搞机”。报告一下情况：
 
用 simplistian 老兄在 66 楼告知的方法一举成功！ app to ext2 for Build-in SD Card （在内置2G 卡中使用 ext2 文件系统安装应用程序）成功获得 1Gb 存储空间。
 -------------------------------------
 2011-06-03 最新更新
 
    今晚（6月3日）终于花了几小时搞定。
 已经成功用手工处理的办法，将内置存储卡的2G 空间划分1G 出来，作为 APP to ext2 ，剩余的 1G 仍然做原有的“存储卡”，不影响使用。
 手工制作的步骤相当复杂，误操作的风险较高，只建议专业玩家继续，普通玩家还是不要弄了。
 
    （本人的惨痛教训，将命令行 mkfs.ext2 .....mmcblk0p15 不小心少输入后面的 “p15”字符，造成整机主存储分区表被清空，导致彻底变砖头，只好拿去华为维修部更换了手机主板，维修部的师傅们没看出人为损坏，给免费更换了。窃喜中…… ^_^）
 
方法概序：只建议具有熟练管理 Linux 知识的玩家操作
 
  1、建立分区
 
        * 用B160 版的 ROM,
        * 系统取得root 权限
        * 复制 busybox 、bash 、e2fsck 到/system/bin 中（可在 dtappas2sd-
 2.7.5.xx.zip压缩包中取得），设置好 755权限；
        * 用 busybox fdisk -l 查看分区表，并复制、记录下分区表；
        * 运行 busybox fdisk /var/block/mmcblk0
        * 小心的将 /var/block/mmcblk0p14 删除，然后重新分区，
        * 新建分区 14 ，重原来的“起始块编号”，划分1Gb 空间，设置分区类型 69 ，得
 到新的 /var/block/mmcblk0p14 分区；
        * 剩余的1G空间全部划分为/var/block/mmcblk0p15，类型为83 （ext分区）
        * 检查无误后 保存，然后重启 。以上步骤中千万不可改动其它的任何分区，切记！
        
        * 重启后再将 /var/block/mmcblk0p14  分区格式化为 vfat 格式:
             busybox mkfs.vfat /var/block/mmcblk0p14
        * 将 /var/block/mmcblk0p15  分区格式化为 ext2 格式(选用 ext2格式的原因是
 busybox 中的 mkfs 只支持 ext2 ):
             busybox mkfs.ext2 /var/block/mmcblk0p15
 
      完成后，分区表应该是这样的：
 

    2、开机自动挂载分区
 
        * 重新 mount /system 分区为读写模式，创建 /system/sd 目录
        * 创建文本文件/system/etc/install-recovery.sh ，并设置为 755 权限
            编辑并保存文件  /system/bin/busybox vi /system/etc/install-recovery.sh
          文件内容如下：
              #!/system/bin/bash
              e2fsck -y /dev/block/mmcblk0p15
              mount -t ext2 -o rw /dev/block/mmcblk0p15 /system/sd
        （记得设置此文件的权限为 755 ： chmod 755 /system/etc/install-recovery.sh ）
 
     3、搬移数据
         
         * 上文第二大步完成后,运行 /system/etc/install-recovery.sh ，然后用 busybox df 命令确认新的 ext2 分区已经挂载到 /system/sd 
        * 搬移 /data/app 到新的 ext2分区:
              /system/bin/busybox cp -a /data/app /system/sd/
              /system/bin/busybox rm -r /data/app
              /system/bin/busybox ln -s /system/sd/app /data/app
         * 搬移 /data/dalvik-cache 到新的 ext2分区:
              /system/bin/busybox cp -a /data/dalvik-cache /system/sd/
              /system/bin/busybox rm -r /data/dalvik-cache
               /system/bin/busybox ln -s /system/sd/dalvik-cache /data/dalvik-cache
   
        * 搬移 /data/oeminfo_ap.log 到新的分区 /system/sd/
            /system/bin/busybox cp /data/oeminfo_ap.log /system/sd/
            /system/bin/busybox rm /data/oeminfo_ap.log
            /system/bin/busybox ln -s /system/sd/oeminfo_ap.log /data/oeminfo_ap.log
    重启后，就完成了。
 
        个人经验：
 
     1、 系统 root 后，先复制 busybox 、bash 、e2fsck 到/system/bin 中，设置好 755权限，然后手机中安装 SSHDroid 软件，打开wifi连接自己的 AP或者宽带路由器，再运行 SSHDroid 软件，这样就可以在 PC 中用 putty 等SSH 终端工具登录手机，此时就与管理操作 Linux 服务器一样，比较方便；
     2、用 SSH 登录后，先运行bash ，在 bash 中敲命令行，效率高一些；
     3、敲入各种命令时（特别是mkfs 命令）最好先在 PC 中的记事本中先输入完成，检查核对无误后，再粘贴到 ssh 终端中，这样可最大程度避免误操作，避免手机变成砖头(本人的惨痛教训换来的经验)。
     4、为了防止误操作发生意外，在做 fdisk  修改之前，先 将 /dev/block/mmcblk0p1 给整体备份出来，预防万一要重建分区表时，可恢复回去：
                备份命令  dd if=/dev/block/mmcblk0p1  of=/HWUserData/boot_bak.img
                万一要恢复时的命令： dd  if=/HWUserData/boot_bak.img of=/dev/block/mmcblk0p1
 
    “凡人”老大已经制作出来了半自动的作品，用另外一种比较安全的办法，很技巧，不过理论上运行速度效率不如我的方法：
             
   [链接](http://www.5irom.com/thread-461-1-1.html)

