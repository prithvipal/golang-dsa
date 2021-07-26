# Sum of All Pair in Sorted Array is Equal to Given Number

**Input**</br>
arr := []int{1, 2, 3, 4, 5}</br>
sum:= 7

**Output:**
[2 5] [3 4]


## Implementation

```golang
package main

import "fmt"

func main() {
	arr := []int{1, 2, 3, 4, 5}
	result := getSumPairs(arr, 7)
	fmt.Println(result)
}

func getSumPairs(arr []int, sum int) [][2]int {
	i := 0
	j := len(arr) - 1
	result := make([][2]int, 0)
	for i < j {
		var pair [2]int
		addition := arr[i] + arr[j]
		if addition == sum {
			pair[0] = arr[i]
			pair[1] = arr[j]
			result = append(result, pair)
			i++
			j--
		} else if addition < sum {
			i++
		} else {
			j--
		}
	}
	return result
}

```
