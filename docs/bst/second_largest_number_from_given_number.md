# Second Largest Number from Given Number

              45
            /    \
          40       60
        /   \	   /  \ 
      20	 42   50   70

In given above tree, </br>
if given number n as 70 then result should be 60 </br>
if given number n as 60 then result should be 45 </br>
if given number n as 43 then result should be 42 </br>
if given number n as 15 then result should be NOT FOUND </br>

## Implementation

```golang
package main

import "fmt"

type Tree struct {
	data  int
	left  *Tree
	right *Tree
}

func main() {
	root := &Tree{data: 45}
	root.left = &Tree{data: 40}
	root.left.left = &Tree{data: 20}
	root.left.right = &Tree{data: 42}

	root.right = &Tree{data: 60}
	root.right.left = &Tree{data: 50}
	root.right.right = &Tree{data: 70}
	result := secondLarge(root, 80)
	if result == nil {
		fmt.Println("Not Found")
	} else {
		fmt.Println(*result)
	}

}

func secondLarge(root *Tree, n int) *int {
	if root == nil {
		return nil
	}
	var result *int
	if root.data < n {
		result = secondLarge(root.right, n)
	} else if root.data > n {
		result = secondLarge(root.left, n)
	}
	if result == nil || *result >= n {
		if root.data > n {
			return nil
		}
		return &root.data
	}
	return result
}
```