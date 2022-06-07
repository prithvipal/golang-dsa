# Find The Correct Possition of Given Missing number

- Find the correct index of given missing number
- Return -1 if it is already present

**Input:** arr[]={2, 4, 7, 9}, k= 5 </br>
**Output:** 2

**Input:** arr[]={2, 4, 7, 9}, k= 8 </br>
**Output:** 3

**Input:** arr[]={2, 4, 7, 9}, k= 4 </br>
**Output:** -1

```
package main

import (
	"fmt"
	"sort"
)

func main() {
	arr := []int{2, 4, 5, 7, 8}
	k := 6
	res := findMissingKsPositive(arr, k)
	fmt.Println(res)
}

func findMissingKsPositive(arr []int, k int) int {
	low := 0
	high := len(arr) - 1
	for low <= high {
		mid := (low + high) / 2
		if arr[mid] == k {
			return -1
		} else if arr[mid] < k {
			low = mid + 1
		} else if arr[mid] > k {
			high = mid - 1
		}
	}
	return low
}
```