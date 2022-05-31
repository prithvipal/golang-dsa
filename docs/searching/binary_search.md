# Binary Search

## Iterative

```
package main

import "fmt"

func main() {

   // idx := search([]int{1, 2, 3, 4, 5}, 6) //-1
    idx := search([]int{1, 2, 3, 4, 5}, 3) // 2
    fmt.Println(idx)
}

func search(nums []int, target int) int {
	low := 0
	high := len(nums) - 1

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

## Recursive

```
package main

import "fmt"

func main() {
    // idx := searchRec([]int{1, 2, 3, 4, 5}, 0, 4, 6) // -1
    idx := searchRec([]int{1, 2, 3, 4, 5}, 0, 4, 3) // 2
	fmt.Println(idx)
}

func searchRec(nums []int, low, high, target int) int {
	if low > high {
		return -1
	}
	mid := (low + high) / 2

	if nums[mid] == target {
		return mid
	} else if nums[mid] < target {
		return searchRec(nums, mid+1, high, target)
	} else {
		return searchRec(nums, low, mid-1, target)
	}
}
```