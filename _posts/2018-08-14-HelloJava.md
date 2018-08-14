---
layout:     post
title:      Hello Java!
subtitle:   Java小学期第一次作业记录
date:       2018-07-24
author:     WQW  
header-img:  img/zyr.jpg
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

## T1大整数加法

高精度加法，还记得数据结构第一次作业的第一题就是高精度乘法，
	
所以这题没什么难度,用来熟悉JAVA还好。
	
	
```ojbc
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
# T2挑选最小的质数
筛出质数&&排序也没什么可说的，这道题是最先开始写的一道，熟悉了JAVA的一些操作之后就很简单了。

```java
package hellotest;
import java.util.Scanner; 
import java.util.Arrays;
public class helloworld1 {
	  public static void main(String[] args) 
	  {
		      // TODO Auto-generated method stub
		  Scanner scan = new Scanner (System.in);
		  while(scan.hasNextInt())
		  {
			  int M=scan.nextInt();//M
			  int N=scan.nextInt();//N
			  int[] numbers=new int[M];
			  int[] primes=new int [N];
			  for (int i=0;i<M;i++)
			  {
				  numbers[i]=scan.nextInt();
				  // System.out.println(numbers[i]);
			  }
			  Arrays.sort(numbers);//SORT
			  int numberOfPrimes=0;
			  for(int i=0;i<M;i++)
			  {
				  if(NumberIsPrime(numbers[i]))
				  {
					  primes[numberOfPrimes++]=numbers[i];
				  }
			  }
			  if(primes[N-1]!=0)			  
				  System.out.println(primes[N-1]);    
			  else
				  System.out.println(-1);
		  	}
		  	scan.close();
	  }
	  private static boolean NumberIsPrime(int n)//judge the number is prime
	  {
		  if(n==1)
			  return false;
		  for(int i=2;i<n;i++)
		  {
			  if(n%i==0)
			  return false;				  
		  }
		  return true;
	  }
}
```
# T3矩阵相乘

我觉得这道是最简单的一个，不说了。
```
import java.util.Scanner;
public class Main
{
	public static void main(String[] args)
	{
		Scanner scan = new Scanner(System.in);
		int row1=scan.nextInt();
		int col1=scan.nextInt();
		int [][]matrix1=new int[row1][col1];
		for(int i=0;i<row1;i++)
		{
			for(int j=0;j<col1;j++)
			{
				matrix1[i][j]=scan.nextInt();
			}
		}
		int row2=scan.nextInt();
		int col2=scan.nextInt();
		int [][]matrix2=new int[row2][col2];
		for(int i=0;i<row2;i++)
		{
			for(int j=0;j<col2;j++)
			{
				matrix2[i][j]=scan.nextInt();
			}
		}
		scan.close();
		int [][]ans=new int[row1][col2];
		for(int i=0;i<row1;i++)
		{
			for(int j=0;j<col2;j++)
			{
				ans[i][j]=getAns(i,j,row1,col1,row2,col2,matrix1,matrix2);
				//System.out.println(ans[i][j]);
			}
		}
		for(int i=0;i<row1;i++)
		{
			for(int j=0;j<col2;j++)
			{
				System.out.print(ans[i][j]);
				if(i==row1-1&&j==col2-1) {}
				else
				System.out.print(" ");
			}
			System.out.print("\n");
		}
	}
	private static int getAns(int row,int col,int row1,int col1,int row2,int col2,int m1[][],int m2[][])
	{
		int data=0;
		for(int i=0;i<col1;i++)
		{
			data=m1[row][i]*m2[i][col]+data;
		}
		return data;
	}
}
```
# T4合法标识符
这道题首先要了解java的合法标识符是什么。 <br>
对开头符号的要求以及中间符号的要求，最后再检查一下是否和保留字冲突就ok。对于关键字……emmmmmm就直接`**暴力**`吧 代码就很暴力
```
import java.util.Arrays;
import java.util.Scanner;
public class Main
{
	public static void main(String[] args) 
	{
		Scanner scan=new Scanner(System.in);
		String data=new String();
		data=scan.next();
		scan.close();
		
		System.out.print(judge(data));

	}
	private static int judge(String temp)
	{
		String[] key= {"abstract","assert",	"boolean","break","byte",
	"case","catch","char","class","const","continue","default","do","double","else",
	"enum","extends"	,"final"	,"finally"	,"float",
	"for",	"goto","if","implements","import",
	"instanceof","int","interface","long","native",
	"new","package","private","protected","public",
	"return","strictfp","short","static","super",
	"switch","synchronized","this","throw","throws",
	"transient"	,"try"	,"void"	,"volatile"	,"while"};
		
		if(temp.length()==0||!Character.isJavaIdentifierStart(temp.charAt(0)))
		{
			return -1;
		}
		String tempTail=temp.substring(1);
		for(int i=0;i<tempTail.length();i++)
		{
			if(!Character.isJavaIdentifierPart(tempTail.charAt(i)))
			{
				return -1;
			}

		}
		boolean flag=Arrays.asList(key).contains(temp);
		if(flag==true)
			return -1;
		return 0;
	}
}
```

# what's more
` 首先感谢教授提供美艳封面照片 `

`刚刚教授吃饭的时候准备起诉我侵犯他的肖像权`

`emm教授最帅了封面是教授手拿体校通知书的稚嫩照`

写这篇主要是学习一下git以及记录一下昨天刚开始学的JAVA，git前面看过一些教程，今天才算正式git push，至于markdown，其实我现在都还不知道到底怎么换行！！！前面用了html的换行发现在markdownpad这里是ok的，但是在github上又崩了，溜了溜了踢球去了。