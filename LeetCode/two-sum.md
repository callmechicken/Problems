---
title: 1. 两数之和
date: 2021/3/8
categories:
- LeetCode
tags:
- 数组
- 遍历
- 哈希
---

[题目链接](https://leetcode-cn.com/problems/two-sum/)

#### 暴力解法

枚举数组中的每一个数 `x`，寻找数组中是否存在 `target - x`。

```java
class Solution {
    public int[] twoSum(int[] nums, int target) {
        int[] result = new int[2];
        int n = nums.length;
        for (int i = 0; i < n - 1; i++) {
            for (int j = i + 1; j < n; j++) {
                if (nums[i] + nums[j] == target) {
                    result[0] = i;
                    result[1] = j;
                    return result;
                }
            }
        }
        return result;
    }
}
```

- 时间复杂度：*O(N^2)*
- 空间复杂度：*O(1)*

#### 哈希解法

枚举数组中的每一个数 `x`，寻找哈希表中是否有 `target - x`，若没有，则将 `x` 当作键，它的索引当成值，插入到哈希表中，后面找到其对应数的时候，只用 *O(1)* 的时间就能找到之前的数和其索引。

```java
import java.util.HashMap;

class Solution {
    public int[] twoSum(int[] nums, int target) {
        HashMap<Integer, Integer> hashMap = new HashMap<>();
        int[] result = new int[2];
        for (int i = 0; i < nums.length; i++) {
            if (hashMap.containsKey(target - nums[i])) {
                result[0] = hashMap.get(target - nums[i]);
                result[1] = i;
                return result;
            }
            hashMap.put(nums[i], i);
        }
        return result;
    }
}
```

- 时间复杂度：*O(N)*
- 空间复杂度：*O(N)*