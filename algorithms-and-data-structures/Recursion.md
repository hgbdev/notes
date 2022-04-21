## collectOddValues
```go
package main

import "fmt"

func main() {
	num := collectOddValues([]int{1, 2, 3})
	fmt.Printf("%v \n", num)
}

func collectOddValues(arr []int) []int {
	result := []int{}

	helper(arr, &result)

	return result

}

func helper(input []int, result *[]int) []int {
	if len(input) == 0 {
		return nil
	}

	if input[0]%2 != 0 {
		*result = append(*result, input[0])
	}

	return helper(input[1:], result)
}

```
