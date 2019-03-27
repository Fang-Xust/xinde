# xinde

//typedef int INT;                      //typedef是类型重定义
//typedef unsigned int UINT;            //加上typedef，会由变量提升为这种类型
//typedef int Arr[10];
//typedef int(*PFUN)[10];               //指向数组的指针-->数组指针-->
//typedef int(*Pfun)(int,int);           //函数指针-->
//
//         面试问题：         typedef   define   const  的区别是什么？？


//	char password[20] = {'0'};     //0  '0'  '\0'   NULL
//0     数字0
//'0'    ASCII码     数字48的ASCII码
//'\0'    字符数组的结束标志，也是0 
//NULL     0地址 空地址
//int *p野指针  面试问题：预防野指针的方法是什么？
//int *p=NULL;  //  0地址   空地址   预留区
//*p=100;       //错误，它现在是空的，不能赋值

//栈  stack  的增长方式是从高地址向低地址去增长
//堆  heap   的增长方式是从低地址向高地址增长



//快捷键   "Ctrl+C"    终止程序

while ((ch=getchar())!=EOF)    //end of file-->  代表"Ctrl+Z"


//getchar()的返回值为什么是int？

getchar有一个int型的返回值.当程序调用getchar时.程序就等着用户按键.
用户输入的字符被存放在键盘缓冲区中.直到用户按回车为止(回车字符也放在缓冲区中).
getchar函数的返回值是用户输入的第一个字符的ASCII码,如出错返回-1,
且将用户输入的字符回显到屏幕.如用户在按回车之前输入了不止一个字符,
其他字符会保留在键盘缓存区中,等待后续getchar调用读取.
也就是说,后续的getchar调用不会等待用户按键,而直接读取缓冲区中的字符,
直到缓冲区中的字符读完为后,才等待用户按键.
getch与getchar基本功能相同,差别是getch直接从键盘获取键值,
不等待用户按回车,只要用户按一个键,getch就立刻返回,
getch返回值是用户输入的ASCII码,出错返回-1.输入的字符不会回显在屏幕上.
getch函数常用于程序调试中,在调试时,在关键位置显示有关的结果以待查看,
然后用getch函数暂停程序运行,当按任意键后程序继续运行.
简单的说,getch()是读取按键值常放在程序末尾起暂停作用
而getchar()是从标准输入设备读取下一个字符~~所读字符若文件结束或出错则返回-1



//看《C陷阱与缺陷》  《高质量C++C编程》
//看《程序员的自我修养》第一章  第二章  第三章  第六章  第十章



二分法查找算法：
#define _CRT_SECURE_NO_WARNINGS 1
#include<stdio.h>
#include<stdlib.h>

int BinarySearch(int arr[],int k,int left,int right)
{
	//int mid=left+(right-left)/2;            //这一行必须放在循环里面，否则while()就成死循环了
	while (left <= right)
	{
		int mid = left + (right - left) / 2;
		if (arr[mid] > k)
		{
			right = mid - 1;
		}
		else if (arr[mid] < k)
		{
			left = mid + 1;
		}
		else
		{ 
			//printf("找到了，下标是：%d\n", mid);
			return mid;
		}
	}
	return -1;
}

int main()
{
	int ret;
	int arr[10] = {1,2,3,4,5,6,7,8,9,10};
	int left = 0;
	int right = sizeof(arr) / sizeof(arr[0]) - 1;
	ret=BinarySearch(arr,7,left,right);
	if (-1 == ret)
	{
		printf("找不到\n");
	}
	else
	{
		printf("找到了，下标是：%d\n", ret);
	}
	system("pause"); 
	return 0;
} 


二分法递归查询：
