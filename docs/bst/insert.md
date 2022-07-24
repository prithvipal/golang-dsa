# Insert in BST

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
	res := insert(root, 6)
	fmt.Printf("%+v", res)
}

func insert(root *Tree, val int) *Tree {
	if root == nil {
		return &Tree{data: val}
	}
	if val < root.data {
		root.left = insert(root.left, val)

	} else {
		root.right = insert(root.right, val)
	}
	return root
}

```