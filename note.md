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

sort函数：排序需指定对象

bool cmp(stu a,stu b){return a.tl<b.tl;}   sort(tp,tp+n,cmp);

简单示例
~~~c++
/*a simple example of struct
explain:
tp: people<60
l:people>60
*/
#include <bits/stdc++.h>
using namespace std;
struct stu{
	string name;
	int y;
	int m;
};
bool cmp(stu a,stu b){
	if(a.y!=b.y)
return a.y>b.y;
else return a.y<b.y;}
//compare data if eqal return the earlier one
int main(){ 
	stu tp[100],l[100];
	int n=0,li=0;
	cin>>n;//input amount of data
	for(int i=0;i<n;i++){
		cin>>tp[i].name>>tp[i].y;
		// data input
		if(tp[i].y>=60){
			l[li]=tp[i];
			tp[i].m=0;
			li++;
		}
	}
	sort(l,l+li,cmp);
	

	for(int i=0;i<li;i++){ 
		cout<<l[i].name<<endl;
}
	for(int i=0;i<n;i++){ 
	if(tp[i].m!=0)
		cout<<tp[i].name<<endl;
}
//output format data
	return 0;
}
~~~

user:

5
q 12
p 23
w 66
k 66
b 67

output:

b
w
k
q
p