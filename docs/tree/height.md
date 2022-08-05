# Height of A Binary Tree

## Implemenation

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

	res := heightOfTree(root)
	fmt.Println(res)
}

func heightOfTree(root *TreeNode) int {
	if root == nil {
		return 0
	}
	leftH := heightOfTree(root.Left) + 1
	rightH := heightOfTree(root.Right) + 1

	if leftH < rightH {
		return rightH
	}
	return leftH
}

```
