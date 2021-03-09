---
title: 338. 比特位计数
date: 2021/3/9
categories:
- LeetCode
tags:
- 数组
- 数学
---

[题目链接](https://leetcode-cn.com/problems/counting-bits/)

#### 偷鸡解法

```java
class Solution {
    public int[] countBits(int num) {
        int[] result = new int[num + 1];
        for (int i = num; i > 0; i--) {
            result[i] = Integer.bitCount(i);
        }
        return result;
    }
}
```

- 时间复杂度：*O(N)*
- 空间复杂度：*O(N)*

#### 数学解法

奇数的二进制一定比前面那个偶数的二进制多一个最低位的 1。

偶数的二进制的 1 的个数一定和除以 2 之后的那个数一样多。除以 2 就是右移一位，抹掉一个 0 而已，1 的个数是不变的。

```java
/*
1 : 00000001
2 : 00000010
3 : 00000011
4 : 00000100
5 : 00000101
6 : 00000110
7 : 00000111
8 : 00001000
9 : 00001001
*/

class Solution {
    public int[] countBits(int num) {
        int[] result = new int[num + 1];
        for(int i = 1; i <= num; i++) {
            if(i % 2 == 1)
                result[i] = result[i - 1] + 1;
            else
                result[i] = result[i / 2];
        }
        return result;
    }
}
```

- 时间复杂度：*O(N)*
- 空间复杂度：*O(N)*