---
title: 75. 颜色分类
date: 2021/3/10
categories:
- LeetCode
tags:
- 数组
- 快慢指针
---

[题目链接](https://leetcode-cn.com/problems/sort-colors/)

#### 快慢指针解法

对数组进行两次扫描。在第一次扫描中，将数组中所有的 0 交换到数组的头部。在第二次扫描中，将数组中所有的 1 交换到头部的 0 之后。此时，所有的 2 都出现在数组的尾部，这样我们就完成了排序。

```java
class Solution {
    public void sortColors(int[] nums) {
        int n = nums.length;
        int ptr = 0;
        for (int i = 0; i < n; ++i) {
            if (nums[i] == 0) {
                int temp = nums[i];
                nums[i] = nums[ptr];
                nums[ptr] = temp;
                ++ptr;
            }
        }
        for (int i = ptr; i < n; ++i) {
            if (nums[i] == 1) {
                int temp = nums[i];
                nums[i] = nums[ptr];
                nums[ptr] = temp;
                ++ptr;
            }
        }
    }
}
```

- 时间复杂度：*O(N)*
- 空间复杂度：*O(1)*
