# Level Order Traversal

## Implementation

```
package main

import "fmt"

type TreeNode struct {
	Val   int
	Left  *TreeNode
	Right *TreeNode
}

type ListNode struct {
	Val  int
	Next *ListNode
}

func main() {
	root := &TreeNode{
		Val: 10,
		Left: &TreeNode{
			Val: 20,
			Left: &TreeNode{
				Val: 40,
			},
			Right: &TreeNode{
				Val: 50,
				Left: &TreeNode{
					Val: 70,
				},
				Right: &TreeNode{
					Val: 80,
				},
			},
		},
		Right: &TreeNode{
			Val: 30,
			Right: &TreeNode{
				Val: 60,
			},
		},
	}

	levelOrderTraversal(root)
}

func levelOrderTraversal(root *TreeNode) {
	queue := []*TreeNode{}
	queue = append(queue, root)
	for len(queue) > 0 {
		ele := queue[0]
		fmt.Println(ele.Val)
		if ele.Left != nil {
			queue = append(queue, ele.Left)
		}
		if ele.Right != nil {
			queue = append(queue, ele.Right)
		}
		queue = queue[1:]
	}
}

```