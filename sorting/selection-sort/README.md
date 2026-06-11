# Selection Sort

## Definition

**Selection Sort** is a simple sorting algorithm that repeatedly finds the smallest element from the unsorted portion of the array and places it at the beginning.

Unlike Bubble Sort, which swaps many times, Selection Sort performs at most one swap per pass.

---

## How It Works

Given the array:

```text
[64, 25, 12, 22, 11]
```

### Pass 1

Find the smallest element in the array:

```text
[64, 25, 12, 22, 11]
                 ↑
             smallest
```

Swap it with the first element:

```text
[11, 25, 12, 22, 64]
```

---

### Pass 2

Find the smallest element in the remaining unsorted portion:

```text
[11, 25, 12, 22, 64]
      ↑
```

Smallest is `12`.

Swap with `25`:

```text
[11, 12, 25, 22, 64]
```

---

### Pass 3

Find the smallest element in:

```text
[25, 22, 64]
```

Smallest is `22`.

Swap:

```text
[11, 12, 22, 25, 64]
```

---

### Pass 4

Remaining elements:

```text
[25, 64]
```

Already in order.

Final sorted array:

```text
[11, 12, 22, 25, 64]
```

---

## JavaScript Implementation

```javascript
function selectionSort(arr) {
  const n = arr.length;

  for (let i = 0; i < n - 1; i++) {
    let minIndex = i;

    // Find the smallest element
    for (let j = i + 1; j < n; j++) {
      if (arr[j] < arr[minIndex]) {
        minIndex = j;
      }
    }

    // Swap if needed
    if (minIndex !== i) {
      [arr[i], arr[minIndex]] = [arr[minIndex], arr[i]];
    }
  }

  return arr;
}

const numbers = [64, 25, 12, 22, 11];

console.log(selectionSort(numbers));
```

### Output

```text
[11, 12, 22, 25, 64]
```

---

## Step-by-Step Visualization

```text
Initial:
[64, 25, 12, 22, 11]

Pass 1:
[11, 25, 12, 22, 64]

Pass 2:
[11, 12, 25, 22, 64]

Pass 3:
[11, 12, 22, 25, 64]

Pass 4:
[11, 12, 22, 25, 64]
```

---

## Time Complexity

| Case         | Time Complexity |
| ------------ | --------------- |
| Best Case    | O(n²)           |
| Average Case | O(n²)           |
| Worst Case   | O(n²)           |

---

## Space Complexity

```text
O(1)
```

Selection Sort sorts the array in place and requires no extra memory.

---

## Characteristics

### Advantages

- Easy to understand and implement.
- Uses minimal memory.
- Performs fewer swaps than Bubble Sort.

### Disadvantages

- Slow for large datasets.
- Time complexity remains O(n²) even if the array is already sorted.
- Not suitable for production-scale sorting.

---

## Bubble Sort vs Selection Sort

| Feature       | Bubble Sort      | Selection Sort |
| ------------- | ---------------- | -------------- |
| Swaps         | Many             | Few            |
| Best Case     | O(n) (optimized) | O(n²)          |
| Average Case  | O(n²)            | O(n²)          |
| Stable        | Yes              | No             |
| Easy to Learn | Yes              | Yes            |

---

## Key Idea

> Find the smallest element from the unsorted part of the array and move it to its correct position in each pass.
