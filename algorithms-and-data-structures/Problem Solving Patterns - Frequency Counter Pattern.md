# Problem Solving Patterns - Frequency Counter Pattern

## Problem 1
Write function called **same**, which accept two arrays. The function should return true if every value in the array has it's corresponding value squared in the second array. The frequency of values must be the same.

```ts
//  Frequency Counter
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

## Problem 2
Given two strings, write function fo determine if the second string is an anagram of the first. An anagram is a word, phrase, or name formed by rearranging the letters of another, such as *cinema*, formed from *iceman*.

```ts
// Function validAnagram us Frequency Counter Pattern
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