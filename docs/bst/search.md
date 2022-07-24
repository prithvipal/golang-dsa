# Search in BST

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
	res := search(root, 2)
	fmt.Println(res)
}

func search(root *Tree, val int) bool {
	if root == nil {
		return false
	}
	if root.data == val {
		return true
	}
	if val < root.data {
		return search(root.left, val)
	}
	return search(root.right, val)
}

```