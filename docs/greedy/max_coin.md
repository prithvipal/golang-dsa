# Max Coin

Given list of coins 10, 5, 2, 1 and total amount. Find min number of coins to get total amount

**Input:** total = 57, coins = []int{10, 5, 2, 1} </br>
**Outout:** 10*5 + 5*1 + 2*1 so total 7 coins

## Implementation

[//]:<> (Please add function in following solution)

```
func minCoin(total int, coins []int) map[int]int {
	res := make(map[int]int)
	for _, c := range coins {
		if total == 0 {
			return res
		}
		if total < c {
			continue
		}
		n := total / c
		res[c] = n
		total = total % c
	}
	return res
}
```