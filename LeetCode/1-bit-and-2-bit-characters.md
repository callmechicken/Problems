---
title: 717. 1比特与2比特字符
date: 2021/3/10
categories:
- LeetCode
tags:
- 数组
---

[题目链接](https://leetcode-cn.com/problems/1-bit-and-2-bit-characters/)

#### 暴力解法

如果是 0，则从下一位开始扫，如果是 1，则从下两位开始扫。

```java
class Solution {
    public boolean isOneBitCharacter(int[] bits) {
        int n = bits.length;
        if (bits[n - 1] == 1) {
            return false;
        }
        boolean 一比特字符 = false;
        for (int i = 0; i < n; i++) {
            if (bits[i] == 1) {
                一比特字符 = false;
                i++;
            } else {
                一比特字符 = true;
            }
        }
        return 一比特字符;
    }
}
```

- 时间复杂度：*O(N)*
- 空间复杂度：*O(1)*

