# Unexpected Asynchronous Behavior in TypeScript Loops with setTimeout

This repository demonstrates a common error in TypeScript when using loops and `setTimeout` together. The issue arises because closures capture the loop variable, leading to unexpected behavior when the `setTimeout` callbacks finally execute. 

## The Bug

The `printNumbers2` function intends to print numbers 1 to 5 sequentially. However, due to the asynchronous nature of `setTimeout`, the `console.log` statements may execute out of order, resulting in unexpected output. The value of `i` is not captured at the time of the `setTimeout` call but when the callback executes, and by then the loop might have already completed.

## The Solution

The solution involves creating a new variable inside the loop to capture the current value of `i` before the `setTimeout` call, ensuring that the correct value is logged, regardless of the asynchronous execution of the callbacks.  The solution provided uses an immediately invoked function expression (IIFE) to create a new scope for the `i` variable.