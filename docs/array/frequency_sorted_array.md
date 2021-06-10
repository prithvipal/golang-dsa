# Frequency in a Sorted Array

**Input:** arr[] = {12, 12, 12, 23, 43, 43} <br/>
**Output:** <br/>
12 -> 3 <br/>
23 -> 1 <br/>
43 -> 2 <br/>

**Input:** arr[] = {14, 14, 14, 14} <br/>
**Output:** <br/>
14 -> 4 <br/>

**Input:** arr[] = {101, 102, 103} <br/>
**Output:** <br/>
101 -> 1 <br/>
102 -> 1 <br/>
103 -> 1 <br/>

## Implementation

```
package main

import "fmt"

func main() {
	arr := []int{10}
	// arr := []int{12, 12, 12, 23, 43, 43}
	// arr := []int{14, 14, 14, 14}
	// arr := []int{101, 102, 103}
	printFreq(arr)
}

func printFreq(arr []int) {
	freq := 1
	i := 1
	for i < len(arr) {
		for i < len(arr) && arr[i] == arr[i-1] {
			i++
			freq++
		}
		fmt.Printf("%d -> %d\n", arr[i-1], freq)
		i++
		freq = 1
	}

	if len(arr) == 1 || arr[i-2] != arr[i-3] {
		fmt.Printf("%d --> %d\n", arr[len(arr)-1], 1)
	}

}

```

- **Time Complexity:** &theta;(n)
- **Note:** Since we are increamenting i in both for loop (outer and inner). As soon as i becomes equal to n, the loop stops. So total number of iterations are inner+outer loops. Time complexity is exactly n.



