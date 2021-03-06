---
layout:     post
title:      2019-11-05-LeetCode刷题总结
subtitle:   刷题笔记
date:       2019-11-05
author:     AndyCao
header-img: img/post-bg-ios9-web.jpg
catalog: true
tags:
    - leetcode
    - C program
---

>**leetcode** 刷题不是目的，只是想让自己更强大一点

# Longest Substring Without Repeating Characters

Given a string, find the length of the longest substring without repeating characters.

Example 1:

```
Input: "abcabcbb"
Output: 3 
Explanation: The answer is "abc", with the length of 3. 
```

Example 2:

```
Input: "bbbbb"
Output: 1
Explanation: The answer is "b", with the length of 1.
```

Example 3:

```
Input: "pwwkew"
Output: 3
Explanation: The answer is "wke", with the length of 3. 
             Note that the answer must be a substring, "pwke" is a subsequence and not a substring.
```    


solution1

```c

//12 ms	7M
int get_string_len(char * s)
{
    int len= 0;
    while (s[len] != '\0')
        ++len;
    
    return len;
}

int lengthOfLongestSubstring(char * s)
{
    
    int length = get_string_len(s);
    int head = 0;
    int tail = 0;
    int max_string = 0;
    
    for (int tail = 0; tail < length; tail++) {
        int i = head;
        while (i < tail) {
            if (s[i] == s[tail]) {
                head = i + 1;
            }
            i++;
        }
       
        if (max_string < (tail-head+1)) {
            max_string = tail-head+1;
        }
    }
    return max_string;

}

```
solution2
也可以采用暴力循环，KMP算法，看到有人通过hash map实现，后面添加两种解决方案，kmp,hash map实现，未完成



