---
title: 665. 非递减数列
date: 2021/3/13
categories:
- LeetCode
tags:
- 数组
---

[题目链接](https://leetcode-cn.com/problems/non-decreasing-array/)

#### 解法

搞清楚数据的规律。

[题解](https://leetcode-cn.com/problems/non-decreasing-array/solution/3-zhang-dong-tu-bang-zhu-ni-li-jie-zhe-d-06gi/)

```java
class Solution {
    public boolean checkPossibility(int[] nums) {
        int count = 0;
        int n = nums.length;
        for (int i = 1; i < n; i++) {
            if (nums[i] < nums[i - 1]) {
                if (i == 1 || nums[i] >= nums[i - 2]) {
                    nums[i - 1] = nums[i];
                } else {
                    nums[i] = nums[i - 1];
                }
                count ++;
            }
        }
        return count <= 1;
    }
}
```

- 时间复杂度：*O(N)*
- 空间复杂度：*O(1)*
