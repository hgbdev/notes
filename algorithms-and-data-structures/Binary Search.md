# Binary Search

- This function accepts a sorted array and a value
- Create a left pointer at the start of the array, and a right pointer at the end of the array
- While the left pointer comes before the right pointer:
  - Create a pointer in the middle
  - If you dinf the value you want, return the index
  - If the value is too small, move the left pointer up
  - If the value is too large, move the right pointer down
- If you never find the value, return -1

```go
// Golang
package main

import (
	"fmt"
	"math"
)

func main() {
	index := binarySearch([]int{1, 2, 3, 4, 5, 6, 7, 8, 9, 10}, 6)
	fmt.Printf("%v \n", index)
}

func binarySearch(arr []int, num int) int {
	left := 0
	right := len(arr)

	for left <= right {
		mid := math.Floor(float64((left + right) / 2))
		if arr[int(mid)] == num {
			return int(mid)
		}
		if arr[int(mid)] < num {
			left = int(mid) + 1
		} else {
			right = int(mid) - 1
		}
	}

	return -1
}

```
