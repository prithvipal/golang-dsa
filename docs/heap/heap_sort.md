# Heap Sort

## Implementation

```
package main

import "fmt"

type Heap struct {
	arr []int
}

func (mh *Heap) buildHeap() {
	idx := (len(mh.arr) - 2) / 2
	for i := idx; i >= 0; i-- {
		mh.maxHeapify(len(mh.arr), i)
	}
}

func (mh *Heap) maxHeapify(size, idx int) {
	leftIdx := left(idx)
	rightIdx := right(idx)
	minIdx := idx
	if leftIdx < size && mh.arr[leftIdx] > mh.arr[idx] {
		minIdx = leftIdx
	}
	if rightIdx < size && mh.arr[rightIdx] > mh.arr[minIdx] {
		minIdx = rightIdx
	}
	if minIdx == idx {
		return
	}
	mh.arr[minIdx], mh.arr[idx] = mh.arr[idx], mh.arr[minIdx]
	mh.maxHeapify(size, minIdx)
}

func (mh *Heap) sort() {
	mh.buildHeap()
	for i := len(mh.arr) - 1; i > 0; i-- {
		mh.arr[i], mh.arr[0] = mh.arr[0], mh.arr[i]
		mh.maxHeapify(i, 0)
	}
}

func newMinHeap(heapArr []int) *Heap {
	mh := &Heap{
		arr: make([]int, len(heapArr)),
	}
	copy(mh.arr, heapArr)
	return mh
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

func main() {
	minHeap := newMinHeap([]int{10, 5, 20, 2, 4, 8})
	fmt.Println(minHeap.arr)
	minHeap.sort()
	fmt.Println(minHeap.arr)
}

```