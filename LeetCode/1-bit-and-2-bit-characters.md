---
title: 717. 1比特与2比特字符
date: 2021/3/10
categories:
- LeetCode
tags:
- 数组
- 遍历
---

[题目链接](https://leetcode-cn.com/problems/1-bit-and-2-bit-characters/)

#### 扫描解法

##### 一路扫过去

如果是 0，则从下一位开始扫，如果是 1，则从下两位开始扫。

```java
// 第一种写法 ↓
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

// 第二种写法 ↓
class Solution {
    public boolean isOneBitCharacter(int[] bits) {
        int i = 0;
        while (i < bits.length - 1) {
            i += bits[i] + 1;
        }
        return i == bits.length - 1;
    }
}
```

- 时间复杂度：*O(n)*
- 空间复杂度：*O(1)*

##### 从尾巴往前扫

最后一位是否为一比特字符，只和他左侧出现的连续的 1 的个数（即它与倒数第二个 0 出现的位置之间的 1 的个数）有关，如果 1 的个数为偶数个，那么最后一位是一比特字符，如果 1 的个数为奇数个，那么最后一位不是一比特字符。

```java
class Solution {
    public boolean isOneBitCharacter(int[] bits) {
        int ones = 0;
        //Starting from one but last, as last one is always 0.
        for (int i = bits.length - 2; i >= 0 && bits[i] != 0 ; i--) { 
            ones++;
        }
        if (ones % 2 > 0) return false; 
        return true;
    }
}
```

- 时间复杂度：*O(n)*
- 空间复杂度：*O(1)*