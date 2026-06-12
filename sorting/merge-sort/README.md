# Merge Sort

## Definition

**Merge Sort** is a divide-and-conquer sorting algorithm that recursively divides an array into smaller halves, sorts those halves, and then merges them back together in sorted order.

Unlike Bubble Sort, Selection Sort, and Insertion Sort, Merge Sort guarantees a time complexity of **O(n log n)**.

---

## How It Works

Merge Sort follows three steps:

1. Divide the array into two halves.
2. Recursively sort each half.
3. Merge the sorted halves.

---

## Example

Given:

```text
[38, 27, 43, 3, 9, 82, 10]
```

### Step 1: Divide

```text
[38, 27, 43, 3, 9, 82, 10]

        ↓

[38, 27, 43]    [3, 9, 82, 10]
```

---

### Step 2: Keep Dividing

```text
[38, 27, 43]
   ↓
[38] [27, 43]
      ↓
    [27] [43]
```

```text
[3, 9, 82, 10]
      ↓
[3, 9] [82, 10]

 ↓        ↓

[3] [9] [82] [10]
```

Now every subarray contains a single element.

---

### Step 3: Merge Sorted Arrays

Merge:

```text
[27] + [43]
```

Result:

```text
[27, 43]
```

Merge:

```text
[38] + [27, 43]
```

Result:

```text
[27, 38, 43]
```

Merge:

```text
[3] + [9]
```

Result:

```text
[3, 9]
```

Merge:

```text
[82] + [10]
```

Result:

```text
[10, 82]
```

Merge:

```text
[3, 9] + [10, 82]
```

Result:

```text
[3, 9, 10, 82]
```

Final merge:

```text
[27, 38, 43] + [3, 9, 10, 82]
```

Result:

```text
[3, 9, 10, 27, 38, 43, 82]
```

---

## Visualization

```text
                [38,27,43,3,9,82,10]

                    /         \

          [38,27,43]         [3,9,82,10]

           /     \             /      \

        [38]   [27,43]      [3,9]   [82,10]

                /  \         / \      / \

             [27][43]     [3][9]  [82][10]

                    Merge Back

             [27,43]      [3,9]    [10,82]

                 \           /        /

                [27,38,43] [3,9,10,82]

                        \      /

              [3,9,10,27,38,43,82]
```

---

## JavaScript Implementation

```javascript
function mergeSort(arr) {
  if (arr.length <= 1) {
    return arr;
  }

  const middle = Math.floor(arr.length / 2);

  const left = arr.slice(0, middle);
  const right = arr.slice(middle);

  return merge(mergeSort(left), mergeSort(right));
}

function merge(left, right) {
  const result = [];

  let i = 0;
  let j = 0;

  while (i < left.length && j < right.length) {
    if (left[i] < right[j]) {
      result.push(left[i]);
      i++;
    } else {
      result.push(right[j]);
      j++;
    }
  }

  return result.concat(left.slice(i)).concat(right.slice(j));
}

const numbers = [38, 27, 43, 3, 9, 82, 10];

console.log(mergeSort(numbers));
```

### Output

```text
[3, 9, 10, 27, 38, 43, 82]
```

---

## Dry Run

Sorting:

```text
[8, 4, 2, 6]
```

### Divide

```text
[8, 4] [2, 6]
```

```text
[8] [4] [2] [6]
```

### Merge

```text
[8] + [4]
→ [4, 8]
```

```text
[2] + [6]
→ [2, 6]
```

```text
[4, 8] + [2, 6]
→ [2, 4, 6, 8]
```

---

## Time Complexity

| Case         | Time Complexity |
| ------------ | --------------- |
| Best Case    | O(n log n)      |
| Average Case | O(n log n)      |
| Worst Case   | O(n log n)      |

---

## Space Complexity

```text
O(n)
```

Merge Sort requires additional memory for temporary arrays during merging.

---

## Characteristics

### Advantages

- Guaranteed O(n log n) performance.
- Stable sorting algorithm.
- Efficient for large datasets.
- Works well for linked lists.
- Ideal for external sorting (large files).

### Disadvantages

- Requires extra memory.
- More complex than Bubble Sort or Insertion Sort.
- Usually slower than Quick Sort in practice due to memory overhead.

---

## Merge Sort vs Quick Sort

| Feature        | Merge Sort | Quick Sort |
| -------------- | ---------- | ---------- |
| Average Time   | O(n log n) | O(n log n) |
| Worst Time     | O(n log n) | O(n²)      |
| Space          | O(n)       | O(log n)   |
| Stable         | Yes        | No         |
| Large Datasets | Excellent  | Excellent  |
| Linked Lists   | Excellent  | Poor       |

---

## Real-World Usage

Merge Sort is commonly used in:

- Database systems
- External file sorting
- Distributed systems
- Large-scale data processing
- Stable sorting requirements

Many production systems use Merge Sort as part of hybrid algorithms.

---

## Key Idea

> Divide the array into smaller pieces, sort each piece, and merge the sorted pieces back together.
