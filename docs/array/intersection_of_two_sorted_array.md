# Intersection of Two Sorted Array

**Input:** a[] = {4, 6, 12, 12, 12, 17, 17, 34}</br>
b[] = { 6, 12, 13, 17, 40} </br>
**Output:** c[] = { 6, 12, 17}

**Input:** a[] = {2, 2, 4, 4, 4} </br>
b[] = {2, 2, 2, 2, 4, 6, 7} </br>
**Output:** c[] = {2, 4}

## Naive Solution

```golang
package main

import "fmt"

func main() {
	a := []int{3, 5, 10, 10, 10, 15, 15, 20}
	b := []int{5, 10, 10, 15, 30}
	res := intersection(a, b)
	fmt.Println(res) //[5 10 15]
}

func intersection(a, b []int) (c []int) {
	for i := 0; i < len(a); i++ {
		if i > 0 && a[i] == a[i-1] {
			continue
		}
		for j := 0; j < len(b); j++ {
			if a[i] == b[j] {
				c = append(c, a[i])
				break
			}
		}
	}

	return c
}

```

**Time Complexity:** O(m*n) </br>

**Dry Run:**</br>
a[] = {1, 20, 20, 40, 60} </br>
b[] = {2, 20, 20, 20} </br>

i=0 : j=0, 1, 2, 3 </br>
i=1 : j=0, 1 </br>
&nbsp;&nbsp;&nbsp;&nbsp; c[] = {20} </br>
i=2 : <br>
i=3 : j = 0, 1, 2, 3 </br>
i=4 : j = 0, 1, 2, 3 </br>

## Efficient Solution
