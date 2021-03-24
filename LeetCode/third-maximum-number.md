---
title: 414. 第三大的数
date: 2021/3/24
categories:
- LeetCode
tags:
- 数组
---

[题目链接](https://leetcode-cn.com/problems/third-maximum-number/)

#### 解法

##### TreeSet解法

```java
class Solution {
    public int thirdMax(int[] nums) {
        TreeSet<Integer> set = new TreeSet<>();
        for (Integer elem : nums) {
            set.add(elem);
            if (set.size() > 3) {
                set.remove(set.first());
            }
        }
        return set.size() < 3 ? set.last() : set.first();
    }
}
```

##### 三个变量扫描交换解法

```java
class Solution {
    private long MIN = Long.MIN_VALUE;

    public int thirdMax(int[] nums) {
        int n = nums.length;
        int first = nums[0];
        long second = MIN;
        long third = MIN;
        int now;
        for (int i = 1; i <  n; i++) {
            now = nums[i];
            if (now == first || now == second || now == third)
                continue;    // 如果重复，就跳过
            if (now > first) {
                third = second;
                second = first;
                first = now;
            } else if (now > second) {
                third = second;
                second = now;
            } else if (now > third) {
                third = now;
            }
        }
        if (third == MIN) return first;  // 没有第三大的元素，就返回最大值
        return (int)third;
    }
}
```

- 时间复杂度：*O(N)*
- 空间复杂度：*O(1)*