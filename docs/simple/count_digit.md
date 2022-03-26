# Count Digit

**Input:** a := 1234</br>
**Output:** 4

**Input:** a := 98</br>
**Output:** 2

**Input:** a := 5</br>
**Output:** 1

where a > 0

## Using Loop

```
package main

import "fmt"

func main() {
	d := digitCount(99999)
	fmt.Println(d)
}

func digitCount(n int) int {
	result := 0
	for n > 0 {
		result++
		n = n / 10
	}
	return result
}
```

**Dry Run**</br>
d = 123</br>
Initially result = 0</br>
After 1st Iteration: x = 12 and res=1</br>
After 2nd Iteration: x = 1 and res=2</br>
After 3rd Iteration: x = 0 and res=3</br>

**Time Complexity:** &theta;(d) where d is number of digits

## Using Logarithm

```
package main

import (
	"fmt"
	"math"
)

func main() {
	n := 99999
	d := int(math.Log10(float64(n))) + 1
	fmt.Println(d)
}

```