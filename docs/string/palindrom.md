# Check if a String is Palindrom or not


## Efficient Approach
```
package main

import "fmt"

func main() {
	str := "日本語本日" // true
	// str := "日本語語本" // false
	// str := "日本語語本日" // true
	// str := "madam" // true
	// str := "maddam" // true
	result := isPalindram(str)
	fmt.Println(result)

}

func isPalindram(str string) bool {
	chars := []rune(str)
	for i := 0; i < len(chars)/2; i++ {
		revIdx := len(chars) - i - 1
		if chars[i] != chars[revIdx] {
			return false
		}
	}
	return true
}

```