# K Largest Numbers

## Implementation

### Using Max Heap

```
package main

import "fmt"

type Heap struct {
	arr []int
}

func (h *Heap) buildHeap(arr []int) {
	h.arr = arr
	idx := (len(h.arr) - 2) / 2
	for i := idx; i >= 0; i-- {
		h.heapify(i)
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
	heap := &Heap{}
	heap.buildHeap(arr)
	for i := k - 1; i >= 0; i-- {
		res[i] = heap.pop()
	}

	return res
}

func main() {
	arr := []int{18, 6, 4, 10, 99}
	res := kLargestElements(arr, 2)
	fmt.Println(res)
}

```