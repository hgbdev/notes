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

Another way\
```go
package main

import "fmt"

func main() {
	num := collectOddValues([]int{1, 2, 3, 4, 5})
	fmt.Printf("%v \n", num)
}

func collectOddValues(arr []int) []int {
	newSlice := []int{}

	if len(arr) == 0 {
		return newSlice
	}

	if arr[0]%2 != 0 {
		newSlice = append(newSlice, arr[0])
	}

	_arr := collectOddValues(arr[1:])

	newSlice = append(newSlice, _arr...)

	return newSlice

}
```

Explain:\
![image](https://user-images.githubusercontent.com/61721550/164599706-33fa0e9b-fb90-4db2-af6b-877416ad4367.png)


