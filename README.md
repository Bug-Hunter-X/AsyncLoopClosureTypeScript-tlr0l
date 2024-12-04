# Asynchronous Loop Closure Bug in TypeScript

This repository demonstrates a common closure issue in TypeScript when using asynchronous operations like `setTimeout` within a loop. The issue arises due to the asynchronous nature of `setTimeout`, which can lead to unexpected behavior when capturing variables within the loop.

## Problem
The `printNumbers2` function intends to print numbers from 1 to `n` with a slight delay using `setTimeout`. However, due to the asynchronous nature of `setTimeout`, the loop finishes executing before the `setTimeout` callbacks are triggered. By the time the callbacks fire, the loop variable `i` has already reached its final value, resulting in all callbacks printing the same value (n+1).

## Solution
The problem can be solved using closures and immediately invoked functions to create a separate scope for each iteration of the loop.  This ensures that each callback has its own copy of the `i` variable at the time of creation.