# Sort K Sorted Array

## Implementation

```
package main

import "fmt"

type Heap struct {
	arr []int
}

func (h *Heap) insert(ele int) {
	h.arr = append(h.arr, ele)
	i := len(h.arr) - 1
	for i > 0 && h.arr[i] < h.arr[parent(i)] {
		h.arr[i], h.arr[parent(i)] = h.arr[parent(i)], h.arr[i]
		i = parent(i)
	}
}

func (h *Heap) pop() int {
	val := h.arr[0]
	lastIdx := len(h.arr) - 1
	h.arr[0] = h.arr[lastIdx]
	h.arr = h.arr[:lastIdx]
	h.heapify(0)
	return val
}

func (h *Heap) isEmpty() bool {
	return len(h.arr) == 0
}

func (h *Heap) heapify(i int) {
	leftIdx := left(i)
	rightIdx := right(i)
	minIdx := i
	if leftIdx <= len(h.arr)-1 && h.arr[leftIdx] < h.arr[i] {
		minIdx = leftIdx
	}

	if rightIdx <= len(h.arr)-1 && h.arr[rightIdx] < h.arr[minIdx] {
		minIdx = rightIdx
	}
	if minIdx == i {
		return
	}
	h.arr[i], h.arr[minIdx] = h.arr[minIdx], h.arr[i]
	h.heapify(minIdx)
}

func left(i int) int {
	return 2*i + 1
}

func right(i int) int {
	return 2*i + 2
}
func parent(i int) int {
	return (i - 1) / 2
}

func sortK(arr []int, k int) {
	h := Heap{}
	for i := 0; i <= k; i++ {
		h.insert(arr[i])
	}
	idx := 0
	for i := k + 1; i < len(arr); i++ {
		ele := h.pop()
		arr[idx] = ele
		idx++
		h.insert(arr[i])
	}

	for !h.isEmpty() {
		ele := h.pop()
		arr[idx] = ele
		idx++
	}
}

func main() {
	arr := []int{6, 5, 3, 2, 8, 10, 9}
	sortK(arr, 3)
	fmt.Println(arr)
}
```