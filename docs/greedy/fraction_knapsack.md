# Fraction Knapsack

## Implementation

```
package main

import (
	"fmt"
	"sort"
)

type knapsack struct {
	weight int
	value  int
}

func main() {
	res := fractionKnapsack([]knapsack{
		{
			weight: 10, value: 200,
		},
		{
			weight: 5, value: 50,
		},
		{
			weight: 20, value: 100,
		},
	}, 15)

	fmt.Println(res)
}

func fractionKnapsack(knapsacks []knapsack, capacity int) int {
	sort.Slice(knapsacks, func(i, j int) bool {
		iWeight := knapsacks[i].value / knapsacks[i].weight
		jWeight := knapsacks[j].value / knapsacks[j].weight
		return iWeight > jWeight
	})

	res := 0
	for _, k := range knapsacks {
		if capacity == 0 {
			return res
		}
		if k.weight <= capacity {
			res += k.value
		} else {
			res += capacity * k.value / k.weight
		}
		capacity -= k.weight
	}
	return res
}

```
