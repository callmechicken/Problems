---
title: 1426. 数元素
date: 2021/3/28
categories:
- LeetCode
tags:
- 数组
- 哈希
---

[题目链接](https://leetcode-cn.com/problems/counting-elements/)

#### 哈希解法

##### 用数组做哈希

```java
class Solution {
    public int countElements(int[] arr) {
        int count = 0;
        int[] hashArr = new int[1001];
        for(int i : arr){
            hashArr[i]++;
        }
        for(int i = 0; i < 1000; i++){
            if (hashArr[i + 1] > 0 && hashArr[i] > 0) {
                count += hashArr[i];
            }
        }
        return count;
    }
}
```

- 时间复杂度：*O(n)*
- 空间复杂度：*O(n)*

##### 用HashMap做哈希

```java
class Solution {
    public int countElements(int[] arr) {
        int count = 0;
        HashMap<Integer, Integer> map = new HashMap<>();
        for(int num : arr){
            if (map.containsKey(num)) {
                map.put(num, map.get(num) + 1);
            } else {
                map.put(num, 1);
            }
        }
        for(int i : map.keySet()){
            if (map.containsKey(i + 1)) {
                count += map.get(i);
            }
        }
        return count;
    }
}
```

- 时间复杂度：*O(n)*
- 空间复杂度：*O(n)*