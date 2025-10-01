---
title: Binary Search Algorithm
tags:
  - algorithm
  - search
  - time-complexity
  - computer-science
---

# Binary Search

Binary search is an efficient algorithm for finding an item from a **sorted list** of items. It works by repeatedly dividing in half the portion of the list that could contain the item, until you've narrowed down the possible locations to just one.

## How it Works

1.  **Start with the middle element:** Compare the target value with the middle element of the sorted list.
2.  **Three possibilities:**
    *   If the target value is equal to the middle element, the search is successful, and its position is returned.
    *   If the target value is less than the middle element, the search continues in the lower half of the list.
    *   If the target value is greater than the middle element, the search continues in the upper half of the list.
3.  **Repeat:** This process is repeated until the target value is found or the remaining portion of the list is empty.

## Example

Let's say we want to find the number 23 in the following sorted list:
`[2, 5, 8, 12, 16, 23, 38, 56, 72, 91]`

1.  **Initial range:** `[2, 5, 8, 12, 16, 23, 38, 56, 72, 91]`
    *   Middle element: 16.
    *   23 > 16, so we search the upper half.
2.  **New range:** `[23, 38, 56, 72, 91]`
    *   Middle element: 56.
    *   23 < 56, so we search the lower half.
3.  **New range:** `[23, 38]`
    *   Middle element: 38.
    *   23 < 38, so we search the lower half.
4.  **New range:** `[23]`
    *   Middle element: 23.
    *   23 == 23, target found!

## Time Complexity

The time complexity of binary search is logarithmic, which is very efficient, especially for large lists.

*   **Worst-case time complexity:** $O(\log n)$
*   **Average-case time complexity:** $O(\log n)$
*   **Best-case time complexity:** $O(1)$ (when the target element is the middle element on the first try)

### Explanation of $O(\log n)$

In each step of binary search, the search space is halved.
*   Initially, the search space is $n$.
*   After 1 step, the search space is $n/2$.
*   After 2 steps, the search space is $n/4$.
*   After $k$ steps, the search space is $n/2^k$.

We stop when the search space is reduced to 1 element. So, we set $n/2^k = 1$.
Solving for $k$:
$n = 2^k$
$\log_2 n = k$

Therefore, the number of steps (and thus the time complexity) is proportional to $\log n$. This means that even for very large lists, binary search can find an element in a relatively small number of steps. For example, for a list of 1 million elements, binary search would take at most about 20 steps ($\log_2 1,000,000 \approx 19.9$).

Adding to one of these sorted lists gives us **O(n)** time, 
And removing from this list gives us **O(n)** time as well *(Because we have to shift everything)*

