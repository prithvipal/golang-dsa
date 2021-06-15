# Bubble Sort

- Bubble sort is stable
- It is in-place
## Naive Approach

```
package main

import "fmt"

func main() {
	arr := []int{10, 3, 25, 17, 21, 55}
	bubbleSort(arr)
	fmt.Println(arr)
}

func bubbleSort(arr []int) {
	for i := 0; i < len(arr); i++ {
		for j := 0; j < len(arr)-i-1; j++ {
			if arr[j] > arr[j+1] {
				arr[j], arr[j+1] = swap(arr[j], arr[j+1])
			}
		}
	}
}

func swap(a, b int) (int, int) {
	return b, a
}

```

**Time Complexity:** &theta;(n*n)

## Efficient Approach

If array is already sorted or get sorted in middle of iteration.

```
package main

import "fmt"

func main() {
	// arr := []int{10, 3, 25, 17, 21, 55}
	arr := []int{3, 10, 17, 21, 25, 55}
	bubbleSort(arr)
	fmt.Println(arr)
}

func bubbleSort(arr []int) {
	for i := 0; i < len(arr); i++ {
		swapped := false
		for j := 0; j < len(arr)-i-1; j++ {
			if arr[j] > arr[j+1] {
				arr[j], arr[j+1] = swap(arr[j], arr[j+1])
				swapped = true
			}
		}
		if !swapped {
			break
		}
	}
}

func swap(a, b int) (int, int) {
	return b, a
}

```
