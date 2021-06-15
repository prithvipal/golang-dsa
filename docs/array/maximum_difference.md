# Maximum Differences

Maximum value of a[j] > a[i] such that j>i

**Input:** arr[] = {3, 4, 11, 7, 5, 9, 1} <br>
**Outout:** 8

**Input:** arr[] = {8, 10, 6, 7, 4, 2} <br>
**Outout:** 2

**Input:** arr[] = {20, 30, 40} <br>
**Output:** 20 <br>
Here array is sorted so max diff is last element minus first element.

**Input:** arr[] = {40, 30, 6, 4} <br>
**Output:** -2 <br>
Here array is reverse sorted then output will be negative


## Naive Approach

```
package main

import (
	"fmt"
)

func main() {
	arr := []int{3, 4, 11, 7, 5, 9, 1} // 8
	// arr := []int{8, 10, 6, 7, 4, 2} // 2
	// arr := []int{20, 30, 40} // 20
	// arr := []int{40, 30, 6, 4} // -2
	result := maxDiff(arr)
	fmt.Println(result)
}

func maxDiff(arr []int) int {
	result := arr[1] - arr[0]
	for i := 0; i < len(arr); i++ {
		for j := i + 1; j < len(arr); j++ {
			result = max(result, arr[j]-arr[i])
		}
	}
	return result
}

func max(a, b int) int {
	if a > b {
		return a
	}
	return b
}
```

**Time complexity:** &theta;(n<sup>2</sup>)

## Efficient Approach

```
package main

import (
	"fmt"
)

func main() {
	arr := []int{3, 4, 11, 7, 5, 9, 1} // 8
	// arr := []int{8, 10, 6, 7, 4, 2} // 2
	// arr := []int{20, 30, 40} // 20
	// arr := []int{40, 30, 6, 4} // -2
	result := maxDiff(arr)
	fmt.Println(result)
}

func maxDiff(arr []int) int {
	result := arr[1] - arr[0]
	minVal := arr[0]
	for i := 1; i < len(arr); i++ {
		result = max(result, arr[i]-minVal)
		minVal = min(minVal, arr[i])
	}
	return result
}

func max(a, b int) int {
	if a > b {
		return a
	}
	return b
}

func min(a, b int) int {
	if a < b {
		return a
	}
	return b
}
```

**Time Complexity:** &theta;(n) <br>
**Aux Space:** &theta;(1)