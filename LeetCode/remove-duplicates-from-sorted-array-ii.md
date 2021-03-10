---
title: 80. 删除排序数组中的重复项 II
date: 2021/3/10
categories:
- LeetCode
tags:
- 数组
- 快慢指针
---

[题目链接](https://leetcode-cn.com/problems/remove-duplicates-from-sorted-array-ii/)

#### 快慢指针解法

`a` 指针停留在待替换的项上（依赖 `count` 计数），`b` 指针往后扫描寻找替换项。

```java
class Solution {
    public int removeDuplicates(int[] nums) {
        int a = 1, count = 1;
        for (int b = 1; b < nums.length; b++) {
            if (nums[b] == nums[b - 1]) {
                count++;
            } else {
                count = 1;
            }
            if (count <= 2) {
                nums[a++] = nums[b];
            }
        }
        return a;
    }
}
```

- 时间复杂度：*O(N)*
- 空间复杂度：*O(1)*

