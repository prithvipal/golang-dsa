# First Occurance in Sorted Array

## Iterative

```
package main

import "fmt"

func main() {
    idx := firstOccu([]int{5, 10, 10, 15, 20, 20, 20}, 20)
    fmt.Println(idx)
}

func firstOccu(nums []int, target int) int {
	low := 0
	high := len(nums) - 1
	for low <= high {
		mid := (low + high) / 2
		if nums[mid] == target {
			if mid == 0 || nums[mid-1] != nums[mid] {
				return mid
			}
			high = mid
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
    idx := firstOccuRec([]int{5, 10, 10, 15, 20, 20, 20}, 0, 6, 20) //4
    fmt.Println(idx)
}

func firstOccuRec(nums []int, low, high, target int) int {
	if low < high {
		mid := (low + high) / 2
		if nums[mid] == target {
			if mid != 0 && nums[mid-1] == nums[mid] {
				return firstOccuRec(nums, low, mid, target)
			}
			return mid
		} else if nums[mid] < target {
			return firstOccuRec(nums, mid+1, high, target)
		} else {
			return firstOccuRec(nums, low, mid-1, target)
		}
	}

	return -1
}
```