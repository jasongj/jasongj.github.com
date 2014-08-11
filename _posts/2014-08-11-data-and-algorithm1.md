---
layout: post
title: "排序算法之快速排序"
description: ""
category: 算法
tags: [快速排序]
---
{% include JB/setup %}





快速排序的思路：

	1.如果集合S中元素个数是0或1，返回
	2.在S集合中任意选取一个元素p，称为枢纽元素(pivot)
	3.将S集合中除p以外的元素分成两部分，小于p的为S1，大于p的为S2
	4.返回quicksort(s1),p,quicksort(s2)


快速排序它的平均运行时间O(NlogN),最坏的情况为 N2

	void Qsort(int A[],int left,int right)
	{
	   if (left>right-1) {
	       return;
	   }
	   int last=left;
	   for (int i=left+1; i<right; i++) {
	       if(A[left]>A[i]){
	           swap(A, i, ++last);
	       }
	   }
	   swap(A, left, last);
	   Qsort(A, left, last-1);
	   Qsort(A, last+1, right);
    
	}
