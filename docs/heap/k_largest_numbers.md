# K Largest Numbers

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
	for i > 0 && h.arr[i] > h.arr[parent(i)] {
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
	maxIdx := i
	if leftIdx <= len(h.arr)-1 && h.arr[leftIdx] > h.arr[i] {
		maxIdx = leftIdx
	}

	if rightIdx <= len(h.arr)-1 && h.arr[rightIdx] > h.arr[maxIdx] {
		maxIdx = rightIdx
	}
	if maxIdx == i {
		return
	}
	h.arr[i], h.arr[maxIdx] = h.arr[maxIdx], h.arr[i]
	h.heapify(maxIdx)
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

func kLargestElements(arr []int, k int) []int {
	res := make([]int, k)
	heap := Heap{}
	for _, ele := range arr {
		heap.insert(ele)
	}
	for i := k - 1; i >= 0; i-- {
		res[i] = heap.pop()
	}

	return res
}

func main() {
	arr := []int{8, 6, 4, 10, 9}
	res := kLargestElements(arr, 3)
	fmt.Println(res)
}

```