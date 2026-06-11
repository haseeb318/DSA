# Bubble Sort

## Definition

Bubble Sort is a simple sorting algorithm that repeatedly compares adjacent elements and swaps them if they are in the wrong order.

After each pass through the array, the largest unsorted element "bubbles up" to its correct position at the end of the array.

## How It Works

Suppose we want to sort:

```text
[5, 3, 8, 4, 2]
```

### Pass 1

Compare adjacent elements:

- `5 > 3` → swap → `[3, 5, 8, 4, 2]`
- `5 < 8` → no swap → `[3, 5, 8, 4, 2]`
- `8 > 4` → swap → `[3, 5, 4, 8, 2]`
- `8 > 2` → swap → `[3, 5, 4, 2, 8]`

Notice that `8`, the largest number, has moved to the end.

### Pass 2

- `3 < 5` → no swap → `[3, 5, 4, 2, 8]`
- `5 > 4` → swap → `[3, 4, 5, 2, 8]`
- `5 > 2` → swap → `[3, 4, 2, 5, 8]`

### Pass 3

- `3 < 4` → no swap → `[3, 4, 2, 5, 8]`
- `4 > 2` → swap → `[3, 2, 4, 5, 8]`

### Pass 4

- `3 > 2` → swap → `[2, 3, 4, 5, 8]`

The array is now sorted.

## JavaScript Code

```js
function bubbleSort(arr) {
  const n = arr.length;

  for (let i = 0; i < n - 1; i++) {
    for (let j = 0; j < n - 1 - i; j++) {
      if (arr[j] > arr[j + 1]) {
        // Swap elements
        [arr[j], arr[j + 1]] = [arr[j + 1], arr[j]];
      }
    }
  }

  return arr;
}

const numbers = [5, 3, 8, 4, 2];
console.log(bubbleSort(numbers));
```

**Output:**

```text
[2, 3, 4, 5, 8]
```

## Optimized Version

If the array becomes sorted before all passes are completed, we can stop early.

```js
function bubbleSort(arr) {
  const n = arr.length;

  for (let i = 0; i < n - 1; i++) {
    let swapped = false;

    for (let j = 0; j < n - 1 - i; j++) {
      if (arr[j] > arr[j + 1]) {
        [arr[j], arr[j + 1]] = [arr[j + 1], arr[j]];
        swapped = true;
      }
    }

    if (!swapped) {
      break;
    }
  }

  return arr;
}

console.log(bubbleSort([1, 2, 3, 4, 5]));
```

Since the array is already sorted, it finishes after one pass.

## Complexity

| Case                  | Time Complexity |
| --------------------- | --------------- |
| Best Case (optimized) | O(n)            |
| Average Case          | O(n²)           |
| Worst Case            | O(n²)           |

**Space Complexity:** O(1)

## Why Bubble Sort Is Rarely Used

Bubble Sort is easy to learn but inefficient for large datasets because it performs many unnecessary comparisons and swaps.

For real applications, developers usually prefer:

- Quick Sort
- Merge Sort
- Heap Sort
- `Array.sort()` (which uses highly optimized algorithms internally)

Bubble Sort remains valuable because it teaches fundamental concepts: comparisons, swapping, nested loops, and algorithm analysis.
