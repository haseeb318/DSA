# Insertion Sort

## Definition

**Insertion Sort** is a simple sorting algorithm that builds the final sorted array one element at a time.

It works similarly to how people sort playing cards in their hands: take one card at a time and insert it into its correct position among the already sorted cards.

---

## How It Works

Given the array:

```text
[5, 2, 4, 6, 1, 3]
```

### Pass 1

Consider `2`.

```text
[5, 2, 4, 6, 1, 3]
```

Since `2 < 5`, shift `5` to the right and insert `2`.

```text
[2, 5, 4, 6, 1, 3]
```

---

### Pass 2

Consider `4`.

```text
[2, 5, 4, 6, 1, 3]
```

Since `4 < 5`, shift `5` right and insert `4`.

```text
[2, 4, 5, 6, 1, 3]
```

---

### Pass 3

Consider `6`.

```text
[2, 4, 5, 6, 1, 3]
```

`6` is already in the correct position.

```text
[2, 4, 5, 6, 1, 3]
```

---

### Pass 4

Consider `1`.

Shift all larger elements to the right.

```text
[2, 4, 5, 6, 1, 3]
```

Result:

```text
[1, 2, 4, 5, 6, 3]
```

---

### Pass 5

Consider `3`.

Shift larger elements (`4`, `5`, `6`) right.

```text
[1, 2, 3, 4, 5, 6]
```

Array is now sorted.

---

## Step-by-Step Visualization

```text
Initial:
[5, 2, 4, 6, 1, 3]

Pass 1:
[2, 5, 4, 6, 1, 3]

Pass 2:
[2, 4, 5, 6, 1, 3]

Pass 3:
[2, 4, 5, 6, 1, 3]

Pass 4:
[1, 2, 4, 5, 6, 3]

Pass 5:
[1, 2, 3, 4, 5, 6]
```

---

## JavaScript Implementation

```javascript
function insertionSort(arr) {
  for (let i = 1; i < arr.length; i++) {
    const current = arr[i];
    let j = i - 1;

    while (j >= 0 && arr[j] > current) {
      arr[j + 1] = arr[j];
      j--;
    }

    arr[j + 1] = current;
  }

  return arr;
}

const numbers = [5, 2, 4, 6, 1, 3];

console.log(insertionSort(numbers));
```

### Output

```text
[1, 2, 3, 4, 5, 6]
```

---

## Dry Run Example

Sorting:

```text
[7, 4, 5]
```

### Iteration 1

Current = 4

```text
[7, 7, 5]
```

Insert 4:

```text
[4, 7, 5]
```

---

### Iteration 2

Current = 5

Shift 7:

```text
[4, 7, 7]
```

Insert 5:

```text
[4, 5, 7]
```

Final result:

```text
[4, 5, 7]
```

---

## Time Complexity

| Case                        | Time Complexity |
| --------------------------- | --------------- |
| Best Case (Already Sorted)  | O(n)            |
| Average Case                | O(n²)           |
| Worst Case (Reverse Sorted) | O(n²)           |

---

## Space Complexity

```text
O(1)
```

Insertion Sort sorts the array in place and requires no extra memory.

---

## Characteristics

### Advantages

- Easy to implement.
- Efficient for small datasets.
- Performs very well on nearly sorted arrays.
- Stable sorting algorithm.
- In-place sorting (constant memory).

### Disadvantages

- Slow for large datasets.
- Inefficient compared to O(n log n) algorithms like Merge Sort and Quick Sort.

---

## Selection Sort vs Insertion Sort

| Feature      | Selection Sort | Insertion Sort |
| ------------ | -------------- | -------------- |
| Best Case    | O(n²)          | O(n)           |
| Average Case | O(n²)          | O(n²)          |
| Worst Case   | O(n²)          | O(n²)          |
| Stable       | No             | Yes            |
| Adaptive     | No             | Yes            |
| Swaps/Shifts | Fewer swaps    | More shifts    |

---

## Real-World Usage

Insertion Sort is commonly used:

- For small datasets.
- As a helper algorithm inside advanced sorting algorithms.
- In hybrid sorting algorithms such as TimSort.
- When data is already nearly sorted.

---

## Key Idea

> Take one element at a time and insert it into its correct position within the already sorted portion of the array.
