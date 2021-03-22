---
title: 11. 盛最多水的容器
date: 2021/3/22
categories:
- LeetCode
tags:
- 数组
- 对撞指针
---

[题目链接](https://leetcode-cn.com/problems/container-with-most-water/)

#### 对撞指针解法

```java
class Solution {
    public int maxArea(int[] height) {
        int res = 0;
        int i = 0;
        int j = height.length - 1;
        while (i < j) {
            int area = (j - i) * Math.min(height[i], height[j]);
            res = Math.max(res, area);
            if (height[i] < height[j]) {
                i++;
            } else {
                j--;
            }
        }
        return res;
    }
}
```

- 时间复杂度：*O(N)*
- 空间复杂度：*O(1)*
