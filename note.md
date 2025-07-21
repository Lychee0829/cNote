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

## 排序

冒泡排序次数：n(n-1)/2

示例

~~~c++
/*a pop-up sort simple example
see also:https://www.luogu.com.cn/problem/P1116 */
#include <bits/stdc++.h>
using namespace std;
const int maxn=10000; //max

int main(){ 
	int c[maxn],*p=c;
	//pointer is used to input data
	int n=0,cnt=0,cnti=0;//n:amount of data	
	cin>>n;              //cnt:range counter
	for(int i=0;i<n;i++){//cnti:sort counter
		cin>>*p++;
	}//get data
	while(cnt<n-1){
		for(int i=0;i<n-1-cnt;i++){ //pop-up
			if(c[i]>c[i+1]){
				swap(c[i],c[i+1]);
				cnti++; 
			}
		}
	cnt++;
	}//sort data
	cout<<cnti<<endl;
	return 0;
}
~~~

插入：先比较，后插入

选择不稳定，其余稳定

~~~c++
#include <bits/stdc++.h>
using namespace std;
int main(){
    long long m,n,cnt=0,cntg=0;
    cin>>m>>n;
    
    for(long long x=0;x<=m;x++){
        for(long long y=0;y<=n;y++){
            long long tmp=min(n-y,x)+min(n-y,m-x)+min(x,y)+min(y,m-x);
			cnt+=tmp;
			cntg+=n*m-tmp; 
        }
    }
    cout<<cnt/4<<' '<<cntg/4<<endl;
    return 0;
}

~~~


## 算法

### 特点

- 有限性

- 确定性

- 可行性

- 输入输出 **可无输入**

### 二分算法

每次将数据分成两份，通过不断缩小查找范围实现高效查询，时间复杂度为O(log n)

中间值=（最小值+最大值+1）/2

~~~c++
//核心
while(L<=R){
	mid=(L+R)>>2;
	if(mid==num){
		cout<<'1';
		break;
	}else if(mid>num){
		R=mid-1;
	}else L=mid++;
}
~~~

### 前缀和算法

前缀和计算L-R区间和

s[R]-s[L-1]

<mark>在下标为0时可用</mark>

例：

~~~c++
/* 	a simple example of Prefix Sum
	n:source
	db:Prefix Sum 
*/
#include <bits/stdc++.h>
using namespace std;
int n[10000],db[10000]={0};

int main(){ 	
	int a=0,b=0,c=0,k=0; 
	cin>>c;
	for(int k=1;k<=c;k++){
		cin>>n[k];
		db[k]=db[k-1]+n[k];
	}
	cin>>a>>b;
	cout<<db[b]-db[a]; 
	return 0;
}
~~~

### 时间复杂度

只在乎量级，不在乎细节

例：O(n^2^)

###　贪心算法

局部最优解推导出全局最优解

tmp:

~~~

#include <bits/stdc++.h>
using namespace std;

int main(){ 
	int q[3002],m,n,db[3002],s=0,t=1000;
	cin>>n>>m;
	for(int i=1;i<=n;i++){
		cin>>q[i];
		db[i]=db[i-1]+q[i];
	}
	for(int i=1;i<=n;i++)cout<<q[i]<<' ';
	cout<<endl;
	for(int i=m;i<=n;i++){
	s=db[i];
	if(s<t)t=s;
	}
	cout<<t<<endl;
	
	return 0;
}
~~~

怕1614
