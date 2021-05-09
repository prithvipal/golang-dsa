# Operations

## Search (unsorted array)

```
package main

import "fmt"

func main() {
	arr := []int{10, 3, 6, 14, 17}
	result := search(arr, 14)
	if result == -1 {
		fmt.Println("Element not found")
	} else {
		fmt.Println("Element found at index:", result)
	}

}

func search(arr []int, ele int) int {
	for i := 0; i < len(arr); i++ {
		if arr[i] == ele {
			return i
		}
	}
	return -1
}
```

**Time Complexity:** O(n)