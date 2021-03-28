---
title: 1572. 矩阵对角线元素的和
date: 2021/3/28
categories:
- LeetCode
tags:
- 模拟
---

[题目链接](https://leetcode-cn.com/problems/matrix-diagonal-sum/)

#### 解法

这题很简单，搞清楚题目数据的规律，偶数矩阵不需要计算重复的那项，而奇数的矩阵要。

```java
public class Solution {
    public int diagonalSum(int[][] mat) {
        int n = mat.length;
        int sum = 0;
        for (int i = 0; i < n; i++) {
            sum += mat[i][i];
        }
        for (int i = n - 1, j = 0; i >= 0; i--, j++) {
            sum += mat[j][i];
        }
        if (n % 2 != 0) {
            sum -= mat[n / 2][n / 2];
        }
        return sum;
    }
}
```

- 时间复杂度：*O(N)*
- 空间复杂度：*O(1)*

