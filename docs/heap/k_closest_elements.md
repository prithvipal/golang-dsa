# K Closest Elements

## Implementation

```
package main

import (
	"fmt"
	"math"
)

type Heap struct {
	arr []Pair
}

type Pair struct {
	diff int
	idx  int
}

func (mh *Heap) insert(diff, idx int) bool {

	mh.arr = append(mh.arr, Pair{diff: diff, idx: idx})
	i := len(mh.arr) - 1
	for i > 0 && mh.arr[parent(i)].diff < mh.arr[i].diff {
		mh.arr[parent(i)], mh.arr[i] = mh.arr[i], mh.arr[parent(i)]
		i = parent(i)
	}

	return true
}

func (h *Heap) pop() Pair {
	val := h.peak()
	lastIdx := len(h.arr) - 1
	h.arr[0] = h.arr[lastIdx]
	h.arr = h.arr[:lastIdx]
	h.heapify(0)
	return val
}

func (h *Heap) peak() Pair {
	return h.arr[0]
}

func (h *Heap) isEmpty() bool {
	return len(h.arr) == 0
}

func (h *Heap) heapify(i int) {
	leftIdx := left(i)
	rightIdx := right(i)
	maxIdx := i
	if leftIdx <= len(h.arr)-1 && h.arr[leftIdx].diff > h.arr[i].diff {
		maxIdx = leftIdx
	}

	if rightIdx <= len(h.arr)-1 && h.arr[rightIdx].diff > h.arr[maxIdx].diff {
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

func kClosestElements(arr []int, x, k int) []int {
	res := make([]int, k)

	heap := &Heap{}
	for i := 0; i < k; i++ {
		diff := int(math.Abs(float64(arr[i] - x)))
		heap.insert(diff, i)
	}

	for i := k; i < len(arr); i++ {
		diff := int(math.Abs(float64(arr[i] - x)))
		if heap.peak().diff > diff {
			heap.pop()
			heap.insert(diff, i)
		}
	}
	idx := 0
	for !heap.isEmpty() {
		res[idx] = arr[heap.pop().idx]
		idx++
	}

	return res
}

func main() {
	arr := []int{30, 40, 32, 33, 36, 37}
	res := kClosestElements(arr, 38, 3)
	fmt.Println(res)
}

```