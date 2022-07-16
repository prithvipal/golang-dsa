# Job Sequence Problem

## Implementation

```
package main

import (
	"fmt"
	"sort"
)

type job struct {
	deadline int
	profit   int
}

func main() {
	res := jobSequence([]job{
		{
			deadline: 2,
			profit:   100,
		},
		{
			deadline: 1,
			profit:   50,
		},
		{
			deadline: 2,
			profit:   10,
		},
		{
			deadline: 1,
			profit:   20,
		},
		{
			deadline: 3,
			profit:   30,
		},
	})
	fmt.Println(res)
}

func jobSequence(jobs []job) int {
	sort.Slice(jobs, func(i, j int) bool {
		if jobs[i].deadline == jobs[j].deadline {
			return jobs[i].profit > jobs[j].profit
		}
		return jobs[i].deadline < jobs[j].deadline
	})
	res := 0
	time := 0
	for _, job := range jobs {
		if time < job.deadline {
			res += job.profit
			time++
		}
	}
	return res
}

```
