# Maximum Activity Solution

## Implementation

```
package main

import (
	"fmt"
	"sort"
)

type activity [2]int

func (act activity) isOverlapping(actN activity) bool {
	return act[1] <= actN[0]
}

type activityList []activity

func (a *activityList) last() activity {
	lastIdx := len(*a) - 1
	return (*a)[lastIdx]
}

func createList(acts ...activity) activityList {
	var actList activityList
	for _, a := range acts {
		actList = append(actList, a)
	}
	return actList
}

func main() {
	list := createList([2]int{3, 8}, [2]int{2, 4}, [2]int{1, 3}, [2]int{10, 11})
	res := activitySolution(list)
	fmt.Println(res)
}

func activitySolution(actList activityList) activityList {
	sort.Slice(actList, func(i, j int) bool {
		return actList[i][1] < actList[j][1]
	})
	res := activityList{actList[0]}
	for i := 1; i < len(actList); i++ {
		actN := actList[i]
		if res.last().isOverlapping(actN) {
			res = append(res, actN)
		}
	}
	return res
}

```