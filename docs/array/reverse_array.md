# Reverse an Array

**Input:** arr[] = {12, 7, 9, 33} </br>
**Output** arr[] = {33, 9, 7, 12}

**Input:** arr[] = {33, 22, 9, 3, 99} </br>
**Output:** arr[] = {99, 3, 9, 22, 33}

## Approach One


**Time Complexity:**: &theta;(n) <br>
**Aux Space:** &theta;(1)

## Approach Two

```
package main

import (
	"fmt"
)

func main() {
	// arr := []int{12, 7, 9, 33} // [33 9 7 12]
	arr := []int{33, 22, 9, 3, 99} // [99 3 9 22 33
	reserveArray(arr)
	fmt.Println(arr)

}

func reserveArray(arr []int) {
	for i := 0; i < len(arr)/2; i++ {
		temp := arr[i]
		j := len(arr) - i - 1
		arr[i] = arr[j]
		arr[j] = temp
	}
}
```

**Time Complexity:**: &theta;(n) <br>
**Aux Space:** &theta;(1)