# Square Root

Floor of square root.

**Input:** 4 </br>
**Output:** 2

**Input:** 6 </br>
**Output:** 2

**Input:** 9 </br>
**Output:** 3

**Input:** 12 </br>
**Output:** 3

**Input:** 16 </br>
**Output:** 4

```
package main

import "fmt"

func main() {
	r := squarRoot(5)
	fmt.Println(r)
}

func squarRoot(n int) int {
	low := 0
	high := n
	for low <= high {
		mid := (low + high) / 2
		if mid*mid == n {
			return mid
		} else if mid*mid < n {
			low = mid + 1
		} else {
			high = mid - 1
		}
	}
	return low - 1
}

```