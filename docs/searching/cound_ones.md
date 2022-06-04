# Count One's

We need to count number 1's in given array. This array contains only 0's and 1's. The array is sorted means 1's are followed by 0's. 

**Input:** arr[] = {0, 0, 1, 1, 1} </br>
**Output:** 3


**Input:** arr[] = {1, 1, 1, 1} </br>
**Output:** 4


**Input:** arr[] = {0, 0, 0} </br>
**Output:** 0

**Input:** arr[] = {} </br>
**Output:** 0

```
package main

import (
	"fmt"
)

func main() {
	nums := []int{0, 0, 1, 1, 1} // 3
	// target := 2
	count := countOnes(nums)
	fmt.Println(count)
}

func countOnes(nums []int) int {
	low := 0
	high := len(nums) - 1

	for low <= high {
		mid := (low + high) / 2
		if nums[mid] == 0 {
			low = mid + 1
		} else {
			if mid == 0 || nums[mid-1] == 0 {
				return len(nums) - mid
			}
			low = mid
		}
	}
	return 0
}
```



