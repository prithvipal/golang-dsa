 
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

**Input:** arr[] = {3, 1}, target=1 </br>
**Output:** 1

**Input:** arr[] = {3, 1}, target=3 </br>
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

func searchInSortedRotatedArray(nums []int, target int) int {
	low := 0
	high := len(nums) - 1
	// to find index of lowest value. The index where rotation's value start
	for low < high {
		mid := (low + high) / 2
		if nums[mid] > nums[high] {
			low = mid + 1
		} else {
			high = mid
		}
	}

	// setting new low and high based of array we have our element. Whether rotated sided or other side
	rotIdx := low
	low = 0
	high = len(nums) - 1
	if nums[rotIdx] == target {
		return rotIdx
	} else if nums[rotIdx] < target && target <= nums[len(nums)-1] {
		low = rotIdx + 1
	} else {
		high = rotIdx - 1
	}

	// normal binary search with new low and high
	for low <= high {
		mid := (low + high) / 2
		if nums[mid] == target {
			return mid
		} else if nums[mid] < target {
			low = mid + 1
		} else {
			high = mid - 1
		}
	}

	return -1
}
```

