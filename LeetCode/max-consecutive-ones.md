---
title: 485. 最大连续 1 的个数
date: 2021/3/13
categories:
- LeetCode
tags:
- 数组
---

[题目链接](https://leetcode-cn.com/problems/max-consecutive-ones/)

#### 解法

记录当前最大连续 1 的个数，每次遇到 0 的时候就将当前的个数和之前的进行比较，然后重新计数。

```java
class Solution {
    public int findMaxConsecutiveOnes(int[] nums) {
        int maxCount = 0, count = 0;
        int n = nums.length;
        for (int i = 0; i < n; i++) {
            if (nums[i] == 1) {
                count++;
            } else {
                maxCount = Math.max(maxCount, count);
                count = 0;
            }
        }
        maxCount = Math.max(maxCount, count);
        return maxCount;
    }
}
```

- 时间复杂度：*O(N)*
- 空间复杂度：*O(1)*
