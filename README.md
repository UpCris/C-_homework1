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
## 6.10
```
#include<iostream>
#include<cstdlib>
using namespace std;
void exchange(int *p, int *q)
{
    int *k =0;
    k = p;
    p = q;
    q = k;
}
int main()
{
    int n = 0, i = 42;
    int *p = &n;
    int *q = &i;
    exchange(p, q);
    cout << *p << endl << *q<<endl;
    return 0;
}
```
## 6.19
  (a)是不合法的，函数的声明只包含一个参数，而函数的调用提供了两个参数，因此无法编译通过。

  (b)是合法的。字面值常量可以作为常量引用形参的值，字符'a'作为char类型形参的值也是可以的。

  (c)是合法的。66虽然是int类型，但是在调用函数时自动转换为double类型。

  (d)是合法的，vec.begin()和vec.end()类型都是形参所需的vector<int>::iterator，第三个实参3.8可以自动转换为形参所需的int类型。

## 6.39
  (a)第二条是计算两个常量整型的数。

  不合法，第二条无法和第一条进行区分。
	
  (b)获得double类型的get()

  不合法，不能使用不同的返回值类型对函数进行重载。

  (c)重置一个double类型的数。

  合法。

## 7.16
类的定义中对于访问说明符出现的位置和次数没有限定。在类中应当将接口定义在public说明符之后，而将成员变量定义在private说明符之后。

## 7.27
```C++
#include <iostream>
#include <string>

class Screen {
public:
    using pos = std::string::size_type;
    Screen() = default;
    Screen(pos ht, pos wd, char c) :
        height(ht), width(wd), contents(ht * wd, c) { }
    char get() const { return contents[cursor]; }
    inline char get(pos ht, pos wd) const;
    inline Screen& set(char ch);
    inline Screen& set(pos h, pos w, char ch);
    Screen& move(pos r, pos c);
    Screen& display(std::ostream& os);
    const Screen& display(std::ostream& os) const;
private:
    pos cursor = 0;
    pos height = 0;
    pos width = 0;
    std::string contents;
    void display_kernel(std::ostream& os) const;
};

Screen& Screen::display(std::ostream& os)
{
    display_kernel(os);
    return *this;
}

const Screen& Screen::display(std::ostream& os) const
{
    display_kernel(os);
    return *this;
}

void Screen::display_kernel(std::ostream& os) const
{
    os << contents;
}

inline Screen& Screen::move(pos r, pos c)
{
    pos row = r * width;
    cursor = row + c;
    return *this;
}

char Screen::get(pos r, pos c) const
{
    pos row = r * width;
    return contents[row + c];
}

inline Screen& Screen::set(char ch)
{
    contents[cursor] = ch;
    return *this;
}

inline Screen& Screen::set(pos r, pos c, char ch)
{
    contents[r * width + c] = ch;
    return *this;
}

int main(int argc, char const *argv[])
{
    Screen myScreen(5, 5, 'X');
    myScreen.move(4, 0).set('#').display(std::cout);
    std::cout << std::endl;
    myScreen.display(std::cout);
    std::cout << std::endl;
    return 0;
}
```

## 7.49
```C++
Sales_data& combine(Sales_data rhs); // 将s的值赋给形参rhs
Sales_data& combine(Sales_data& rhs); // 直接将s赋给rhs，也就是传引用
Sales_data& combine(const Sales_data& rhs) const; // 错误，this指针将会变成底层const，无法修改this指向的的内容
```

## 7.58
static double rate = 6.5;

类的静态成员变量需要在类外初始化。

double Example::rate=6.5;

声明只是表明了变量的数据类型和属性，定义则是需要分配内存。

static声明的类静态数据成员，其实体远在main()函数开始之前就已经在全局数据段中诞生了，这时候类对象的生命期还没开始。

static const int vecSize = 20;//因为是const 程序就不再试图去初始化它
