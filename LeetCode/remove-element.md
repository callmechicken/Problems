---
title: 27. 移除元素
date: 2021/3/10
categories:
- LeetCode
tags:
- 数组
- 快慢指针
- 对撞指针
---

[题目链接](https://leetcode-cn.com/problems/remove-element/)

#### 快慢指针解法

当 `nums[b]` 与给定的值相等时，递增 `b` 以跳过该元素。只要 `nums[b] != val`，就交换并同时递增两个索引。重复这一过程，直到 `b` 到达数组的末尾，该数组的新长度为 `a`。

```java
class Solution {
    public int removeElement(int[] nums, int val) {
        int a = 0, b = 0, temp;
        while (b < nums.length) {
            if (nums[b] != val) {
                temp = nums[a];
                nums[a] = nums[b];
                nums[b] = temp;
                a++;
            }
            b++;
        }
        return a;
    }
}
```

- 时间复杂度：*O(N)*
- 空间复杂度：*O(1)*

#### 对撞指针解法

将当前元素与最后一个元素交换，将数组的大小减少 1。被交换的最后一个元素可能是你想要移除的值。但在下一次扫描中，还会再检查这个元素。

```java
class Solution {
    public int removeElement(int[] nums, int val) {
        int i = 0;
        int n = nums.length;
        while (i < n) {
            if (nums[i] == val) {
                nums[i] = nums[n - 1];
                n--;
            } else {
                i++;
            }
        }
        return n;
    }
}
```

- 时间复杂度：*O(N)*
- 空间复杂度：*O(1)*