---
title: 66. 加一
date: 2021/3/9
categories:
- LeetCode
tags:
- 模拟
---

[题目链接](https://leetcode-cn.com/problems/plus-one/)

#### 解法

从后往前扫，如果当前位数字为9，那么这位数字加 1 后就余下 0 产生进位；如果当前位数字不为 9，那么该位数字加 1，直接返回数组即可。

```java
class Solution {
    public int[] plusOne(int[] digits) {
        for (int i = digits.length - 1; i >= 0; i--) {
            if (digits[i] != 9) {
                digits[i]++;
                return digits;
            }
            digits[i] = 0;
        }
        //跳出for循环，说明数字全部是9
        int[] result = new int[digits.length + 1];
        result[0] = 1;
        return result;
    }
}
```

- 时间复杂度：*O(N)*
- 空间复杂度：*O(N)*
