# Add One in Lisked List Digit


**Input:** |1| -> |3| -> |9| -> |9| <br/>
*Digit is:* 1399 <br/>
1399 + 1 = 1400<br>
**Output:** |1| -> |4| -> |0| -> |0|

**Input:** |9| -> |9| -> |9| -> |9| <br/>
**Output:** |1| -> |0| -> |0| -> |0| -> |0| <br/>

## Implementation

```
package main

import "fmt"

func main() {
	head := initialize(19999)
	head = addOne(head)
	printResult(head)
}

func initialize(n int) (head *Node) {

	var arr []int
	for n > 0 {
		data := n % 10
		arr = append(arr, data)
		n = n / 10
	}
	var curr *Node
	for i := len(arr) - 1; i >= 0; i-- {
		if i == len(arr)-1 {
			curr = &Node{data: arr[i]}
			head = curr
		} else {
			curr.next = &Node{data: arr[i]}
			curr = curr.next
		}
	}

	return head
}

func printResult(head *Node) {
	for head != nil {
		fmt.Print(head.data)
		head = head.next
	}
	fmt.Println()

}

type Node struct {
	data int
	next *Node
}

func addOne(head *Node) *Node {
	var stack []*Node
	curr := head
	for curr != nil {
		stack = append(stack, curr)
		curr = curr.next
	}
	carry := 1
	for i := len(stack) - 1; i >= 0; i-- {
		ele := stack[i]
		add := ele.data + carry
		ele.data = add % 10
		carry = add / 10
	}
	if carry > 0 {
		newHead := &Node{data: carry}
		newHead.next = head
		return newHead
	}
	return head
}

```

