---
title: 304. 二维区域和检索 - 矩阵不可变
date: 2021/3/9
categories:
- LeetCode
tags:
- 数组
- 前缀和
- 二维前缀和
---

[题目链接](https://leetcode-cn.com/problems/range-sum-query-2d-immutable/)

#### 一维前缀和解法

对矩阵的每一行计算前缀和，检索时对二维区域中的每一行计算和，然后对每一行的和计算总和。

```java
class NumMatrix {

    int[][] preSums;

    public NumMatrix(int[][] matrix) {
        int n = matrix.length;
        if (n == 0) {
            return;
        }
        int m = matrix[0].length;
        preSums = new int[n][m + 1];
        for (int i = 0; i < n; i++) {
            preSums[i][0] = 0;
            for (int j = 0; j < m; j++) {
                preSums[i][j + 1] = preSums[i][j] + matrix[i][j];
            }
        }
    }
    
    public int sumRegion(int row1, int col1, int row2, int col2) {
        int sum = 0;
        while (row1 <= row2) {
            sum += preSums[row1][col2 + 1] - preSums[row1][col1];
            row1++;
        }
        return sum;
    }
}
```

- 时间复杂度：计算前缀和为 *O(mn)*，每次检索为 *O(m)*
- 空间复杂度：*O(mn)*

#### 二维前缀和解法

二位前缀和数组中的每一个元素，是以自己为右下角端点的矩阵中所有元素值的和。

```java
class NumMatrix {
    
    int[][] preSums;
    
    public NumMatrix(int[][] matrix) {
        int n = matrix.length;
        if (n <= 0) {
            return;
        }
        int m = matrix[0].length;
        preSums = new int[n + 1][m + 1];
        for (int i = 0; i < n; i++) {
            for (int j = 0; j < m; j++) {
                preSums[i + 1][j + 1] = preSums[i][j + 1] + preSums[i + 1][j] - preSums[i][j] + matrix[i][j];
            }
        }
    }
    
    public int sumRegion(int row1, int col1, int row2, int col2) {
        return preSums[row2 + 1][col2 + 1] - preSums[row1][col2 + 1] - preSums[row2 + 1][col1] + preSums[row1][col1];
    }
}
```

- 时间复杂度：计算前缀和为 *O(mn)*，每次检索为 *O(1)*
- 空间复杂度：*O(mn)*