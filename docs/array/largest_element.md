# Largest element in array

```
package main

import "fmt"

func main() {
	arr := []int{10, 52, 18, 20}
	largest := getLargest(arr)
	fmt.Println("largest element at index", largest)
	fmt.Println("largest element", arr[largest])
}

func getLargest(arr []int) int {
	largest := 0
	for i := 1; i < len(arr); i++ {
		if arr[i] > arr[largest] {
			largest = i
		}
	}
	return largest
}
```

**Time Complexity:** O(n)