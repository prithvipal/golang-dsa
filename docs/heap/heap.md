# Heap

```
package main

import "fmt"

type MinHeap struct {
	arr []int
}

func (mh *MinHeap) insert(ele int) bool {

	mh.arr = append(mh.arr, ele)
	i := len(mh.arr) - 1
	for i > 0 && mh.arr[parent(i)] > mh.arr[i] {
		mh.arr[parent(i)], mh.arr[i] = mh.arr[i], mh.arr[parent(i)]
		i = parent(i)
	}

	return true
}

func (mh *MinHeap) minExtract() *int {
	if len(mh.arr) == 0 {
		return nil
	}
	if len(mh.arr) == 1 {
		val := mh.arr[0]
		mh.arr = []int{}
		return &val
	}
	val := mh.arr[0]
	lastIdx := len(mh.arr) - 1
	mh.arr[lastIdx], mh.arr[0] = mh.arr[0], mh.arr[lastIdx]
	mh.arr = mh.arr[:lastIdx]
	mh.heapify(0)
	return &val
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
func parent(i int) int {
	return (i - 1) / 2
}

func main() {
	minHeap := newMinHeap([]int{20, 25, 30, 35, 40, 80, 32, 100, 70, 60})
	fmt.Println(minHeap.arr)
	fmt.Println(minHeap.minExtract())
	fmt.Println(minHeap.arr)
}

```