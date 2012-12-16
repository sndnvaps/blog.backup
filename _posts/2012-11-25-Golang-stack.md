---
layout: post
style: [syntax]
title: Go语言stack package
---




{% highlight go linenos %}

//$GOROOT/src/pkg/stacker/stack/stack.go
// create by sndnvaps<sndnvaps@gmail.com>
//date : 2012,11,20 15:36 
package stack 
import "errors"

type Stack []interface{}

func (stack Stack) Len() int { // func Len() 
	return len(stack)
}

func (stack *Stack) Push(x interface{}) { //func Push()
	*stack = append(*stack,x)
}

func (stack Stack) Top() (interface{},error) { //func Top()
	if len(stack) == 0 {
		return nil,errors.New("Can't Top() an empty stack")
	}
	return stack[len(stack)-1],nil
}


func (stack *Stack) Pop() (interface{},error) {
	theStack := *stack
	if len(theStack) == 0 {
		return nil, errors.New("Can't Pop() an empty stack")
	}
	x := theStack[len(theStack)-1]
	*stack = theStack[:len(theStack)-1]
	return x,nil
}

{% endhighlight %}
