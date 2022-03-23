# Problem Solving Patterns - Multiple Points Pattern

## Problem 1
Write function called **sumZero** which aceepts a **sorted** array of integers. The function should find the first pair where the sum is 0. Return an arraya that includes both values that zum to zero or undefined if a pair does not exist.
```ts
// Typescript
// Function sumZero using Multiple Points Pattern
function sumZero(numbers: number[]): number[] | any {
    let left = 0;
    let right = numbers.length - 1;

    while(left < right) {
        const sum: number = numbers[left] + numbers[right];
        console.log(sum)
        if(sum === 0) {
            return [numbers[left], numbers[right]];
        } else if(sum < 0) {
            left++;
        } else {
            right--;
        }
    }

}
```

## Problem 2
Implement a function called **countUniqueValues**, which accepts a sorted array, and counts the unique values in the array. There can be negative numbers in the array, but it will always be sorted.
```ts
// Typescript
// Count Unique Values using Multiple Point Pattern
function countUniqueValues(numbers) {
    if (numbers.length === 0)
        return 0;
    let count = 0;
    for (let i in numbers) {
        if (numbers[count] !== numbers[i]) {
            count++;
            numbers[count] = numbers[i];
        }
    }
    return count + 1;
}

// countUniqueValues([1, 1, 1, 2]); => 2
// countUniqueValues([1, 1, 1, 2, 3, 4, 4, 5, 6, 6, 7, 7]); => 7
```
