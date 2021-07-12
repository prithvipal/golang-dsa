# Reverse a Singly Linked List

**Input:** 1 -> 2 -> 3 -> 4-> 5->  </br>
**OutPut:** 5 -> 4 -> 3 -> 2 -> 1

## Implementation

```golang
package main

import "fmt"

type Node struct {
	data int
	next *Node
}

func main() {
	head := &Node{data: 1}
	head.next = &Node{data: 2}
	head.next.next = &Node{data: 3}
	head.next.next.next = &Node{data: 4}
	head.next.next.next.next = &Node{data: 5}
	head = reverse(head)
	for head != nil {
		fmt.Printf("%d ", head.data)
		head = head.next
	}
	fmt.Println()

}

func reverse(head *Node) *Node {
	curr := head
	var temp *Node = nil
	var pre *Node = nil
	for curr != nil {
		temp = curr.next
		curr.next = pre
		pre = curr
		curr = temp
	}
	return pre
}
```