# Merge Sort

## Introduction
- Divide and Conquer Algorithm
    - Divide
    - Conquer
    - Merge
- Stable Algorithm
- &theta;(n log n) time and O(n) aux space
- Well suited for linked list. Works in O(1) aux space
- Used in external sorting
- In generate for array. Quick sort outperforms it.

## Merge Two Sorted Array

**Input:** a[] = {12, 17, 22} </br>
b[] = {7, 8, 8, 17} </br>
**Ouput:** c[] = {7, 8, 8, 12, 17, 22} </br>
</br>

**Input:** a[] = {11, 11, 22} </br>
b[] = {33} </br>
**Ouput:** c[] = {11, 11, 22, 33} </br>


### Naive Solution

```
package main

import (
	"fmt"
	"sort"
)

type Person struct {
	id   int
	name string
}

func main() {
	a := []int{10, 15, 20, 20}
	b := []int{1, 2, 13}
	c := merge(a, b)
	fmt.Println(c)
}

func merge(a []int, b []int) []int {
	c := make([]int, len(a)+len(b))
	for i, ele := range a {
		c[i] = ele
	}
	for i, ele := range b {
		c[len(a)+i] = ele
	}
	sort.Ints(c)
	return c
}
```

**Time Complexity:** O((m+n) log(m+n)) </br>
**Space Complexity:** &theta;(m+n)

**Dry Run:** </br>
a[] = {10, 15, 20, 20} </br>
b[] = {1, 2, 13} </br>
 
*After 1st Loop:* c[] = {10, 15, 20, 20, _, _, _} </br>
*After 2st Loop:* c[] = {10, 15, 20, 20, 1, 2, 13} </br>
*After Sorting:* c[] = {1, 2, 10, 13, 15, 20, 20} </br>


### Efficient Solution

## Merge Function of Merge Sort

### Implementation Idea

### Implementation

## Merge Sort Algorithm

## Merge Sort Analysis