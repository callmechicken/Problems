---
title: 1002. 查找常用字符
date: 2021/4/1
categories:
- LeetCode
tags:
- 数组
- 哈希
---

[题目链接](https://leetcode-cn.com/problems/find-common-characters/)

#### 哈希解法

```java
class Solution {
    public List<String> commonChars(String[] A) {
        List<String> list = new ArrayList<>();
        int[] res = new int[26];
        for (char c : A[0].toCharArray()) {
            res[c - 'a']++;
        }
        for (int i = 1; i < A.length; i++) {
            int[] temp = new int[26];
            for (char c : A[i].toCharArray()) {
                temp[c - 'a']++;
            }
            for (int j = 0; j < 26; j++) {
                res[j] = Math.min(res[j], temp[j]);
            }
        }
        for (int i = 0; i < res.length; i++) {
            if (res[i] > 0) {
                for (int j = 0; j < res[i]; j++) {
                    list.add(((char) ('a' + i) + ""));
                }
            }
        }
        return list;
    }
}
```

- 时间复杂度：*O(n^2)*
- 空间复杂度：*O(1)*

