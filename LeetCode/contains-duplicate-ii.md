---
title: 219. 存在重复元素 II
date: 2021/3/28
categories:
- LeetCode
tags:
- 数组
- 哈希
---

[题目链接](https://leetcode-cn.com/problems/contains-duplicate-ii/)

#### 哈希解法

用 **Map** 的键存 `nums` 中的元素，用值存元素的索引。

```java
class Solution {
    public boolean containsNearbyDuplicate(int[] nums, int k) {
        HashMap<Integer, Integer> hashMap = new HashMap<>();
        for (int i = 0; i < nums.length; i++) {
            if (hashMap.containsKey(nums[i]) && Math.abs(hashMap.get(nums[i]) - i) <= k) {
                return true;
            }
            hashMap.put(nums[i], i);
        }
        return false;
    }
}
```

- 时间复杂度：*O(n)*
- 空间复杂度：*O(n)*

