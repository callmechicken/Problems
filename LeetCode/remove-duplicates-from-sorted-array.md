---
title: 26. 删除排序数组中的重复项
date: 2021/3/10
categories:
- LeetCode
tags:
- 数组
- 快慢指针
---

[题目链接](https://leetcode-cn.com/problems/remove-duplicates-from-sorted-array/)

#### 快慢指针解法

放置两个指针 `i` 和 `j`，其中 `i` 是慢指针，而 `j` 是快指针。只要 `nums[i] == nums[j]`，我们就增加 `j` 以跳过重复项。

当遇到 `nums[j] != nums[i]` 时，跳过重复项的运行已经结束，因此把 `nums[j]` 的值复制到 `nums[i + 1]`。然后递增 `i`，接着重复相同的过程，直到 `j` 到达数组的末尾为止。

```java
class Solution {
    public int removeDuplicates(int[] nums) {
        int i = 0;
        for (int j = 1; j < nums.length; j++) {
            if (nums[i] != nums[j]) {
                if(j - i > 1) { // 避免发生原地交换
                    nums[i + 1] = nums[j];
                }
                i++;
            }
        }
        return i + 1;
    }
}
```

- 时间复杂度：*O(N)*
- 空间复杂度：*O(1)*
