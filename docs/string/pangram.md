# Check if a String is Pangram or not

A string is pangram if string contain a-z / A-Z alphabets alteast once. You can ignore the case. You need to consider only english alphabets and the string may contain punctuation marks. Also, you need to return how number of letter are missing if it is not pangram.

Example of angram string: 
1. The quick brown fox jumps over a lazy dog.
2. Mr. Jock, TV quiz PhD., bags few lynx.


```
package main

import (
	"fmt"
	"strings"
)

func main() {
	str := "The quick brown fox jumps over a lazy dog." // true 0
	// str := "Mr. Jock, TV quiz PhD., bags few lynx." // true 0
	// str := "The quick brown fox jumps over the dog" // false 4
	result, count := isPangram(str)
	fmt.Println(result, count)

}

func isPangram(str string) (bool, int) {
	charMap := make(map[string]bool)
	for _, ele := range str {
		if (ele >= 'A' && ele <= 'Z') || (ele >= 'a' && ele <= 'z') {
			char := strings.ToLower(string(ele))
			charMap[char] = true
		}
	}
	if len(charMap) == 26 {
		return true, 0
	}
	return false, 26 - len(charMap)
}
```
