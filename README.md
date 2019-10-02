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

  '''#include<iostream>
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
  }'''
 
