# DAA Lab Task 3 — Section A & Section B: Theory & Logic Tracing

---

# Section A: Concept Check — Answers

1. Bubble sort works by repeatedly swapping **adjacent** elements if they are in the wrong order.

2. Selection sort repeatedly finds the **minimum** (or **smallest**) element from the unsorted part and places it at the beginning.

3. Insertion sort builds the sorted portion one element at a time by **inserting** each new element into its correct position.

4. Merge sort follows a **divide** and **conquer** approach: split the array, sort each half, then combine.

5. Quick sort picks a **pivot** and partitions the array around it before recursing.

6. Heap sort relies on a data structure called a **heap** (or **binary heap** / **max-heap**), which is typically implemented using an array.

7. Radix sort processes numbers digit by digit, starting from the **least** significant digit (in the standard LSD version).

8. Binary search requires the input array to be **sorted** before it can be used.

9. In hashing, when two different keys map to the same index, this is called a **collision**.

10. Separate chaining resolves collisions by storing multiple values at the same index using a **linked list** (or **chain**), while linear probing resolves them by **searching for the next open/available slot sequentially** (probing `(index + 1) % table_size`).

---

# Section B: Trace the Logic (Step-by-Step)

---

### Question 1: Trace Bubble Sort on `[5, 2, 8, 1, 9]` for One Full Pass
**Initial Array:** `[5, 2, 8, 1, 9]`  
Length $n = 5$. One full pass checks adjacent pairs `(arr[j], arr[j+1])` for $j = 0, 1, 2, 3$:

| Step | Comparison | Action | Array State After Step |
| :--- | :--- | :--- | :--- |
| **Start** | — | — | `[5, 2, 8, 1, 9]` |
| **Pair 1** | Compare `arr[0]` (5) & `arr[1]` (2): $5 > 2$ | **Swap (Swap 1)** | `[2, 5, 8, 1, 9]` |
| **Pair 2** | Compare `arr[1]` (5) & `arr[2]` (8): $5 < 8$ | No swap | `[2, 5, 8, 1, 9]` |
| **Pair 3** | Compare `arr[2]` (8) & `arr[3]` (1): $8 > 1$ | **Swap (Swap 2)** | `[2, 5, 1, 8, 9]` |
| **Pair 4** | Compare `arr[3]` (8) & `arr[4]` (9): $8 < 9$ | No swap | `[2, 5, 1, 8, 9]` |

- **Array after Swap 1:** `[2, 5, 8, 1, 9]`
- **Array after Swap 2:** `[2, 5, 1, 8, 9]`
- **Final Array after 1 full pass:** `[2, 5, 1, 8, 9]` (largest element 9 has bubbled to the end).

---

### Question 2: Trace Selection Sort on `[5, 2, 8, 1, 9]` (4 Selection-and-Swap Steps)
**Initial Array:** `[5, 2, 8, 1, 9]`

- **Step 1 ($i = 0$):**
  - Unsorted slice: `[5, 2, 8, 1, 9]` (indices 0 to 4)
  - Minimum element is `1` at index 3.
  - Swap `arr[0]` (5) with `arr[3]` (1).
  - **Array after Step 1:** `[1, 2, 8, 5, 9]`

- **Step 2 ($i = 1$):**
  - Unsorted slice: `[2, 8, 5, 9]` (indices 1 to 4)
  - Minimum element is `2` at index 1.
  - Swap `arr[1]` (2) with itself (no movement).
  - **Array after Step 2:** `[1, 2, 8, 5, 9]`

- **Step 3 ($i = 2$):**
  - Unsorted slice: `[8, 5, 9]` (indices 2 to 4)
  - Minimum element is `5` at index 3.
  - Swap `arr[2]` (8) with `arr[3]` (5).
  - **Array after Step 3:** `[1, 2, 5, 8, 9]`

- **Step 4 ($i = 3$):**
  - Unsorted slice: `[8, 9]` (indices 3 to 4)
  - Minimum element is `8` at index 3.
  - Swap `arr[3]` (8) with itself.
  - **Array after Step 4:** `[1, 2, 5, 8, 9]`

**Final Sorted Array:** `[1, 2, 5, 8, 9]`

---

### Question 3: Trace Insertion Sort on `[5, 2, 8, 1, 9]`
**Initial Array:** `[5, 2, 8, 1, 9]`  
Initial sorted subarray: `[5]`

- **Step 1 (Insert element `arr[1] = 2`):**
  - Compare 2 with 5: $2 < 5$, shift 5 to index 1, place 2 at index 0.
  - **Array after inserting 2:** `[2, 5, 8, 1, 9]` (sorted portion: `[2, 5]`)

- **Step 2 (Insert element `arr[2] = 8`):**
  - Compare 8 with 5: $8 > 5$, 8 remains at index 2.
  - **Array after inserting 8:** `[2, 5, 8, 1, 9]` (sorted portion: `[2, 5, 8]`)

- **Step 3 (Insert element `arr[3] = 1`):**
  - Compare 1 with 8: shift 8.
  - Compare 1 with 5: shift 5.
  - Compare 1 with 2: shift 2.
  - Place 1 at index 0.
  - **Array after inserting 1:** `[1, 2, 5, 8, 9]` (sorted portion: `[1, 2, 5, 8]`)

- **Step 4 (Insert element `arr[4] = 9`):**
  - Compare 9 with 8: $9 > 8$, 9 remains at index 4.
  - **Array after inserting 9:** `[1, 2, 5, 8, 9]` (sorted portion: `[1, 2, 5, 8, 9]`)

**Final Sorted Array:** `[1, 2, 5, 8, 9]`

---

### Question 4: Trace Merge Sort's Splitting Step Only on `[8, 3, 5, 4, 7, 6, 1, 2]`
Starting array: `[8, 3, 5, 4, 7, 6, 1, 2]` (size 8).

```
Level 0 (Original):
  [8, 3, 5, 4, 7, 6, 1, 2]

Level 1 (Split in halves):
  Left Subarray:   [8, 3, 5, 4]
  Right Subarray:  [7, 6, 1, 2]

Level 2 (Split each 4-element subarray):
  From [8, 3, 5, 4] -> [8, 3] and [5, 4]
  From [7, 6, 1, 2] -> [7, 6] and [1, 2]

Level 3 (Split each 2-element subarray into single-element subarrays):
  From [8, 3] -> [8] and [3]
  From [5, 4] -> [5] and [4]
  From [7, 6] -> [7] and [6]
  From [1, 2] -> [1] and [2]
```

**All sub-arrays produced until single-element base cases:**
- **Level 1:** `[8, 3, 5, 4]`, `[7, 6, 1, 2]`
- **Level 2:** `[8, 3]`, `[5, 4]`, `[7, 6]`, `[1, 2]`
- **Level 3 (Leaves):** `[8]`, `[3]`, `[5]`, `[4]`, `[7]`, `[6]`, `[1]`, `[2]`

---

### Question 5: Trace Quick Sort's First Partition Step on `[8, 3, 5, 4, 7, 6, 1, 2]` Using Pivot = Last Element (2)
- Input: `arr = [8, 3, 5, 4, 7, 6, 1, 2]`, `low = 0`, `high = 7`
- Pivot: `pivot = arr[7] = 2`
- Pointer $i = \text{low} - 1 = -1$

**Scan with index $j$ from $0$ to $6$:**
- $j = 0$: `arr[0] = 8` ($8 \le 2$ False) $\rightarrow i = -1$, array: `[8, 3, 5, 4, 7, 6, 1, 2]`
- $j = 1$: `arr[1] = 3` ($3 \le 2$ False) $\rightarrow i = -1$, array: `[8, 3, 5, 4, 7, 6, 1, 2]`
- $j = 2$: `arr[2] = 5` ($5 \le 2$ False) $\rightarrow i = -1$, array: `[8, 3, 5, 4, 7, 6, 1, 2]`
- $j = 3$: `arr[3] = 4` ($4 \le 2$ False) $\rightarrow i = -1$, array: `[8, 3, 5, 4, 7, 6, 1, 2]`
- $j = 4$: `arr[4] = 7` ($7 \le 2$ False) $\rightarrow i = -1$, array: `[8, 3, 5, 4, 7, 6, 1, 2]`
- $j = 5$: `arr[5] = 6` ($6 \le 2$ False) $\rightarrow i = -1$, array: `[8, 3, 5, 4, 7, 6, 1, 2]`
- $j = 6$: `arr[6] = 1` ($1 \le 2$ **True**):
  - Increment $i$: $i = 0$
  - Swap `arr[i]` (arr[0] = 8) with `arr[j]` (arr[6] = 1)
  - Array becomes: `[1, 3, 5, 4, 7, 6, 8, 2]`

**Final Pivot Placement:**
- Place pivot by swapping `arr[i + 1]` (`arr[1] = 3`) with `arr[high]` (`arr[7] = 2`):
- **Array after partition:** `[1, 2, 5, 4, 7, 6, 8, 3]`
- **Pivot's final index:** **Index 1**  
  (Left partition: `[1]` where elements $\le 2$; Right partition: `[5, 4, 7, 6, 8, 3]` where elements $> 2$).

---

### Question 6: Trace Radix Sort on `[170, 45, 75, 90, 802, 24, 2, 66]`

#### 1. Sort by Ones Digit ($num \% 10$):
- $170 \rightarrow 0$
- $45 \rightarrow 5$
- $75 \rightarrow 5$
- $90 \rightarrow 0$
- $802 \rightarrow 2$
- $24 \rightarrow 4$
- $2 \rightarrow 2$
- $66 \rightarrow 6$

Stable bucket grouping:
- Bucket 0: `170, 90`
- Bucket 2: `802, 2`
- Bucket 4: `24`
- Bucket 5: `45, 75`
- Bucket 6: `66`

**Array after sorting by ones digit:**  
`[170, 90, 802, 2, 24, 45, 75, 66]`

#### 2. Sort by Tens Digit ($(num // 10) \% 10$):
Input array: `[170, 90, 802, 2, 24, 45, 75, 66]`
- $170 \rightarrow 7$
- $90 \rightarrow 9$
- $802 \rightarrow 0$
- $2 \rightarrow 0$
- $24 \rightarrow 2$
- $45 \rightarrow 4$
- $75 \rightarrow 7$
- $66 \rightarrow 6$

Stable bucket grouping:
- Bucket 0: `802, 2`
- Bucket 2: `24`
- Bucket 4: `45`
- Bucket 6: `66`
- Bucket 7: `170, 75`
- Bucket 9: `90`

**Array after sorting by tens digit:**  
`[802, 2, 24, 45, 66, 170, 75, 90]`

---

### Question 7: Trace Binary Search for Value 23 on Sorted Array
**Array:** `[2, 5, 8, 12, 16, 23, 38, 45, 56, 72, 91]`  
Length $N = 11$, Target = $23$.

| Step | `low` | `high` | `mid` formula | `mid` | `arr[mid]` | Comparison with Target (23) |
| :---: | :---: | :---: | :---: | :---: | :---: | :--- |
| **1** | **0** | **10** | $(0 + 10) // 2$ | **5** | **23** | `arr[5] == 23` $\rightarrow$ **MATCH FOUND!** |

- Target 23 is found at index **5** in exactly **1 step / comparison**.

---

### Question 8: Separate Chaining Hash Table (Size 7, $h(key) = key \% 7$)
Keys inserted in order: `10, 3, 17, 24, 9`

1. **Insert 10:**
   - $h(10) = 10 \% 7 = 3$.
   - Slot 3 is empty. Insert 10.
   - **Collision:** None.
2. **Insert 3:**
   - $h(3) = 3 \% 7 = 3$.
   - Slot 3 already has 10.
   - **Collision:** Yes, with key 10.
   - Resolved by chaining to slot 3: `[10 -> 3]`.
3. **Insert 17:**
   - $h(17) = 17 \% 7 = 3$.
   - Slot 3 already has 10 and 3.
   - **Collision:** Yes, with keys 10 and 3.
   - Resolved by chaining to slot 3: `[10 -> 3 -> 17]`.
4. **Insert 24:**
   - $h(24) = 24 \% 7 = 3$.
   - Slot 3 already has 10, 3, 17.
   - **Collision:** Yes, with keys 10, 3, 17.
   - Resolved by chaining to slot 3: `[10 -> 3 -> 17 -> 24]`.
5. **Insert 9:**
   - $h(9) = 9 \% 7 = 2$.
   - Slot 2 is empty. Insert 9.
   - **Collision:** None.

#### Final Hash Table State (Separate Chaining):
| Index | Chain / Stored Keys |
| :---: | :--- |
| **0** | `Empty` |
| **1** | `Empty` |
| **2** | `[9]` |
| **3** | `[10 -> 3 -> 17 -> 24]` |
| **4** | `Empty` |
| **5** | `Empty` |
| **6** | `Empty` |

---

### Question 9: Linear Probing Hash Table (Size 7, $h(key) = key \% 7$)
Keys inserted in order: `10, 3, 17, 24, 9`  
Probing sequence: `(h(key) + i) % 7` for $i = 0, 1, 2, \dots$

1. **Insert 10:**
   - $h(10) = 10 \% 7 = 3$.
   - Slot 3 is empty $\rightarrow$ Place **10** at **Index 3**.
2. **Insert 3:**
   - $h(3) = 3 \% 7 = 3$. Slot 3 is occupied by 10 (Collision!).
   - Probe $(3 + 1) \% 7 = 4$. Slot 4 is empty $\rightarrow$ Place **3** at **Index 4**.
3. **Insert 17:**
   - $h(17) = 17 \% 7 = 3$. Slot 3 is occupied (Collision!).
   - Probe $(3 + 1) \% 7 = 4$. Slot 4 is occupied (Collision!).
   - Probe $(3 + 2) \% 7 = 5$. Slot 5 is empty $\rightarrow$ Place **17** at **Index 5**.
4. **Insert 24:**
   - $h(24) = 24 \% 7 = 3$. Slot 3 is occupied (Collision!).
   - Probe 4 is occupied (Collision!).
   - Probe 5 is occupied (Collision!).
   - Probe $(3 + 3) \% 7 = 6$. Slot 6 is empty $\rightarrow$ Place **24** at **Index 6**.
5. **Insert 9:**
   - $h(9) = 9 \% 7 = 2$.
   - Slot 2 is empty $\rightarrow$ Place **9** at **Index 2**.

#### Final Index of Each Key (Linear Probing):
| Key | Hash $key \% 7$ | Probes Made | Final Index |
| :---: | :---: | :---: | :---: |
| **9** | 2 | 1 (Slot 2) | **2** |
| **10** | 3 | 1 (Slot 3) | **3** |
| **3** | 3 | 2 (Slot 3 $\rightarrow$ Slot 4) | **4** |
| **17** | 3 | 3 (Slot 3 $\rightarrow$ Slot 4 $\rightarrow$ Slot 5) | **5** |
| **24** | 3 | 4 (Slot 3 $\rightarrow$ Slot 4 $\rightarrow$ Slot 5 $\rightarrow$ Slot 6) | **6** |

#### Final Hash Table Array:
`[None, None, 9, 10, 3, 17, 24]` (Indices 0 and 1 are empty).
