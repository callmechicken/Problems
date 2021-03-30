---
title: 674. 最长连续递增序列
date: 2021/3/30
categories:
- LeetCode
tags:
- 数组
---

[题目链接](https://leetcode-cn.com/problems/longest-continuous-increasing-subsequence/)

#### 解法

```java
class Solution {
    public int findLengthOfLCIS(int[] nums) {
        int len = nums.length;
        if (len <= 1) {
            return len;
        }
        int ans = 1;
        int count = 1;
        for (int i = 0; i < len - 1; i++) {
            if (nums[i + 1] > nums[i]) {
                count++;
            } else {
                count = 1;
            }
//            ans = Math.max(count, ans);
            ans = count > ans ? count : ans;
        }
        return ans;
    }
}
```

- 时间复杂度：*O(N)*
- 空间复杂度：*O(1)*

