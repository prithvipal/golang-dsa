# Check If An Array is Sorted

**Input:** arr[] = {18, 25, 27} </br>
**Output:** Yes

**Input:** arr[] = {18, 30, 30, 99} </br>
**Output:** Yes


**Input:** arr[] = {100} </br>
**Output:** Yes

**Input:** arr[] = {100, 20, 200} </br>
**Output:** No

**Note** <br>
- We are only considering array wheree array are in assending order <br>
- It there are duplicate then is also true. Ex. 2nd example above

## Naive Approach


```
package main

import (
	"fmt"
)

func main() {
	arr := []int{18, 25, 27} // Yes
	// arr := []int{18, 30, 30, 99} // Yes
	// arr := []int{100} // Yes
	// arr := []int{100, 20, 200} // No
	result := isArraySorted(arr)
	if result {
		fmt.Println("Yes")
	} else {
		fmt.Println("No")
	}

}

func isArraySorted(arr []int) bool {
	for i := 0; i < len(arr); i++ {
		for j := i + 1; j < len(arr); j++ {
			if arr[i] > arr[j] {
				return false
			}
		}
	}
	return true
}
```

**Time Complexity:** O(n2)

## Efficient Approach

```
package main

import (
	"fmt"
)

func main() {
	// arr := []int{18, 25, 27} // Yes
	// arr := []int{18, 30, 30, 99} // Yes
	// arr := []int{100} // Yes
	arr := []int{100, 20, 200} // No
	result := isArraySorted(arr)
	if result {
		fmt.Println("Yes")
	} else {
		fmt.Println("No")
	}

}

func isArraySorted(arr []int) bool {
	for i := 0; i < len(arr)-2; i++ {
		if arr[i] > arr[i+1] {
			return false
		}
	}
	return true
}
```

**Time Complexity:** O(n)