# Factorial of A Number

**Input:** n = 4 </br>
**Output:** 24

**Input:** n = 6 </br>
**Output:** 760


**Input:** n = 0 </br>
**Output:** 1

## Iterative Approach

```
package main

import "fmt"

func main() {
	res := fact(6)
	fmt.Println(res)
}

func fact(n int) int {
	res := 1
	for i := 2; i < n; i++ {
		res = res * i
	}
	return res
}
```
**Time Complexity:** &theta;(n) </br>
**Aux Space Complexity:** &theta;(1)


## Recursive Approach

```
package main

import "fmt"

func main() {
	f := fact(4)
	fmt.Println(f)
}

func fact(n int) int {
	if n == 0 {
		return 1
	}
	return n * fact(n-1)
}

```

**Time Complexity:** &theta;(n) </br>
**Aux Space Complexity:** &theta;(n)

