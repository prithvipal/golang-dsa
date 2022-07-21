# K Largest Elements

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

### Using Min Heap

```
package main

import "fmt"

type Heap struct {
	arr []int
}

func (mh *Heap) insert(ele int) bool {

	mh.arr = append(mh.arr, ele)
	i := len(mh.arr) - 1
	for i > 0 && mh.arr[parent(i)] > mh.arr[i] {
		mh.arr[parent(i)], mh.arr[i] = mh.arr[i], mh.arr[parent(i)]
		i = parent(i)
	}

	return true
}

func (h *Heap) buildHeap(arr []int) {
	h.arr = make([]int, len(arr))
	copy(h.arr, arr)
	idx := (len(h.arr) - 2) / 2
	for i := idx; i >= 0; i-- {
		h.heapify(i)
	}
}

func (h *Heap) pop() int {
	val := h.peak()
	lastIdx := len(h.arr) - 1
	h.arr[0] = h.arr[lastIdx]
	h.arr = h.arr[:lastIdx]
	h.heapify(0)
	return val
}

func (h *Heap) peak() int {
	return h.arr[0]
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

func kLargestElements(arr []int, k int) []int {
	res := make([]int, k)

	heap := &Heap{}
	heap.buildHeap(arr[:k])

	for i := k; i < len(arr); i++ {
		if heap.peak() < arr[i] {
			heap.pop()
			heap.insert(arr[i])
		}
	}
	idx := 0
	for !heap.isEmpty() {
		res[idx] = heap.pop()
		idx++
	}

	return res
}

func main() {
	arr := []int{18, 6, 44, 10, 99}
	res := kLargestElements(arr, 3)
	fmt.Println(res)
}

```