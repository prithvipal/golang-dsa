# Cound Occurance in Sorted Array

```
package main

import (
	"fmt"
	"math"
	"sort"
)

func main() {
    res := countOcc([]int{10, 20, 20, 20, 40, 40, 50}, 20) // 3
	fmt.Println(res)
}

func countOcc(arr []int, target int) int {
	low := 0
	high := len(arr) - 1
	firstO := firstOcc(arr, low, high, target)
	if firstO == -1 {
		return 0
	}
	lastO := lastOcc(arr, low, high, target)
	return (lastO - firstO) + 1
}

func firstOcc(arr []int, low, high, target int) int {
	if low > high {
		return -1
	}
	mid := (low + high) / 2
	if arr[mid] < target {
		return firstOcc(arr, mid+1, high, target)
	} else if arr[mid] > target {
		return firstOcc(arr, low, mid-1, target)
	} else {
		if mid == 0 || arr[mid] != arr[mid-1] {
			return mid
		}
		return firstOcc(arr, low, mid-1, target)
	}
}

func lastOcc(arr []int, low, high, target int) int {
	if low > high {
		return -1
	}
	mid := (low + high) / 2
	if arr[mid] < target {
		return lastOcc(arr, mid+1, high, target)
	} else if arr[mid] > target {
		return lastOcc(arr, low, mid-1, target)
	} else {
		if mid == len(arr)-1 || arr[mid] != arr[mid+1] {
			return mid
		}
		return lastOcc(arr, low+1, high, target)
	}
}

```