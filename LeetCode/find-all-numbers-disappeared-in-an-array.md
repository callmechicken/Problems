---
title: 448. 找到所有数组中消失的数字
date: 2021/3/12
categories:
- LeetCode
tags:
- 数组
---

[题目链接](https://leetcode-cn.com/problems/find-all-numbers-disappeared-in-an-array/)

#### 解法

遍历 `nums`，每遇到一个数 `x`，就让 `nums[x − 1]` 增加 `n`。由于 `nums` 中所有数均在 `[1, n]` 中，增加以后，这些数必然大于 `n`。最后遍历 `nums`，若 `nums[i]` 未大于 `n`，就说明没有遇到过数 `i + 1`。这样就找到了缺失的数字。

```java
class Solution {
    public List<Integer> findDisappearedNumbers(int[] nums) {
        int n = nums.length;
        for (int num : nums) {
            int x = (num - 1) % n;
            nums[x] += n;
        }
        List<Integer> ret = new ArrayList<Integer>();
        for (int i = 0; i < n; i++) {
            if (nums[i] <= n) {
                ret.add(i + 1);
            }
        }
        return ret;
    }
}
```

- 时间复杂度：*O(N)*
- 空间复杂度：*O(1)*
