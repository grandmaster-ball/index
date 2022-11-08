---
layout: post
title: Add_Binary 67
date: 2022-11-07
Author: keen
tags: [Easy,二进制,模拟]
comments: false
toc: true
---
# 67-Add Binary
## 题目：Easy
- 用string 模拟两个二进制数字相加
![Add_Binary](https://lh3.googleusercontent.com/u/0/d/1yidUpX1OqUw7f-HTEcWeH9aO1D9_Pf0j)

- 本来是想写个模拟的加法器，但是实在是有够麻烦
- 思路1：先两个异或，然后找出C的string，给异或之后的加上去，发现不行
- 思路2：按末位来加法器，发现太麻烦了
- 思路3：其实因为C并不是个二进制，只要全加到C上去，最后再%2，然后c /=2就行了

```cpp
    string addBinary(string a, string b) {
       string ret = "";
       int lena = a.size()-1,lenb = b.size()-1,c = 0;
       while(lena>=0||lenb>=0||c==1){
           c += lena>=0 ? a[lena--] - '0' : 0;
           c += lenb>=0 ? b[lenb--] - '0' : 0;
           ret = char(c%2 + '0') + ret;
           c /= 2;
       } 
       return ret;
    }
```
