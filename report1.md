# Report 1 : Population Growth Problems
### Author: Cathaya Liu ,   [*WHU*](http://physics.whu.edu.cn/)

***

## 一、问题描述
Population growth problems often give rise to rate equations that are first-order. For example, the equation 

![](http://latex.codecogs.com/gif.latex?\frac{dN}{dt}=aN-bN^2)

might describe how the number of individuals in a population, N, varies with time. Here the first term aN corresponds to the brith of new members, while the second term-bN^2 corresponds to deaths. The death term is proportional to N^2 to allow for the fact that food will become harder to find when the population N become large. Begin by solving the equation with b=0 using the Euler method, and compare your numerical result result with the exact solution. Then solve the equation with nonzero values b . Give an intuitive explanation of you results. Interesting values of a and b depend on the initial population N . For small N(0) , a=10 and b=3 is a good choice, while for N(0)=1000 a good choice is a=10 and b=0.01 . 

## 二、问题分析
我们将分四个部分讨论这个问题。
* 求出该常微分方程在b=0情况下的解析解。
* 用Euler法求出该常微分方程在b=0情况下的数值解，并与其解析解进行比较。
* 用Euler法求出该常微分方程在b≠0情况下的数值解，尝试多个b的值并展示结果。
* 定性地解释结果。

## 三、算法设计及其Python实现
### I、程序分析
我们需要四个变量来描述这个数学模型，它们分别是：时间 t ，时间间隔（步长） Delta t ，当前人口数 N(t) 和初始人口数 N(0) 。

* 首先我们建立两个长度相同的独立一维数组，分别用来存放时间 t 和当前人口数 N(t) ，其元素一一对应。

* 对于时间 t 的数组，令其 t(0)=0 , t(n)=n\Delta t 。

* 对于人口数 N(t) 的数组，令其 N(0) 为初始人口数， N(t)= N(t-1)±f(N(t-1))\Delta t ，其中 f 取决于题目本身的变化。

* 循环生成时间 t 和当前人口数 N(t) 的数组元素。
* 画出 t-N 图。
### II、算法的Python实现
```
#引入matplotlib库

import matplotlib.pyplot as plt

#定义相关变量

N=[0 for x in range(0,'需要的长度')]
t=[0 for x in range(0,'需要的长度')]
N[0]='初始人口'
T='时间间隔'
t[0]=0

for i in range(1,'需要的长度'):
    N[i]=N[i-1]+f(N[i-1])*T
    t[i]=i*T

#绘图的相关设置

plt.title('')
plt.xlabel('t')
plt.ylabel('n')
P1=plt.plot(t,N)
plt.legend(handles = [P1], labels = [], loc = 'best')
plt.show()
```
## 四、程序的运行结果