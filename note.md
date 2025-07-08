[TOC]
## Define
DEFINE type c=const char\*/char\*

DEFINE type i=int

DEFINE type s=string



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

