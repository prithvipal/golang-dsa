# Last Occurance in Sorted Array


## Iterative

```
package main

import "fmt"

func main() {
    idx := lastOccu([]int{5, 10, 10, 15, 20, 20, 20}, 20) // 6
	fmt.Println(idx)
}

func lastOccu(nums []int, target int) int {
	low := 0
	high := len(nums) - 1
	for low <= high {
		mid := (low + high) / 2
		if nums[mid] == target {
			if mid == len(nums)-1 || nums[mid+1] != nums[mid] {
				return mid
			}
			low = mid + 1
		} else if nums[mid] < target {
			low = mid + 1

		} else {
			high = mid - 1

		}
	}

	return -1
}
```

## Recursive

```
package main

import "fmt"

func main() {
    idx := lastOccuRec([]int{5, 10, 10, 15, 20, 20, 20}, 0, 6, 20) // 6
	fmt.Println(idx)
}

func lastOccuRec(nums []int, low, high, target int) int {
	if low <= high {
		mid := (low + high) / 2
		if nums[mid] == target {
			if mid == len(nums)-1 || nums[mid+1] != nums[mid] {
				return mid
			}
			return lastOccuRec(nums, mid+1, high, target)
		} else if nums[mid] < target {
			return lastOccuRec(nums, mid+1, high, target)
		} else {
			return lastOccuRec(nums, low, mid-1, target)
		}
	}

	return -1
}
```