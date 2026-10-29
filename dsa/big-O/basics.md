# Big O: time and space

Big O describes how an algorithm's resource use grows as the input grows. We usually analyze **time complexity** (how the amount of work grows) and **space complexity** (how much extra memory it needs) separately. `n` means the input size, such as the number of items in an array.

## `O(1)` — constant

The work stays about the same no matter how many items are in the input.

```js
function firstItem(items) {
  return items[0];
}
```

- **Time:** `O(1)` — one array lookup.
- **Extra space:** `O(1)` — no memory that grows with the input.

## `O(n)` — linear

The work grows in proportion to the number of items. A loop that visits each item once is usually `O(n)`.

```js
function sum(items) {
  let total = 0;
  for (const item of items) {
    total += item;
  }
  return total;
}
```

- **Time:** `O(n)` — in the worst case, it visits all `n` items.
- **Extra space:** `O(1)` — `total` uses one variable, regardless of `n`.

## `O(n²)` — quadratic

Work grows roughly with the square of the input. Two loops that each run over all `n` items commonly produce `n × n` work.

```js
function printAllPairs(items) {
  for (const first of items) {
    for (const second of items) {
      console.log(first, second);
    }
  }
}
```

- **Time:** `O(n²)` — there are `n` outer iterations and `n` inner iterations per outer iteration.
- **Extra space:** `O(1)` — the loops use a fixed number of variables; they do not build a collection.

### `O(log n)` — logarithmic

Each step cuts the remaining search area in half. Binary search requires sorted input.

```js
function binarySearch(items, target) {
  let low = 0;
  let high = items.length - 1;

  while (low <= high) {
    const middle = Math.floor((low + high) / 2);
    if (items[middle] === target) return middle;
    if (items[middle] < target) low = middle + 1;
    else high = middle - 1;
  }
  return -1;
}
```

- **Time:** `O(log n)` — each iteration halves the remaining range.
- **Extra space:** `O(1)` — it stores only a few indexes.

### `O(n log n)` — linearithmic

Efficient comparison sorts such as merge sort split the input into about `log n` levels, doing about `n` work at each level.

```js
// Merge-sort idea (merge() combines two sorted halves in linear time)
function mergeSort(items) {
  if (items.length <= 1) return items;
  const middle = Math.floor(items.length / 2);
  return merge(
    mergeSort(items.slice(0, middle)),
    mergeSort(items.slice(middle)),
  );
}
```

- **Time:** `O(n log n)` — `n` work across `log n` levels.
- **Extra space:** `O(n)` — merge sort needs temporary arrays to combine results. (This simple `slice` version also copies subarrays.)

### `O(2ⁿ)` — exponential

The number of calls doubles as each item branches into two choices. This pattern appears in simple recursive subset generation.

```js
function countChoices(n) {
  if (n === 0) return 1;
  return countChoices(n - 1) + countChoices(n - 1);
}
```

- **Time:** `O(2ⁿ)` — each level doubles the number of calls.
- **Extra space:** `O(n)` — the deepest chain of recursive calls has depth `n` (not counting any stored results).

### `O(n!)` — factorial

Trying every ordering of `n` distinct items can take factorial time: there are `n × (n - 1) × ... × 1` orderings.

```js
function visitPermutations(items, used = new Set()) {
  if (used.size === items.length) return;
  for (const item of items) {
    if (used.has(item)) continue;
    used.add(item);
    visitPermutations(items, used);
    used.delete(item);
  }
}
```

- **Time:** `O(n × n!)` for this version, because it explores `n!` arrangements and scans up to `n` items at each call. Often summarized as factorial time.
- **Extra space:** `O(n)` for the `used` set and recursion depth, excluding stored/output permutations.

### `O(n + m)` — two input sizes

When an algorithm scans two separate inputs, name both sizes instead of assuming they are equal.

```js
function printBoth(first, second) {
  for (const item of first) console.log(item);
  for (const item of second) console.log(item);
}
```

- **Time:** `O(n + m)` — scans each input once.
- **Extra space:** `O(1)` — uses no growing data structure.

## How to find time and space complexity

1. **Choose the input size.** For an array, `n` is its length.
2. **For time, count repeated work.** One pass through `n` items is `O(n)`; a full nested pass is often `O(n²)`. Work done one step after another adds, then keep the fastest-growing term: `O(n² + n)` becomes `O(n²)`. Ignore constant multipliers: `O(3n)` becomes `O(n)`.
3. **For space, count extra memory that grows with the input.** A few variables are `O(1)`. A new array holding `n` items is `O(n)`. Don't count the input itself unless the analysis specifically asks for total memory.
4. **Report them separately**, for example: “time `O(n)`, extra space `O(1)`.”

The examples show worst-case time unless stated otherwise. A loop that returns early may do less work on some inputs, but can still be `O(n)` in the worst case.
