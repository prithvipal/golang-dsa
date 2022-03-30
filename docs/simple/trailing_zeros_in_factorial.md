# Trailing Zeros in Factorial

**Input:** n = 5 </br>
**Output:** 1 </br>
**Explaination:** 1 * 2 * 3 * 4 * 5 = 120. We have one trailing zero in 120 </br>

**Input:** n = 10 </br>
**Output:** 2 </br>
**Explaination:** 1 * 2 * 3 * 4 * 5 * 6 * 7 * 8 * 9 * 10 = 3628800. We have two trailing zero in 3628800 </br>


**Input:** n = 10 </br>
**Output:** 2 </br>
**Explaination:** 1 * 2 * 3 * 4 * 5 * 6 * 7 * 8 * 9 * 10 = 3628800. We have two trailing zero in 3628800 </br>

**Input:** n = 100 </br>
**Output:** 24 </br>
**Explaination:** 1 * 2 * 3 * 4 * 5 ..... 98 * 99 * 100 = `93326215443944152681699238856266700490715968264381621468592963895217599993229915608941463976156518286253697920827223758251185210916864000000000000000000000000`. We have 24 trailing zero in this number </br>


## Naive Approach

```
package main

import "fmt"

func main() {
	res := trailingZeroInFact(10)
	fmt.Println(res)
}

func trailingZeroInFact(n int) int {
	fact := 1
	for i := 2; i <= n; i++ {
		fact = fact * i
	}
	res := 0
	for fact%10 == 0 {
		res++
		fact = fact / 10
	}
	return res
}

```