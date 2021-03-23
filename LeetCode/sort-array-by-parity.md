---
title: 905. 按奇偶排序数组
date: 2021/3/23
categories:
- LeetCode
tags:
- 数组
- 快慢指针
---

[题目链接](https://leetcode-cn.com/problems/sort-array-by-parity/)

#### 双指针解法

```java
class Solution {
    public int[] sortArrayByParity(int[] A) {
        for (int i = 0, j = 0; j < A.length; j++)
            if (A[j] % 2 == 0) {
                int tmp = A[i];
                A[i++] = A[j];
                A[j] = tmp;;
            }
        return A;
    }
}
```

- 时间复杂度：*O(N)*
- 空间复杂度：*O(1)*