# Factorial of A Number

```
package main

import "fmt"

func main() {
	f := fact(4)
	fmt.Println(f)
}

func fact(n int) int {
	if n == 1 {
		return 1
	}
	return n * fact(n-1)
}

```