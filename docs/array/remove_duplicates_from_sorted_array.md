# Remove Duplicates from Sorted Array

**Input:** arr[] = {12, 15, 15, 20, 20, 20, 20} </br>
length: 7 </br>
**Output:** arr[] = {12, 15, 20} </br>
length: 3

**Input:** arr[] = {16, 16, 16} </br>
length: 3 </br>
**Output:** arr[] = {16} </br>
length: 1

## Naive Approach

```
package main

import (
	"fmt"
)

func main() {
	// arr := []int{12, 15, 15, 20, 20, 20, 20} // [12 15 20]
	arr := []int{16, 16, 16} // [16]
	result := removeDups(arr)
	fmt.Println("arr[] =", result)
	fmt.Println("length =", len(result))
}

func removeDups(arr []int)  []int {
	var temp []int
	temp = append(temp, arr[0])
	result := 1
	for i := 1; i < len(arr); i++ {
		if temp[result-1] != arr[i] {
			temp = append(temp, arr[i])
			result++
		}
	}
	for i := 0; i < result; i++ {
		arr[i] = temp[i]
	}
	return arr[:result]
}
```

**Time Complexity:** O(n)
**Space Complexity:** O(n)

## Efficient Approach

```
package main

import (
	"fmt"
)

func main() {
	// arr := []int{12, 15, 15, 20, 20, 20, 20} // [12 15 20]
	arr := []int{16, 16, 16} // [16]
	result := removeDups(arr)
	fmt.Println("arr[] =", result)
	fmt.Println("length =", len(result))
}

func removeDups(arr []int) []int {
	result := 1
	for i := 1; i < len(arr); i++ {
		if arr[i] != arr[result-1] {
			arr[result] = arr[i]
			result++
		}
	}
	return arr[:result]
}
```

**Time Complexity:** O(n)
**Space Complexity:** O(1)

**Note:** we are using `result` variable to keep track to unique elements in array.