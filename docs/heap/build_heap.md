# Build Heap

## Implementation

```
package main

import "fmt"

type MinHeap struct {
	arr []int
}

func (mh *MinHeap) buildHeap() {
	idx := (len(mh.arr) - 2) / 2
	for i := idx; i >= 0; i-- {
		mh.heapify(i)
	}
}

func (mh *MinHeap) heapify(idx int) {
	leftIdx := left(idx)
	rightIdx := right(idx)
	minIdx := idx
	if leftIdx < len(mh.arr) && mh.arr[leftIdx] < mh.arr[idx] {
		minIdx = leftIdx
	}
	if rightIdx < len(mh.arr) && mh.arr[rightIdx] < mh.arr[minIdx] {
		minIdx = rightIdx
	}
	if minIdx == idx {
		return
	}
	mh.arr[minIdx], mh.arr[idx] = mh.arr[idx], mh.arr[minIdx]
	mh.heapify(minIdx)
}

func newMinHeap(heapArr []int) *MinHeap {
	mh := &MinHeap{
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


func main() {
	minHeap := newMinHeap([]int{10, 5, 20, 2, 4, 8})
	fmt.Println(minHeap.arr)
	minHeap.buildHeap()
	fmt.Println(minHeap.arr)
}

```