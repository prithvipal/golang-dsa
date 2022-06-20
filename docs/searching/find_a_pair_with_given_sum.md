# Find a Pair With Given Sum

## Unsorted Array

**Input:** arr[] = {2, 5, 13, 6, 9, 4}, sum=10 </br>
**Output:** Yes

**Input:** arr[] = {10, 5, 13, 6, 9, 4}, sum=5 </br>
**Output:** No

### Implementation

```
package main

import (
	"fmt"
	"sort"
)

func main() {
	arr := []int{2, 5, 13, 6, 9, 10}
	k := 13
	res := findPairWithGivenSum(arr, k)
	fmt.Println(res)

}

func findPairWithGivenSum(arr []int, target int) bool {
	m := make(map[int]bool)
	for _, ele := range arr {
		if _, ok := m[target-ele]; ok {
			return true
		}
		m[ele] = true
	}
	return false
}
```

## Sorted Array

**Input:** arr[] = {2, 4, 6, 9, 12, 13}, sum=10 </br>
**Output:** Yes

**Input:** arr[] = {3, 4, 6, 9, 10, 13}, sum=8 </br>
**Output:** No

### Implementation

```
package main

import (
	"fmt"
	"sort"
)

func main() {
	arr := []int{2, 5, 13, 6, 9, 10}
	k := 13
	res := findPairWithGivenSum(arr, k)
	fmt.Println(res)

}

func findPairWithGivenSum(arr []int, target int) bool {
	i := 0
	j := len(arr) - 1
	for i < j {
		sum := arr[i] + arr[j]
		if sum == target {
			return true
		} else if sum > target {
			j--
		} else {
			i++
		}
	}
	return false
}
```