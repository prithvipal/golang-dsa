# Palindrome Numbers

- A number is palindrome if its reverse is same as number.
- Number is >=0
- A single digit number is always a palindrome number.

**Input:** n = 12321
**Output:** Yes

**Input:** n = 2332
**Output:** Yes

**Input:** n = 5
**Output:** Yes

**Input:** n = 34
**Output:** No

**Input:** n = 123
**Output:** No

## Implementation

```
package main

import (
	"fmt"
)

func main() {
	// res := isPalindrome(12321) // true
	// res := isPalindrome(1221) // true
	res := isPalindrome(123) // false
	fmt.Println(res)
}

func isPalindrome(n int) bool {
	rev := 0
	temp := n
	for temp != 0 {
		lastDigit := temp % 10
		rev = rev*10 + lastDigit
		temp = temp / 10
	}
	return rev == n

}

```