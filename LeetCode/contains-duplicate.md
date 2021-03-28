---
title: 217. 存在重复元素
date: 2021/3/28
categories:
- LeetCode
tags:
- 数组
---

[题目链接](https://leetcode-cn.com/problems/contains-duplicate/)

#### 排序解法

排序后的相邻元素会贴在一起。

```java
class Solution {
    public boolean containsDuplicate(int[] nums) {
        Arrays.sort(nums);
        for (int i = 0; i < nums.length - 1; ++i) {
            if (nums[i] == nums[i + 1]) {
                return true;
            }
        }
        return false;
    }
}
```

- 时间复杂度：*O(n log n)*
- 空间复杂度：*O(1)*

#### 利用数据结构的解法

主要是 **contains** 函数，它能在 *O(1)* 的时间找到元素，不用 **Map** 是因为键值对有点冗余。

```java
class Solution {
    public boolean containsDuplicate(int[] nums) {
        HashSet<Integer> set = new HashSet<>();
        for (int num: nums) {
            if (set.contains(num)) {
                return true;
            }
            set.add(num);
        }
        return false;
    }
}
```

- 时间复杂度：*O(n)*
- 空间复杂度：*O(n)*