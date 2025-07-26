# 	妈了个逼

# 这辈子都别碰scanf()

# 这辈子都别碰scanf()

# 这辈子都别碰scanf()

## 重要事情说三遍,警示后人

printf，高！					//指效率

cin，硬！						//指异常安全

cout，菜！					//指私人效率和煞笔参数

scanf，又菜又废！	//煞笔参数强如大份，int类型输char可以原地爆炸的上古老飞舞

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

## 算法

### 排序

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



### 特点

- 有限性

- 确定性

- 可行性

- 输入输出 **可无输入**

### 时间复杂度

只在乎量级，不在乎细节

例：O(n^2^)

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

P1614

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



###　贪心算法

局部最优解推导出全局最优解

## 高精度数值运算

### 高精加法

~~~c++
//传统派
#include <bits/stdc++.h>
using namespace std;
#define max 500
char a[max]={0},b[max]={0};
int a1[max]={0},b1[max]={0},c1[max]={0};
int main(){ 
	scanf("%s",a);
	scanf("%s",b);
	long long la=strlen(a),lb=strlen(b);
	for(long long i=0;i<la;i++){
		a1[la-1-i]=a[i]-'0';	
	}
	for(long long i=0;i<lb;i++){
		b1[lb-1-i]=b[i]-'0';
	}
	long long lc=la>lb?la:lb,x=0;
	for(long long i=0;i<lc;i++){
		c1[i]=a1[i]+b1[i]+x;
		x=c1[i]/10;
		c1[i]=c1[i]%10;
	} 
	if(x!=0){
		c1[lc]=x;
		lc++;
	} 
	for(long long i=lc-1;i>=0;i--){
		printf("%d",c1[i]);
	}
	return 0;
}
~~~

### 高精减法

~~~c++
//维新派
#include <bits/stdc++.h>
using namespace std;
#define max 500
string a,b;
int a1[max]={0},b1[max]={0},c1[max]={0};
int main(){ 
	cin>>a;
	cin>>b;
	long long la=a.size(),lb=b.size();
	int flag;
	if(la<lb||la==lb&&a<b){
		flag=1;
		swap(la,lb);
		swap(a,b);
	}
	for(long long i=0;i<la;i++){
		a1[la-1-i]=a[i]-'0';	
	}
	for(long long i=0;i<lb;i++){
		b1[lb-1-i]=b[i]-'0';
	}
	long long lc=la;
	for(long long i=0;i<lc;i++){
		if(a1[i]>=b1[i]) 
			c1[i]=a1[i]-b1[i];
		else {
			a1[i+1]--;
			a1[i]+=10;
			c1[i]=a1[i]-b1[i];}
	}  
	long long k;
	for(k=la;k>0;k--){
		if(c1[k]!=0)break;
	}
	if(flag==1)printf("-");
	for(long long i=k;i>=0;i--){
		printf("%d",c1[i]);
	}
	return 0;
}
~~~

#### 高精乐高超级拼装

~~~c++
//器官移植派
#include <bits/stdc++.h>
using namespace std;
#define max 500
string a,b;
int q(string a){
	#define max 500
string b;
int a1[max]={0},b1[max]={0},c1[max]={0};
	cin>>b;
	long long la=a.size(),lb=b.size();
	for(long long i=0;i<la;i++){
		a1[la-1-i]=a[i]-'0';	
	}
	for(long long i=0;i<lb;i++){
		b1[lb-1-i]=b[i]-'0';
	}
	long long lc=la>lb?la:lb,x=0;
	for(long long i=0;i<lc;i++){
		c1[i]=a1[i]+b1[i]+x;
		x=c1[i]/10;
		c1[i]=c1[i]%10;
	} 
	if(x!=0){
		c1[lc]=x;
		lc++;
	} 
	for(long long i=lc-1;i>=0;i--){
		printf("%d",c1[i]);
	}

}
int a1[max]={0},b1[max]={0},c1[max]={0};
string w;
int main(){ 
	cin>>a;
	cin>>b;

	long long la=a.size(),lb=b.size();
	int flag;
	if(la<lb||la==lb&&a<b){
		flag=1;
		swap(la,lb);
		swap(a,b);
	}
	for(long long i=0;i<la;i++){
		a1[la-1-i]=a[i]-'0';	
	}
	for(long long i=0;i<lb;i++){
		b1[lb-1-i]=b[i]-'0';
	}
	long long lc=la;
	for(long long i=0;i<lc;i++){
		if(a1[i]>=b1[i]) 
			c1[i]=a1[i]-b1[i];
		else {
			a1[i+1]--;
			a1[i]+=10;
			c1[i]=a1[i]-b1[i];}
	}  
	long long k,t=0;
	for(k=la;k>0;k--){
		if(c1[k]!=0)break;
	}
	if(flag==1)printf("-");
	for(long long i=k;i>=0;i--){
		w[t]=c1[i];
		t++;
	}
	q(w);
	
	return 0;
}
~~~

### 高精乘法

~~~c++
//抽风派
#include <bits/stdc++.h>
#define max 500
char a[max]={0},b[max]={0};
int a1[max]={0},b1[max]={0},c1[5001]={0};
int main(){ 
	scanf("%s",a);
	scanf("%s",b);
	long long la=strlen(a),lb=strlen(b);
	for(long long i=0;i<la;i++){
		a1[la-1-i]=a[i]-'0';	
	}
	for(long long i=0;i<lb;i++){
		b1[lb-1-i]=b[i]-'0';
	}
	long long lc=la>lb?la:lb,x=0;
	for(long long i=0;i<lb;i++){
		for(long long j=0;j<la;j++){
		c1[j+i]=c1[j+i]+a1[j]*b1[i]+x;
		x=c1[j+i]/10;
		c1[j+i]=c1[j+i]%10;
	}
	c1[i+la]=x;
	x=0;
	} 
	
	for(long long i=lc;i>=0;i--){
		printf("%d",c1[i]);
	}
	return 0;
}
~~~



## 栈

~~~c++
#include <bits/stdc++.h>
using namespace std;
#define max 500

int a[max]={0},top=0;
void push(int v){
	if(top<max){
		top++;
		a[top]=v;
	}
}
void pop(int k){
	if(top>0){
		top--;
	}
}
int get_top(){
	return a[top];
}
void clr(){
	top=0;
}
int main(){ 
	
	return 0;
}
~~~

~~~c++
#include <bits/stdc++.h>
using namespace std;
#define max 500

char a[max]={0},top=0,input[max],q=0;
void push(int v){
	if(top<max){
		top++;
		a[top]=v;
	}
}
void pop(){
	if(top>0){
		top--;
	}
}
char get_top(){
	return a[top];
}
void clr(){
	top=0;
}
int main(){ 
int w=0;
string s;
cin>>s;
w=s.size();
	for(int i=0;i<w;i++){
		if(s[i]!='@'){
		if(s[i]=='(')
		push(s[i]);
		else if(get_top()=='(')pop();
		else {
			cout<<"NO";
			return 0;
		} }
	}
	if(top==0)cout<<"YES";
	else cout<<"NO";
	
	return 0;
}
~~~

## 链表

一部分用来存放数据节点，一部分用来存放指针

可使用结构体实现

串联

~~~c++
#include <bits/stdc++.h>
using namespace std;

int main(){ 
	struct node{
		int data;
		node *next;
	};
	int t=0;
	cin>>t;
	node a={1,NULL};
	node b={2,NULL};
	node c={3,NULL};
	node d={4,NULL};
	node e={5,NULL};
	a.next=&b;
	b.next=&c;
	c.next=&d;
	d.next=&e;
	node q={t,NULL};
	q.next=&c;
	b.next=&q;
	node *p;
	p=&a;
	while(p!=NULL){
		if(p->next->data==p){
		f.next=p->next;
		p->next=&f;
		break;}
		p=p->next;
		
	}
	//cout<<p->data;
	//	p=p->next ;
	return 0;
}
~~~

## 队列

~~~c++
#include <bits/stdc++.h>
using namespace std;
#define max 500

int que[6],front=0,rear=0;
void push(int n)
if(rear<6){
	que[rear++]=n;
	return;
}
void pop(){
	if(front!=rear)
		front++;
	return;
}
int size(){
	return rear-front;
}
int getfront(){
	return que[front];
}
int main(){ 
	int a[max]={1,2,3},b[10]={4,5,6},c[3]={7,8,9},top=0;
	
	return 0;
}
~~~

