---
categories:
  - MATLAB
tags:
  - c++
  - coder
  - code conversion
---
利用**MATLAB coder**将`.m`文件转`.cpp`的方法

首先看一下要转换的代码(一个`function`文件)，非常简单，只是用于测试，实际使用不会这么简单，因为还会涉及到：`代码的优化`，以及`变量类型声明`，`变量的维度动态变化`等问题，这些都C++和MATLAB严重冲突的地方。

```matlab
function sum = myadd(x,y)
sum = x+y;
```


# 1. 安装编译器
```matlab
>> mex -setup
MEX 配置为使用 'MinGW64 Compiler (C)' 以进行 C 语言编译。

要选择不同的语言，请从以下选项中选择一种命令:
 mex -setup C++ 
 mex -setup FORTRAN
```
如果已经安装好可以跳过，如果没有安装好matlab会弹出安装下载链接，根据提示点击链接即可！

# 2. 安装matlab coder app
点击右上角`附件功能`输入coder下载安装（听说破解版MATLAB似乎无法安装，试一下吧）

![](https://7475-tututong-1302752799.tcb.qcloud.la/MD%E5%9B%BE%E5%BA%8A/coder/a1.png?sign=bf11aadf99cc72d599311354337d80ba&t=1596757848)
![](https://7475-tututong-1302752799.tcb.qcloud.la/MD%E5%9B%BE%E5%BA%8A/coder/a2.png?sign=ab73abeb241c1fdff054fe15157ddabe&t=1596757859)

# 3. 启动matlab coder app
```matlab
>> coder
```
# 4. 添加函数开始转换
>在此之前，为了不必要的麻烦，请大家将当前文件夹改为所要转换函数所在的文件夹。

## 4.1 添加函数
![](https://7475-tututong-1302752799.tcb.qcloud.la/MD%E5%9B%BE%E5%BA%8A/coder/c1.png?sign=bd8dc6666ea0be2b1737df18bc7f23ff&t=1596757870)
重点：要添加function而不是脚本！
## 4.2 声明变量类型
![](https://7475-tututong-1302752799.tcb.qcloud.la/MD%E5%9B%BE%E5%BA%8A/coder/c2.png?sign=d488a0489dbad435274758b8e5e5c8c4&t=1596757882)
用命令在命令行声明或者手动选择
## 4.3 转换测试
![](https://7475-tututong-1302752799.tcb.qcloud.la/MD%E5%9B%BE%E5%BA%8A/coder/c3.png?sign=2aafc431af34ae7ac26f4a21bfa79598&t=1596757892)
![](https://7475-tututong-1302752799.tcb.qcloud.la/MD%E5%9B%BE%E5%BA%8A/coder/c4.png?sign=8b967e178d7175dec05ab0013dd4431b&t=1596757902)
如果有错误，根据对应的错误进行修改
## 4.4 设置一些东西
![](https://7475-tututong-1302752799.tcb.qcloud.la/MD%E5%9B%BE%E5%BA%8A/coder/c5.png?sign=7c8753ada49acb6877e077e2aaeac13b&t=1596757943)
如果不懂，就按默认就好了，选一下要转换的类型
## 4.5 查看文件和报告
![](https://7475-tututong-1302752799.tcb.qcloud.la/MD%E5%9B%BE%E5%BA%8A/coder/c6.png?sign=929d56874027a6b8fd864e4eab3342f6&t=1596757953)
![](https://7475-tututong-1302752799.tcb.qcloud.la/MD%E5%9B%BE%E5%BA%8A/coder/c7.png?sign=c505d2bad1ca4ec6083ee8271cde25c5&t=1596757971)
重点关注`同名.cpp`和`同名.h`;main.cpp、main.h是测试文件，可以忽略，也可以看一下，是官方给的一个调用生成函数的例子，不会参与最终的代码！其他的文件按照需要进行选择，我这里只保留了同名.cpp和同名.h。

# 5. 在c++编译器中进行测试
![](https://7475-tututong-1302752799.tcb.qcloud.la/MD%E5%9B%BE%E5%BA%8A/coder/d1.png?sign=867534127637bb769905c643291fa7b6&t=1596757981)
我用的是VS2013，这不是MATLAB的重点，需要大家了解C++的代码，我仅仅给出改造的测试文件(我的B站视频有这部分的`录屏`)：
```c++
//这是头文件.h

/*
 * Academic License - for use in teaching, academic research, and meeting
 * course requirements at degree granting institutions only.  Not for
 * government, commercial, or other organizational use.
 *
 * myadd.h
 *
 * Code generation for function 'myadd'
 *
 */

#ifndef MYADD_H
#define MYADD_H

/* Include files */
#include <cstddef>
#include <cstdlib>

/* Function Declarations */
extern double myadd(double a, double b);

#endif

/* End of code generation (myadd.h) */
```
```c++
//这是源文件.cpp
#include "iostream"
#include "myadd.h"
using namespace std;

int main(void)
{
	double result;
	double x = 1;
	double y = 2;
	result = myadd(x,y);
	cout<<result<<endl;
	cout << "按任意键继续……";

	cin.clear();//清空缓存区
	cin.sync();
	cin.get();
	/* 这是出现“无法查找或打开 PDB 文件”的解决方案，
	目前本机还没有更好的方法，但是大家不一定会出现这个问题
	以上四行可以换成，system("pause");但是不推荐
	*/
}

/* Function Definitions */
double myadd(double a, double b)
{
  return a + b;
}

/* End of code generation (myadd.cpp) */
```

最后，文字稿写的相对概括，如果不明白可以看我的B站视频（主页找找）。
