 
 - Given array is sorted and rotated.
 - We it can rotated any number of times

**Input:** arr[] = {10, 20, 30, 40, 50, 8, 9}, target=30 </br>
**Output:** 2

**Input:** arr[] = {100, 200, 400, 10, 20}, target=40 </br>
**Output:** -1

**Input:** arr[] = {100, 200, 400, 10, 20}, target=10 </br>
**Output:** 3

**Input:** arr[] = {100, 200, 400, 10, 20}, target=100 </br>
**Output:** 0

```
package main

import (
	"fmt"
	"sort"
)

func main() {
	arr := []int{10, 20, 30, 40, 50, 8, 9}
	k := 501
	res := searchInSortedRotatedArray(arr, k)
	fmt.Println(res)
}

func searchInSortedRotatedArray(arr []int, target int) int {
	low := 0
	high := len(arr) - 1
	for low <= high {
		mid := (low + high) / 2
		if arr[mid] == target {
			return mid
		}
		if arr[low] < arr[mid] {
			if arr[low] < target && target < arr[mid] {
				high = mid - 1
			} else {
				low = mid + 1
			}
		} else {
			if arr[mid] < target && target < arr[high] {
				low = mid + 1
			} else {
				high = mid - 1
			}
		}
	}
	return -1
}
```

