# Second Largest Element in Array

**Input:** arr[] = {10, 5, 6, 15} </br>
**Output:** 0 // index of 10

**Input:** arr[] = {30, 15, 23, 9, 28} </br>
**Output:** 4 // index of 28

**Inpute:** arr[] = {15, 15, 15} </br>
**Output:** -1 // No second element

## Naive Approach

```
package main

import (
	"fmt"
)

func main() {
	// arr := []int{10, 5, 6, 15}
	// arr := []int{30, 15, 23, 9, 28}
	arr := []int{15, 15, 15}
	secLargest := getSecondLargest(arr)
	if secLargest == -1 {
		fmt.Println("No sencond largest found")
	} else {
		fmt.Println("largest element at index", secLargest)
		fmt.Println("largest element", arr[secLargest])
	}

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

func getSecondLargest(arr []int) int {
	first := getLargest(arr)
	second := -1
	for i := 0; i < len(arr); i++ {
		if arr[first] != arr[i] {
			if second == -1 {
				second = i
			} else if arr[second] < arr[i] {
				second = i
			}
		}
	}
	return second
}
```

## Efficient Approach

- arr[i] > arr[largest]: res = largest, largest = i
- arr[i] == arr[largest]: Ignore
- arr[i] < arr[largest]:
	- res == -1: res = i
	- arr[i] <= arr[res]: Ignore
	- arr[i] > arr[res]: res = i

```
package main

import (
	"fmt"
)

func main() {
	arr := []int{10, 5, 6, 15}
	// arr := []int{30, 15, 23, 9, 28}
	// arr := []int{15, 15, 15}
	secLargest := getSecondLargest(arr)
	if secLargest == -1 {
		fmt.Println("No sencond largest found")
	} else {
		fmt.Println("largest element at index", secLargest)
		fmt.Println("largest element", arr[secLargest])
	}

}

func getSecondLargest(arr []int) int {
	first := 0
	second := -1
	for i := 1; i < len(arr); i++ {
		if arr[i] > arr[first] {
			second = first
			first = i
		} else if (second == -1 || arr[i] > arr[second]) && arr[i] != arr[first] {
			second = i
		}
	}
	return second
}
```

**Time Complexity:** O(n)