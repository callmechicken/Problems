---
title: 1. 两数之和
date: 2021/3/10
categories:
- LeetCode
tags:
- 数组
---

[题目链接](https://leetcode-cn.com/problems/array-partition-i/)

#### 暴力解法

找到规律就是扫一遍的事。

```java
import java.util.Arrays;

class Solution {
    public int arrayPairSum(int[] nums) {
        Arrays.sort(nums);
        int n = nums.length;
        int sum = 0;
        for (int i = n - 2; i >= 0; i -= 2) {
            sum += nums[i];
        }
        return sum;
    }
}
```

- 时间复杂度：*O(n log n)*
- 空间复杂度：*O(log n)*
