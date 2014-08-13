---
layout: post
title: "排序算法之快速排序"
description: ""
category: 算法
tags: [快速排序]
---
{% include JB/setup %}





快速排序的思路：

1. 如果集合S中元素个数是0或1，返回
2. 在S集合中任意选取一个元素p，称为枢纽元素(pivot)
3. 将S集合中除p以外的元素分成两部分，小于p的为S1，大于p的为S2
4. 返回quicksort(s1),p,quicksort(s2)


快速排序它的平均运行时间O(NlogN),最坏的情况为 N2

---
第一种实现方式

1. 取第一个数为pivot＝A[left]。
2. 设置last标记位，每次遇到小于pivot的数都移动到++last标记位，同时last标记位加1，所以要每次循环完成之后，last标记位之前的数都小于pivot，last标记位之后的数都大于pivot
3. 将pivot移动到last位置。
4. 递归处理last左右两边的数组。

实现如下

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
	
---	
	
第二种实现方式	
	
	int partion(int A[], int low, int high)
	{
    int pivot =A[low];
    while (low<high) {
        while (low<high && pivot <= A[high]) {
            high--;
        }
        A[low] =A[high];
        while (low < high && pivot >=A[low]) {
            low++;
        }
        A[high] =A[low];
        
    }
    A[low]=pivot;
    return low;
	}

	void Qsort(int A[],int left,int right)
	{
	    if (left<right) {
	        int mid =partion(A, left, right);
	        Qsort(A, left, mid-1);
	        Qsort(A, mid+1, right);
	    }
	}
