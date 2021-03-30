---
title: 724. 寻找数组的中心下标
date: 2021/3/30
categories:
- LeetCode
tags:
- 模拟
---

[题目链接](https://leetcode-cn.com/problems/find-pivot-index/)

#### 解法

左边元素的和 + 当前元素 = 总元素和。

```java
class Solution {
    public int pivotIndex(int[] nums) {
        int total = Arrays.stream(nums).sum();
        int sum = 0;
        for (int i = 0; i < nums.length; ++i) {
            if (2 * sum + nums[i] == total) {
                return i;
            }
            sum += nums[i];
        }
        return -1;
    }
}
```

- 时间复杂度：*O(N)*
- 空间复杂度：*O(1)*

