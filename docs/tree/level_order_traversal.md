# Level Order Traversal

### Implementation

```
package main

import "fmt"

type TreeNode struct {
	Val   int
	Left  *TreeNode
	Right *TreeNode
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

## Level Order Traversal Line by Line

### Implementation

```
package main

import "fmt"

type TreeNode struct {
	Val   int
	Left  *TreeNode
	Right *TreeNode
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

	levelOrderTraversalLineByLine(root)
}

func levelOrderTraversalLineByLine(root *TreeNode) {
	queue := []*TreeNode{}
	queue = append(queue, root)
	queue = append(queue, nil)

	for len(queue) > 1 {
		ele := queue[0]
		queue = queue[1:]
		if ele == nil {
			fmt.Println()
			queue = append(queue, nil)
			continue
		}
		fmt.Printf("%v ", ele.Val)
		if ele.Left != nil {
			queue = append(queue, ele.Left)
		}
		if ele.Right != nil {
			queue = append(queue, ele.Right)
		}

	}
}

```