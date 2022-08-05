# Tree Traversal

## Inorder Traversal

### Implementation
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
	inorder(root)
}

func inorder(root *TreeNode) {
	if root != nil {
		inorder(root.Left)
		fmt.Println(root.Val)
		inorder(root.Right)
	}
}

```

## Preorder Traversal

### Implementation

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
	preorder(root)
}

func preorder(root *TreeNode) {
	if root != nil {
		fmt.Println(root.Val)
		preorder(root.Left)
		preorder(root.Right)
	}
}

```

## Post Order Traversal

### Implementation

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
	postorder(root)
}

func postorder(root *TreeNode) {
	if root != nil {
		postorder(root.Left)
		postorder(root.Right)
		fmt.Println(root.Val)
	}
}

```