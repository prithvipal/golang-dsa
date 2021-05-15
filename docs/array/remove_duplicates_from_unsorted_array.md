# Remove Duplicates from Un-sorted Array

## Implementation

```
package main

import "fmt"

func main() {
	arr := []int{10, 12, 8, 10, 12}
	result := removeDups(arr)
	fmt.Println(result)
}

func removeDups(arr []int) []int {
	var tempArr []int
	m := make(map[int]bool)
	for _, ele := range arr {
		if _, ok := m[ele]; !ok {
			m[ele] = true
			tempArr = append(tempArr, ele)
		}
	}
	return tempArr
}
```