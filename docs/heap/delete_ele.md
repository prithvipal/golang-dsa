# Delete Elememt

## Implementation

```
package main

import "fmt"

type MinHeap struct {
	arr []int
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

func (mh *MinHeap) delete(idx int) bool {
	if idx >= len(mh.arr) {
		return false
	}
	mh.arr[idx] = mh.arr[len(mh.arr)-1]
	mh.arr = mh.arr[:len(mh.arr)-1]
	mh.heapify(idx)
	return true
}

func main() {
	minHeap := newMinHeap([]int{5, 9, 8, 12, 14, 20, 40})
	fmt.Println(minHeap.arr)
	minHeap.delete(3)
	fmt.Println(minHeap.arr)
}

```