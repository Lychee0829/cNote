[TOC]
## Define
DEFINE type c=const char\*/char\*

DEFINE type i=int

DEFINE type s=string

DEFINE type d=double

## String/char* oprate
strlen(c1) //compute size(without\0)

strcpy(c1,c2) //copy

strcmp(c1,c2) //compare

strcat(c1,c2) //equal string oprater+

数组可能溢出

cin.getline(c1,i) //c1 output,i long

c风格

getline(cin,c1)

string风格

s1.length() //equal strlen

s1.size() //equal strlen

sizeof(c1) //with \0

strcmp(s1,s2) //return bool

s.find(c,i) //return ss or -1

参数i为查找开始下标

## Data format output

printf("%.3lf",d) //三位小数



## Function

int (int a){

statement;

return v;}

**EQAL**

void (int& a){

statement;

}

void(){return v;}

不会报错

声明需要原型例int (int a);

## Standard library function

swap(x,y) //交换函数,数据类型不指定**包括但不限于dic **

max(x,y)

min(x,y)

sort(begin,end) //左闭右开区间 **begin/end是对象地址且end不参与排序**

实例：sort(a,a+5,cmp) //升序

默认升序

**参数必须为地址,例：sort(a,a+i**)而并非sort(a,a[i])

sort第三个函数是函数名,不带实参

bool cmp(int a,int b){return a<b;}

## Struct

