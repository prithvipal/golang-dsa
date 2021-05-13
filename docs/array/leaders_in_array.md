# Leaders in an Array

**Input:** arr[] = {17, 20, 14, 13, 16, 15, 12} </br>
**Output:** {20, 16, 15, 12}

**Input:** arr[] = {10, 20, 30} </br>
**Output:** {30}

**Input:** arr[] = {25, 15, 10} </br>
**Output:** {25, 15, 10}

- Leader in an array is the element that there is no larger than the element to its right side.
- Left most is always be leader because there is no large then that element to its right side.
- If there are duplicate elements then first occurance can be considers as leader. We can consider last occurance because we are say larger but not equal.
    - Ex: {9, 11, 6, 11, 8, 7, 2} <br>
    :: here can not consider 11 of 1st index. we can condier 11 of 3rd index.


## Naive Approach

```
package main

import (
	"fmt"
)

func main() {
	// arr := []int{17, 20, 14, 13, 16, 15, 12} // 20 16 15 12
	// arr := []int{10, 20, 30} // 30
	arr := []int{25, 15, 10}
	leader(arr)
}

func leader(arr []int) {
	for i := 0; i < len(arr); i++ {
		flag := false
		for j := i + 1; j < len(arr); j++ {
			if arr[i] <= arr[j] {
				flag = true
				break
			}
		}
		if !flag {
			fmt.Printf("%d ", arr[i])
		}
	}
	fmt.Println()
}
```

**Time Complexity:** O(n * n)

## Efficient Approach

```
package main

import (
	"fmt"
)

func main() {
	arr := []int{17, 20, 14, 13, 16, 15, 12} // 12 15 16 20
	// arr := []int{10, 20, 30} // 30
	// arr := []int{25, 15, 10} // 10 15 25
	leader(arr)
}

func leader(arr []int) {
	curLeader := arr[len(arr)-1]
	fmt.Printf("%d ", curLeader)
	for i := len(arr) - 2; i >= 0; i-- {
		if curLeader < arr[i] {
			curLeader = arr[i]
			fmt.Printf("%d ", curLeader)
		}
	}
	fmt.Println()
}
```

**Time Complexity:** &theta;(n)

**Note:**

- It will print leaders in reverse order
- If we want to print in same order as we have in array, then we can store leaders in a new array and then we can iterate new array in reverse order and print each element.