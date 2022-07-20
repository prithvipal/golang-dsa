# Buy Maximum Items by Given Sum

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

func buyMaxItems(arr []int, sum int) int {
	res := 0
	heap := Heap{}
	for _, ele := range arr {
		heap.insert(ele)
	}
	for sum > 0 {
		ele := heap.pop()
		if ele <= sum {
			res++
		}
		sum -= ele
	}
	return res
}

func main() {
	arr := []int{1, 12, 5, 11, 200}
	res := buyMaxItems(arr, 19)
	fmt.Println(res)
}
```