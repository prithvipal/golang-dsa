# Check If Two Given Strings are Anagram or Not

**Example of anagram strings:**

- Listen == Silent
- Triangle == Integral
- William Shakespeare == I am a weakish speller
- 

**Note:** The string may contain punctuations. You need to ignore punctuations

## Implementation

```
package main

import (
	"fmt"
	"strings"
)

func main() {
	str1 := "William Shakespeare."
	str2 := " I am a weakish speller"
	res := anagram(str1, str2)
	fmt.Println(res)
}

func anagram(str1, str2 string) bool {
	r1 := []rune(strings.ToLower(str1))
	r2 := []rune(strings.ToLower(str2))
	m1 := make(map[rune]int)
	for _, ele := range r1 {
		if (ele >= 97 && ele <= 122) || (ele >= 65 && ele <= 90) {
			m1[ele] = m1[ele] + 1
		}
	}

	m2 := make(map[rune]int)
	for _, ele := range r2 {
		if (ele >= 97 && ele <= 122) || (ele >= 65 && ele <= 90) {
			m2[ele] = m2[ele] + 1
		}
	}

	if len(m1) != len(m2) {
		return false
	}
	for key, val := range m1 {
		if val != m2[key] {
			return false
		}
	}

	return true
}

```



