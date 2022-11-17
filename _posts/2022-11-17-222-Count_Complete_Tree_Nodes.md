---
layout: post
title: 222-Count_Complete_Tree_Nodes
date: 2022-11-17
Author: keen
tags: [二叉树,完全二叉树]
toc: true
---
# 222-Count Complete Tree Nodes
## 题目：Medium
- 统计一个完全二叉树的节点数目
![Count_Complete_Tree_Nodes](https://lh3.googleusercontent.com/u/0/d/1ALpUhpNQtZ-C5FwMPOTlQTKse97qW87j)  

- 完全二叉树：长得跟满二叉树一个德行，按行编号完全一样  

- 

```cpp
    int countNodes(TreeNode* root) {

        if(!root) return 0;

        int hl=0, hr=0;

        TreeNode *l=root, *r=root;

        while(l) {hl++;l=l->left;}              //左右跑到底

        while(r) {hr++;r=r->right;}

        if(hl==hr) return pow(2,hl)-1;          //如果一层是满的，那么它上面应该是2的n次方-1  

        return 1+countNodes(root->left)+countNodes(root->right); //如果不是满的，就去找满的  

    }
```
- 重点！！！！！！！！！！！
- 时间复杂度分析他是个 log n 的平方 很神奇
