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

当 a、b 指针的位置不一样时，a 一定处在 0 的位置上，而 b 略过而没有发生交换的位置肯定为 0，最后 b 一定停在非 0 的位置上，然后进行交换。

当 a 和 b 处在同一个位置上时，而当前位置的元素又不为 0，则会发生原地交换。

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
