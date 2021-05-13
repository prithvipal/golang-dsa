# Move All Zeroes to End

**Input:** arr[] = {18, 13, 0, 30, 0, 40} </br>
**Output:** arr[] = {18, 13, 30, 40, 0, 0}

**Input:** arr[] = {0, 0, 0, 20, 0} </br>
**Output:** arr[] = {20, 0, 0, 0}

**Input:** arr[] = {50, 66} <br>
**Output:** arr[] = {50, 66}

## Noive Approach

```
package main

import (
	"fmt"
)

func main() {
	// arr := []int{18, 13, 0, 30, 0, 40} // [18 13 40 30 0 0]
	// arr := []int{0, 0, 0, 20, 0} // [20 0 0 0 0]
	arr := []int{50, 66} // [50 66]
	moveToEnd(arr)
	fmt.Println(arr)
}

func moveToEnd(arr []int) {
	for i := 0; i < len(arr); i++ {
		if arr[i] == 0 {
			for j := i + 1; j < len(arr); j++ {
				if arr[j] != 0 {
					arr[i], arr[j] = swap(arr[i], arr[j])
				}
			}
		}
	}
}

func swap(a, b int) (int, int) {
	return b, a
}
```

**Time Complexity:** O(n*n)

## Efficient Approach

```
package main

import (
	"fmt"
)

func main() {
	// arr := []int{18, 13, 0, 30, 0, 40} // [18 13 40 30 0 0]
	// arr := []int{0, 0, 0, 20, 0} // [20 0 0 0 0]
	arr := []int{50, 66} // [50 66]
	moveToEnd(arr)
	fmt.Println(arr)
}

func moveToEnd(arr []int) {
	count := 0
	for i := 0; i < len(arr); i++ {
		if arr[i] != 0 {
			arr[i], arr[count] = swap(arr[i], arr[count])
			count++
		}
	}
}

func swap(a, b int) (int, int) {
	return b, a
}
```

**Time Complexity:** O(n)
