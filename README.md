# 第一次作业
## 2.23
  nullptr可以转换成任意其他的指针类型。之后判断p是否指向合法对象，只要把p作为if语句的条件就可以了。如果p的值是nullptr，则条件为假；反之为真。
## 2.24
  void* 是一种特殊的指针类型，可以用于存放任意对象的地址，p是合法的；
  lp是不合法的，因为lp是一个长整型指针，而i只是一个普通整型数，二者的类型不匹配。
## 2.25
  (a)类型：ip是整型指针 值：整型数在内存中的地址；类型：i是一个整型数；类型：r是一个引用，绑定i 值：r==i；
  (b)类型：i是一个整型数；ip是一个整型指针； 值：ip的值为0
  (c)类型：ip是一个整型指针；ip2是一个整型数 值：所指整型数在内存中的地址；
## 2.35 
```C++
  #include<iostream>
  #include<typeinfo>
  int main(){
    const int i = 42;
    auto j = i;
    const auto &k = i;
    auto *p = &i;
    const auto j2 = i;
    const auto &k2 = i;
    std::cout<<typeid(i).name()<<std::endl;
    std::cout<<typeid(j).name()<<std::endl;
    std::cout<<typeid(k).name()<<std::endl;
    std::cout<<typeid(p).name()<<std::endl;
    std::cout<<typeid(j2).name()<<std::endl;
    std::cout<<typeid(k2).name()<<std::endl;
  return 0;
  }
  ```
## 3.4
```C++
  #include<iostream>
  #include<string>
  int main(){
    string s1,s2;
    std::cin>>s1>>s2;
    auto len1 s1.size();
    auto len2 s2.size();
    if (len1==len2)
      std::cout<<len1<<len2<<std::endl;
    else if(len1>len2)
      std::cout<<len1-len2<<std::endl;
    else
      stdcout<<len2-len1<<std::endl;
    return 0;
  }
```
## 3.5
```C++
  #include<iostream>
  #include<string>
  int main(){
    char cont = 'y';
    string s;
    string result;
    while(stdcin>>s){
      if(!result.size())
        result += s;
      else
        result = result+" "+s;
      std::cin>>cont;
      if(cont=='y'||cont=='Y')
        continue;
      else
        break;
    }
    return 0;
  }
```
## 3.20
```C++
#include<iostream>
#include<vector>
#include<stdafx.h>
using namespace;
int main()
{
	vector<int> vint;
	_int64 ival;
	cout << "请输入一组数字,以其他非数字字符结束：" << endl;
	while (cin >> ival)
		vint.push_back(ival);
	if (vint.size()==0)
	{
		cout << "没有一个元素" << endl;
		return -1;
	}
	cout << "相邻两项的和依次是：" << endl;
	//利用decltype推断i的类型
	for (decltype (vint.size()) i = 0; i < vint.size()-1; i+=2)
	{
		//求相邻两项的和
		cout << vint[i] + vint[i + 1] << " ";
		//每五行输出五个数字
		if ((i + 2) % 10 == 0 )
			cout << endl;
	}
	//如果元素是奇数个的话，单独处理最后一个元素
	if (vint.size()%2!=0)
		cout<<vint[vint.size()-1];
 
	return 0;
	
}
```
## 3.23
```
  #include <iostream>
#include <vector>
#include<cctype>
using namespace std;
int main()
{
	vector<int>ivec(10,1);//定义一个int类型的容器ivec
	int ival;
	cout<<"请输入10个整型数字！"<<endl;
	for(vector<int>::iterator iter = ivec.begin();iter<ivec.end();++iter)//使用迭代器访问vector中的元素
	{
	   cout<<(*iter)*2<<endl;
	}
	   if(ivec.size()==0)//如果容器为空，则输入No element! 并退出
	{
	   cout<<"No element!"<<endl;
	   return -1;
	}
	return 0;
}
```
