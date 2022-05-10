# Quick Sort

## Partition a Given Array

**Input:** arr[] = {13, 16, 22, 20, 17} </br>
pivot = 5 </br>
**Output:** arr[] = {13, 16, 17, 22, 20}  </br>
or </br>
arr[] = {16, 13, 17, 22, 20}
return value: 2 </br>
It is a new index of pivot element
```
Stability in Partition
├── Stable
│   └── Naive Partition
└── Not Stable
    ├── Lomuto Partition
    └── Hoare's Partition
```

## Naive Partition

![](docs/naive_partition.png)

**Input:** arr[] = {12, 17, 18, 13, 17} </br>
pivot = 1 or 4 </br>
**Output:** arr[] = {12, 13, 17, 17, 18}
return value = 3</br>

**Note:** Please note in the return value on above example that we return the last index of 17 i.e. 3, even our pivot is 1 or 4. So we  need to return the last occurrence of pivot element as explained in above example.

### Implementation

