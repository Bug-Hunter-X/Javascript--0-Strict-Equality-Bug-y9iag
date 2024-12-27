# Javascript -0 Strict Equality Bug

This repository demonstrates a subtle bug in JavaScript related to the comparison of 0 and -0 using strict equality.  The `foo` function attempts to handle null, negative, and positive numbers, but it fails to correctly handle -0.

## Bug Description
The problem lies in the `if (x === null)` check.  While this correctly handles null values, it also unexpectedly handles -0 as if it were 0, which may lead to unexpected behavior.  This is because while `0 === -0` is true, `-0` is a distinct value from `0` in Javascript, and the behavior is not always consistent with other numerical comparisons.

## How to Reproduce
Clone this repository and run `bug.js`. Note the output.  Then run the `bugSolution.js` file to see the correct output.

## Solution
The solution is to explicitly check for -0 in addition to null, using `Object.is(x, -0)` before the `x === null` check. This accounts for the distinct identity of -0.