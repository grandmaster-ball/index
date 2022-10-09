---
layout: post
title: 16-3Sum_Closest
date: 2022-10-09
Author: keen
tags: [暴力,two_pointers,medium]
toc: true
---
# 16-3Sum Closest
## 题目：Medium
- 从一串序列中，选择三个使之求和尽可能的接近目标值，返回求和结果

![3Sum_closest](https://lh3.googleusercontent.com/u/0/d/198TFQwiJIzV8peJJlfzqcwOPLjpWPXsC)

- 传统思路上来说很容易给出一个O(n^3)的结果
- 所以我们需要把它优化到n^2

```CPP
	int threeSumClosest(vector<int>& nums, int target) {
    	sort(nums.begin(),nums.end());                                  //先sort使之可以进行比较
        int sum = nums[0] + nums[1] + nums[2];
        int len = nums.size();
        for(int i=0;i<len-2;i++){
            int second = i+1;
            int third  = len-1;
            while(second<third){
                int cursum = nums[i] + nums[second] + nums[third];
                if(cursum == target) return target;
                if(abs(cursum-target)<abs(sum-target)) sum = cursum;    //谁更接近要谁
                cursum>target ? third-- : second++;                     //这一步很巧妙的降低了时间复杂度
            }
        }
        return sum;
    }
```

- 通过固定一个，让另外两个量向中间移动来有效的降低了时间复杂度

```cpp
int second = i+1;
int third  = len-1; 

cursum>target ? third-- : second++;	
```

