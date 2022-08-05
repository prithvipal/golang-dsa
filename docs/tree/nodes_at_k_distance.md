# Print Nodes at K Distance

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
	printNodeAtKDistance(root, 2)
}

func printNodeAtKDistance(root *TreeNode, k int) {
	if root == nil {
		return
	}
	if k == 0 {
		fmt.Println(root.Val)
	} else {
		printNodeAtKDistance(root.Left, k-1)
		printNodeAtKDistance(root.Right, k-1)
	}

}

```