# Delete Middle Element of Singly Linked List

**Input:** 1 -> 2 -> 3 -> 4 -> 5 </br>
**Output:** 1 -> 2 -> 4 -> 5 </br>
***Note:*** If there are odd number of element then delete middle

**Input:** 1 -> 2 -> 3 -> 4 </br>
**Output:** 1 -> 2 -> 4 </br>
***Note:*** If there are even number of element then there will be two middle elements. So we will delete second middle.

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
	deleteMiddle(head)
	for head != nil {
		fmt.Printf("%d ", head.data)
		head = head.next
	}
	fmt.Println()

}

func deleteMiddle(head *Node) {
	fast := head
	slow := head
	pre := head

	for fast != nil && fast.next != nil {
		pre = slow
		slow = slow.next
		fast = fast.next.next
	}
	pre.next = slow.next
}
```

