# Problem Solving Patterns - Sliding Window Pattern.md

## Description
This pattern involves creating a **window** which can either be an array or number from one position to another.\
Depending on a certain condition, the window either increases or closes (and a new window is created).\
Very useful for keeping track of a subset of data in array/string etc.

## Problem
Write a function called **maxSubArraySum** which accepts an array of integers and a number called **n**. The function should calculate the maximum sum of **n** consecutive emelents in the array.

```ts
//typescript
function maxSubArraySum(arr: number[], num: number): number {
    let max: number = 0;
    let tmpMax: number = 0;

    for(let i = 0; i < num; i++) {
        tmpMax += arr[i];
    }

    max = tmpMax;

    for(let i = num; i < arr.length; i++) {
        tmpMax = tmpMax - arr[i - num] + arr[i];
        max = Math.max(max, tmpMax);
    }

    return max;
}

const result = maxSubArraySum([1, 4, 5, 4, 10], 3);
console.log(result);

```
