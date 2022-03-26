# Count Digit

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