---
layout: post
title: 653-Two Sum IV - Input is a BST
date: 2022-10-09
Author: keen
tags: [暴力,二叉树,Easy]
toc: true
---
挺简单的，待补完所有的Two Sum

# 653-Two Sum IV - Input is a BST

## 题目：Easy
- 一棵树，询问是否存在两个节点的加和等于目标值

![Two Sum IV](https://lh3.googleusercontent.com/u/0/d/1J2bC1PHc4tOdsMiZpqin1GYcGufTX_tW)

- set的使用

```CPP
	unordered_set<int> m;
    bool findTarget(TreeNode* root, int k) {
        if(!root) return false;
        if(m.count(k-root->val)) return true;                      //找到的话
        m.insert(root->val);
        return findTarget(root->left,k)||findTarget(root->right,k);
    }
```

- set是一个基于红黑树的自动排序的一元列表，默认从大到小排列，每次只能有一个
- set内部不允许重复但是插入重复值并不是个错误，而是会被insert忽略掉
- m.count()返回这个东西出现的次数
