---
title: 13 - 罗马数字转整数
date: 2018-04-07 19:44:26
tags: 
- LeetCode
- Python
categories: LeetCode
---

## 题目描述
![problem](images/13.png)

<!-- more -->

## 罗马数字
我觉得这位兄台的和百科差不多，又比百科美观，就借过来用用嘻嘻。
![RomanNumber](images/RomanNumber.png)

## 整数转罗马数字
cr: [leetcode 罗马数字与整数的转换算法](https://blog.csdn.net/net_wolf_007/article/details/51770112)

idea: 用“放在大数左边的数字只能使用一个”的特点来判断对当前字母是加还是减。

```python
class Solution:
    def intToRoman(self, num):
        """
        :type num: int
        :rtype: str
        """
        if num <= 0:
            return ''

        ret = ''
        roman = ["M","CM", "D", "CD", "C", "XC", "L", "XL", "X", "IX", "V", "IV", "I"]
        arab = [1000, 900, 500, 400, 100,90, 50, 40, 10, 9, 5, 4, 1]

        for i in range(13):
            if num > 0:
                if num < arab[i]:
                    continue
                while num >= arab[i]:
                    num -= arab[i]
                    ret += roman[i]
        return ret
```