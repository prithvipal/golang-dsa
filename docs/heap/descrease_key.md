# Descrease Key

## Implementation

```
package main

import "fmt"

type MinHeap struct {
	arr []int
}



func newMinHeap(heapArr []int) *MinHeap {
	mh := &MinHeap{
		arr: make([]int, len(heapArr)),
	}
	copy(mh.arr, heapArr)

	return mh
}


func parent(i int) int {
	return (i - 1) / 2
}

func (mh *MinHeap) decreaseKey(idx, val int) {
	mh.arr[idx] = val

	for idx >= 0 && mh.arr[idx] < mh.arr[parent(idx)] {
		mh.arr[idx], mh.arr[parent(idx)] = mh.arr[parent(idx)], mh.arr[idx]
		idx = parent(idx)
	}
}

func main() {
	minHeap := newMinHeap([]int{20, 80, 200, 90, 100, 250, 500, 120})
	fmt.Println(minHeap.arr)
	minHeap.decreaseKey(3, 10)
	fmt.Println(minHeap.arr)
}

```