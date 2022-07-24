# Delete from BST

## Implementation

```
package main

import "fmt"

type Tree struct {
	data  int
	left  *Tree
	right *Tree
}

func main() {
	root := &Tree{
		data: 15,
		left: &Tree{
			data: 5,
			left: &Tree{
				data: 3,
			}},
		right: &Tree{
			data: 20,
			left: &Tree{
				data: 18,
				left: &Tree{
					data: 16,
				},
			},
			right: &Tree{
				data: 80,
			},
		}}

	res := delete(root, 15)
	fmt.Printf("%+v", res)
}

func delete(root *Tree, val int) *Tree {
	if root == nil {
		return nil
	}
	if val < root.data {
		root.left = delete(root.left, val)

	} else if val > root.data {
		root.right = delete(root.right, val)
	} else {
		if root.left == nil {
			return root.right
		} else if root.right == nil {
			return root.left
		} else {
			succ := getSuccesor(root)
			root.data = succ.data
			delete(root.right, succ.data)
		}
	}
	return root
}

func getSuccesor(root *Tree) *Tree {
	curr := root.right
	for curr != nil && curr.left != nil {
		curr = curr.left
	}
	return curr
}

```