---
publish: true
title: "Valid Sudoku"
description: "Validate a 9x9 Sudoku board using sets for rows, columns, and 3x3 boxes in O(1) time."
thumbnail: _assets/thumbnails/lc.png
published: 2025-06-11
tags:
  - LeetCode
  - POTD
category: Blog
likes: 0
views: 0
created: 2025-06-11T14:50
updated: 2026-03-25T14:00
---

## Problem Statement

[Leetcode: Valid Sudoku](https://leetcode.com/problems/valid-sudoku)

[GFG: Is Sudoku Valid](https://www.geeksforgeeks.org/problems/is-sudoku-valid4820/1)

We are given a **partially filled 9x9 Sudoku board**. We need to validate whether the current state of the board is valid or not. A board is considered **valid** if:

- Each **row** contains digits 1–9 **without repetition**.
- Each **column** contains digits 1–9 **without repetition**.
- Each of the **nine 3x3 sub-boxes** contains digits 1–9 **without repetition**.

Empty cells may be represented by `0` or `'.'`

## Approach

1. Create **9 sets for each** row, column, and 3x3 box
2. For every filled cell `mat[i][j]`:
    - Skip if the value is `0`.
    - Calculate the box index using: `boxIndex = 3 * (i / 3) + (j / 3)`
    - Check if the value already exists in:
        - `row[i]`
        - `col[j]`
        - `box[boxIndex]`
    - If **any set already contains** the value, return `false`.
    - Otherwise, insert the value into all three sets.

```cpp
class Solution {
  public:
    bool isValid(vector<vector<int>>& mat) {
        vector<set<int>> row(9), col(9), box(9);

        for(int i = 0; i < 9; i++) {
            for(int j = 0; j < 9; j++) {
                int val = mat[i][j];
                if(val == 0) continue;  // Skip empty cells

                int boxIndex = 3 * (i / 3) + (j / 3);

                // Check if value already exists in row, column or box
                if(row[i].count(val) || col[j].count(val) || box[boxIndex].count(val))
                    return false;

                // Insert the value into respective sets
                row[i].insert(val);
                col[j].insert(val);
                box[boxIndex].insert(val);
            }
        }

        return true;
    }
};
```

## Time and Space Complexity

- **Time Complexity:** `O(81)` = `O(1)`
    
    (Since the board is always 9x9)
    
- **Space Complexity:** `O(27)` = `O(1)`
    
    (9 sets each for row, column, and box)

## Related

- [[blog/leetcode-weekly-contest-144|LeetCode Weekly Contest 144]] — more LeetCode solutions with arrays and trees.
- [[blog/game-of-xor|Game of XOR]] — another array-based problem with a clean O(N) trick.
