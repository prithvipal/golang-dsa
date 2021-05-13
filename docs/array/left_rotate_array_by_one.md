# Left Rotate an Array by One

**Input:** arr[] = {11, 22, 33, 44, 55} </br>
**Output:** arr[] = {22, 33, 44, 55, 11}

**Input:** arr[] = {50, 3, 22} </br>
**Output:** arr[] = {3, 22, 50}
 
```
package main

import (
	"fmt"
)

func main() {
	// arr := []int{11, 22, 33, 44, 55} // [22 33 44 55 11]
	arr := []int{50, 3, 22} // [3 22 50]
	leftRotateOn(arr)
	fmt.Println(arr)
}

func leftRotateOn(arr []int) {
	temp := arr[0]
	for i := 1; i < len(arr); i++ {
		arr[i-1] = arr[i]
	}
	arr[len(arr)-1] = temp
}
```