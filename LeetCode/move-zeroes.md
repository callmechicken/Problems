---
title: 283. 移动零
date: 2021/3/10
categories:
- LeetCode
tags:
- 数组
- 快慢指针
---

[题目链接](https://leetcode-cn.com/problems/move-zeroes/)

#### 快慢指针解法

左指针指向当前已经处理好的序列的尾部，右指针指向待处理序列的头部。

右指针不断向右移动，每次右指针指向非零数，则将左右指针对应的数交换，同时左指针右移。

注意到以下性质：

1. 左指针左边均为非零数；
2. 右指针左边直到左指针处均为零。

```java
class Solution {
    public void moveZeroes(int[] nums) {
        int a = 0, b = 0, temp;
        while (b < nums.length) {
            if (nums[b] != 0) {
                temp = nums[a];
                nums[a] = nums[b];
                nums[b] = temp;
                a++;
            }
            b++;
        }
    }
}
```

- 时间复杂度：*O(N)*
- 空间复杂度：*O(1)*
