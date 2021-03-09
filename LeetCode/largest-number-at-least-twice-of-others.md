---
title: 747. 至少是其他数字两倍的最大数
date: 2021/3/9
categories:
- LeetCode
tags:
- 数组
---

[题目链接](https://leetcode-cn.com/problems/largest-number-at-least-twice-of-others/)

#### 暴力解法

找出最大值和第二大值，记录最大值的索引，如果最大值小于第二大值的两倍，则返回 -1。

```java
class Solution {
    public int dominantIndex(int[] nums) {
        int n = nums.length;
        if (n == 1) {
            return 0;
        }
        int firstMax = 0;
        int secondMax = 0;
        int index = 0;
        for (int i = 0; i < n; i++) {
            if (nums[i] > firstMax) {
                secondMax = firstMax;
                firstMax = nums[i];
                index = i;
            } else {
                secondMax = Math.max(secondMax, nums[i]);
            }
        }
        return firstMax >= secondMax * 2 ? index : -1;
    }
}
```

- 时间复杂度：*O(N)*
- 空间复杂度：*O(1)*
