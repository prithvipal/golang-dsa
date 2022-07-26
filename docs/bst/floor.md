# Find Floor of Given Number

## Implementation

### Recursive 
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
		data: 50,
		left: &Tree{
			data: 30,
			left: &Tree{
				data: 20,
			},
			right: &Tree{
				data: 40,
			},
		},
		right: &Tree{
			data: 70,
			left: &Tree{
				data: 60,
				left: &Tree{
					data: 55,
				},
				right: &Tree{
					data: 65,
				},
			},
			right: &Tree{
				data: 80,
			},
		}}

	res := findFloor(root, 51)
	if res != nil {
		fmt.Println(*res)
	} else {
		fmt.Println(res)
	}

}

func findFloor(root *Tree, val int) *int {
	if root == nil {
		return nil
	}
	if root.data == val {
		return &val
	} else if root.data < val {
		res := findFloor(root.right, val)
		if res == nil {
			return &root.data
		}
		return res
	} else {
		return findFloor(root.left, val)
	}

}

```

### Iterative