---
title: 941. 有效的山脉数组
date: 2021/3/12
categories:
- LeetCode
tags:
- 数组
- 模拟
- 双指针
---

[题目链接](https://leetcode-cn.com/problems/valid-mountain-array/)

#### 双指针解法

##### 一路扫过去

先递增扫，找最高点，找到之后判断最高点是否在数组的最左边或者最右边，然后递减扫，如果扫完了则说明是有效的山脉数组。

```java
class Solution {
    public boolean validMountainArray(int[] arr) {
        int N = arr.length;
        int i = 0;

        while (i + 1 < N && arr[i] < arr[i + 1]) {
            i++;
        }

        if (i == 0 || i == N - 1) {
            return false;
        }

        while (i + 1 < N && arr[i] > arr[i + 1]) {
            i++;
        }

        return i == N - 1;
    }
}
```

##### 两边一起扫

看左右两边找到的是不是同一个山峰。

```java
class Solution {
    public boolean validMountainArray(int[] A) {
        int len = A.length;
        int left = 0;
        int right = len - 1;
        //从左边往右边找，一直找到山峰为止
        while (left + 1 < len && A[left] < A[left + 1])
            left++;
        //从右边往左边找，一直找到山峰为止
        while (right > 0 && A[right - 1] > A[right])
            right--;
        //判断从左边和从右边找的山峰是不是同一个
        return left > 0 && right < len - 1 && left == right;
    }
}
```

- 时间复杂度：*O(N)*
- 空间复杂度：*O(1)*
