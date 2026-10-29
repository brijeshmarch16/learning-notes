# Big O Cheat Sheet

Big O describes how an algorithm's running time or memory use grows as the size of its input grows. It focuses on the growth rate, so constant factors and less significant terms are omitted.

## Common Time Complexities

| Complexity | Name | Typical pattern or example |
| --- | --- | --- |
| `O(1)` | Constant | A fixed number of operations, regardless of input size |
| `O(log n)` | Logarithmic | Repeatedly reducing the search space, as in binary search on sorted data |
| `O(n)` | Linear | Visiting each of `n` items once |
| `O(n log n)` | Linearithmic (log linear) | Efficient sorting algorithms |
| `O(n^2)` | Quadratic | Comparing pairs of items, often with two nested loops |
| `O(n^3)` | Cubic | Three nested loops over the input |
| `O(2^n)` | Exponential | Exploring combinations of choices; common in some recursive searches |
| `O(n!)` | Factorial | Exploring every possible ordering of `n` items |

The loop shape alone does not determine complexity; consider how many times each operation runs. For example, iterating over half of a collection is still `O(n)` because constant factors are omitted.

For separate inputs, use a different variable for each input. Work performed sequentially on collections of sizes `a` and `b` is `O(a + b)`. If a loop over one collection is nested inside a loop over the other, the work is `O(a * b)`.

## What Can Affect a Function's Running Time?

- Operations such as addition, subtraction, multiplication, and division
- Comparisons such as `<`, `>`, and `===`
- Loops such as `for` and `while`
- Calls to other functions
- Sorting

When analyzing a function that calls another function, include the called function's cost.

## Sorting Algorithms

| Algorithm | Space complexity | Best-case time | Worst-case time |
| --- | --- | --- | --- |
| Insertion sort | `O(1)` | `O(n)` | `O(n^2)` |
| Selection sort | `O(1)` | `O(n^2)` | `O(n^2)` |
| Bubble sort | `O(1)` | `O(n)` | `O(n^2)` |
| Merge sort | `O(n)` | `O(n log n)` | `O(n log n)` |
| Quicksort | `O(log n)` | `O(n log n)` | `O(n^2)` |
| Heapsort | `O(1)` | `O(n log n)` | `O(n log n)` |

## Common Data Structure Operations

The table shows the complexities listed for worst-case operations.

| Data structure | Access | Search | Insertion | Deletion | Space |
| --- | --- | --- | --- | --- | --- |
| Array | `O(1)` | `O(n)` | `O(n)` | `O(n)` | `O(n)` |
| Stack | `O(n)` | `O(n)` | `O(1)` | `O(1)` | `O(n)` |
| Queue | `O(n)` | `O(n)` | `O(1)` | `O(1)` | `O(n)` |
| Singly linked list | `O(n)` | `O(n)` | `O(1)` | `O(1)` | `O(n)` |
| Doubly linked list | `O(n)` | `O(n)` | `O(1)` | `O(1)` | `O(n)` |
| Hash table | N/A | `O(n)` | `O(n)` | `O(n)` | `O(n)` |

## Rules for Analyzing Big O

1. **Consider the worst case** unless a different case is requested.
2. **Remove constants.** For example, `O(2n)` simplifies to `O(n)`.
3. **Use a separate variable for each input.** Sequential work on inputs of sizes `a` and `b` is `O(a + b)`; nested work is `O(a * b)`.
4. **Drop non-dominant terms.** For example, `O(n^2 + n)` simplifies to `O(n^2)`.

As a rule of thumb, add the costs of steps that happen in sequence and multiply the costs of nested repetitions.

## What Can Affect Space Complexity?

- Variables
- Data structures
- Function calls and the call stack
- Memory allocations
