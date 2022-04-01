# Problem Solving Patterns - Frequency Counter Pattern

## Problem 1
Write function called **same**, which accept two arrays. The function should return true if every value in the array has it's corresponding value squared in the second array. The frequency of values must be the same.

```ts
//  Frequency Counter
// typescript
function same(arr1: number[], arr2: number[]): boolean {
    if(arr1.length !== arr2.length) {
        return false;
    }

    const frequencyCounterArr1: any = {};
    const frequencyCounterArr2: any = {};

    for(let val of arr1) {
        frequencyCounterArr1[val] = (frequencyCounterArr1[val] || 0) + 1; 
    }

    for(let val of arr2) {
        frequencyCounterArr2[val] = (frequencyCounterArr2[val] || 0) + 1;
    }

    for(let key in frequencyCounterArr1) {
        if(!(Number(key) ** 2 in frequencyCounterArr2)) {
            return false;
        }

        if(frequencyCounterArr1[key] !== frequencyCounterArr2[Number(key) ** 2]) {
            return false
        }
    }

    return true;
}

const result = same([1, 2, 3, 2], [9, 1, 4, 4]);
console.log(result);
```

```go
// Golang
package main

import (
	"fmt"
)

func main() {
	sl1 := []int{1, 2, 3, 2}
	sl2 := []int{9, 1, 4, 5}
	isSame := same(sl1, sl2)
	fmt.Printf("%v", isSame)

}

func same(sl1, sl2 []int) bool {
	if len(sl1) != len(sl2) {
		return false
	}

	frequencyCounter1 := make(map[int]int)
	frequencyCounter2 := make(map[int]int)

	for _, i := range sl1 {
		if _, ok := frequencyCounter1[i]; ok {
			frequencyCounter1[i]++
		} else {
			frequencyCounter1[i] = 1
		}
	}

	for _, i := range sl2 {
		if _, ok := frequencyCounter2[i]; ok {
			frequencyCounter2[i]++
		} else {
			frequencyCounter2[i] = 1
		}
	}

	for i := range frequencyCounter1 {
		if _, ok := frequencyCounter2[i*i]; !ok {
			return false
		}

		if frequencyCounter1[i] != frequencyCounter2[i*i] {
			return false
		}
	}

	return true
}

```

## Problem 2
Given two strings, write function fo determine if the second string is an anagram of the first. An anagram is a word, phrase, or name formed by rearranging the letters of another, such as *cinema*, formed from *iceman*.

```ts
// Function validAnagram us Frequency Counter Pattern
// Typescript
function validAnagram(str1, str2) {
    if (str1.length !== str2.length) {
        return false;
    }
    const lookup = {};
    for (let letter of str1) {
        lookup[letter] = (lookup[letter] || 0) + 1;
    }
    for (let letter of str2) {
        if (!lookup[letter]) {
            return false;
        }
        else {
            lookup[letter] = lookup[letter] - 1;
        }
    }
    return true;
}
```

```go
// Golang
package main

import (
	"fmt"
)

func main() {
	isValidAnagram := validAnagram("iceman", "cinema")
	fmt.Printf("%v ", isValidAnagram)
}

func validAnagram(str1, str2 string) bool {
	if len(str1) != len(str2) {
		return false
	}

	lookup := make(map[string]int)

	for _, letter := range str1 {
		if _, ok := lookup[string(letter)]; !ok {
			lookup[string(letter)]++
		} else {
			lookup[string(letter)] = 1
		}
	}

	for _, letter := range str2 {
		if v := lookup[string(letter)]; v < 1 {
			return false
		} else {
			lookup[string(letter)]--
		}
	}

	return true
}

```

## Problem 3: Frequency counter - sameFrquency
Write a function called **sameFrequency**. Given two positive integers, find out if the two numbers have the same frequency of digits.
```ts
//typescript
function sameFrequency(num1: number, num2: number): boolean {
    const frequencyNum1: any = {};
    const frequencyNum2: any = {};

    let _tNum1: number = num1;
    let _tNum2: number = num2;

    while(_tNum1 >= 1) {
        const key = Math.floor(_tNum1 % 10)
        frequencyNum1[key] = (frequencyNum1[key] || 0) + 1;
        _tNum1 = _tNum1 / 10;
    }

    while(_tNum2 >= 1) {
        const key = Math.floor(_tNum2 % 10)
        frequencyNum2[key] = (frequencyNum2[key] || 0) + 1;
        _tNum2 = _tNum2 / 10;
    }

    for(let key in frequencyNum1) {
        if(frequencyNum1[key] !== frequencyNum2[key]) {
            return false;
        }
    }

    return true;
}
```
