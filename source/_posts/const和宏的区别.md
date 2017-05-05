---
title: 宏和const的区别
date: 2016-11-02 21:20:47
tags:宏 const
---


1、编译的时刻不一样
2、




const的简单实用

const作用：
1.修饰右边基本变量或者指针变量 int a int *p
		  
2.被const修饰变量只读


int * const p;	 //p只读，*p可以改    

int const * p;	//*p只读， p可以改

const int *p; 	// *p只读，p变量

const int *const p; 	//都是只读

int const *const p;	//都是只读