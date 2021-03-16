---
categories:
  - MATLAB
tags:
  - figure plot
  - plot3
  - surf
  - label
---

* 这篇讲了如何对MATLAB绘制的数据图进行数值标注，思路就是读取坐标，用`text()`标注，
当然这里都是与原始数据无关的`后处理`，显然也可以用原始的绘图数据进行标注。
 * 只举了三维的例子，二维就简单模仿就好了。
* PS：text()的[参数说明](https://www.mathworks.com/help/releases/R2019b/matlab/ref/text.html)


## 线图：如plot绘制的图

```matlab
clear all;close all
%% 思路，读取坐标，用text()标注

%1=========================== 线图,Z值标注
% 随便绘制的一个图
t = 0:pi/10:pi;
xt(1,:) = sin(t).*cos(10*t);
yt(1,:) = sin(t).*sin(10*t);
zt = cos(t);
figure
h1=plot3(xt,yt,zt);
% 标注

strcell=num2cell(h1.ZData);
text(h1.XData,h1.YData,h1.ZData,strcell);
```

## 面图：如surf绘制的图

```matlab
%2============================= 面图,Z值标注
figure
h2=surf(magic(5));
XX=repmat(h2.XData,1,length(h2.YData));
YY=repmat(h2.YData,1,length(h2.XData));
    YY=reshape(YY',1,size(YY,1)*size(YY,2));
ZZ=reshape(h2.ZData,1,size(h2.ZData,1)*size(h2.ZData,2));
strcell=num2cell(ZZ);
text(XX,YY,ZZ,strcell);
```
## 运行结果
![plot3](https://7475-tututong-1302752799.tcb.qcloud.la/MD%E5%9B%BE%E5%BA%8A/Untitled_01.png?sign=f6d47547a865713ac5dfa34f4a8ca148&t=1596547938)
![surf](https://7475-tututong-1302752799.tcb.qcloud.la/MD%E5%9B%BE%E5%BA%8A/Untitled_02.png?sign=e154952ce4ded99705ff78e27d2bee40&t=1596547959)
