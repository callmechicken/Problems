---
title: 303. 区域和检索 - 数组不可变
date: 2021/3/9
categories:
- LeetCode
tags:
- 数组
- 前缀和
---

[题目链接](https://leetcode-cn.com/problems/range-sum-query-immutable/)

#### 前缀和解法

`preSum[i]` 就是 `nums[0...i - 1]` 的和。如果我们想求 `nums[i..j]` 的和，只需要一步操作 `preSum[j + 1]` - `preSum[i]` 即可，而不需要去遍历数组了。

```java
class NumArray {
    
    int[] sums;

    public NumArray(int[] nums) {
        int n = nums.length;
        sums = new int[n + 1];
        for (int i = 0; i < n; i++) {
            sums[i + 1] = sums[i] + nums[i];
        }
    }
    
    public int sumRange(int i, int j) {
        return sums[j + 1] - sums[i];
    }
}
```

- 时间复杂度：计算前缀和为 *O(N)*，每次检索为 *O(1)*
- 空间复杂度：*O(N)*

