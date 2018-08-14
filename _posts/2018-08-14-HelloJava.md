---
layout:     post
title:      Hello Java!
subtitle:   Java小学期第一次作业记录
date:       2018-07-24
author:     WQW  
header-img: img/0399a990d815b14b258321a272584f73.jpg
catalog: true
tags:
    - Java
---


# Hello Java

第一次使用Java还有很多生疏的地方 仅作为记录。   </br>	
题目比较简单所以代码也比较`生猛`~  </br>
顺便练习一下m语法以及git </br>
git add 2018-08-14-HelloJava.md</br>
git commit -m "想说啥就说点啥吧"</br>
git push origin master


# 题目

- #一 ![](https://i.imgur.com/gKz4kja.png)

- #二 ![](https://i.imgur.com/ySach6R.png)

- #三 ![](https://i.imgur.com/ggSNah9.png)

- #四 ![](https://i.imgur.com/67LnWHl.png)

## 大整数加法

高精度加法，还记得数据结构第一次作业的第一题就是高精度乘法，
	
所以这题没什么难度,用来熟悉JAVA还好。
	
	
```
import java.util.Scanner;
public class Main 
{
	public static void main(String[] args)
	{
		Scanner scan = new Scanner (System.in);
		while(scan.hasNext())
		{
			String num1=new String() ;
			String num2=new String() ;
			num1=scan.next();// save num1 as String
			num2=scan.next();
			int len1=num1.length();
			int len2=num2.length();
			int [] n1=new int[5001];
			int [] n2=new int[5001];
			int [] ans=new int[5001];
			for(int i=0;i<len1;i++)//solve number1
			{
				char data=num1.charAt(i);
				if(data>='0'&&data<='9')
				{
					n1[len1-i-1]=(int)data-'0';
				}
			}
			for(int i=0;i<len2;i++)//solve number2
			{
				char data=num2.charAt(i);
				if(data>='0'&&data<='9')
				{
					n2[len2-i-1]=(int)data-'0';
				}
			}
			int maxlen=0;
			if(len1>len2)
				maxlen=len1;
			else
				maxlen=len2;
			int sign=0;
			for(int i=0;i<maxlen;i++)
			{
				if(sign==1)
				{
					int temp=n1[i]+n2[i]+1;
					if(temp>=10)
					{
						sign=1;
						temp=temp%10;
					}
					else
						sign=0;
					ans[i]=temp;
				}
				else
				{
					int temp=n1[i]+n2[i];
					if(temp>=10)
					{
						sign=1;
						temp=temp%10;
					}
					else
						sign=0;
					ans[i]=temp;
				}
			}
			if(sign==1)
			{
				maxlen=maxlen+1;
				ans[maxlen-1]=1;
			}
			for(int i=maxlen-1;i>=0;i--)
			{
				System.out.print(ans[i]);
			}
			System.out.print("\n");
		}
		scan.close();
	}
}
```
