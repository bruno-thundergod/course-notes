### 计算机运算方法

1. 无符号数与有符号数
2. 数的定点表示和浮点表示
3. 定点运算
4. 浮点四则运算
5. 算术逻辑单元

主要内容

1. 计算机中数的表示
2. 计算机的运算方法
3. 计算器的设计

------

### 1.无符号数和有符号数

==无符号数（没有正负号的数）==

​	寄存器的位数反映了无符号数的表示范围

<img src="https://s1.ax1x.com/2020/06/13/tv00o9.png" alt="tv00o9.png" style="zoom:50%;" />

==有符号数（有正负号的数）==

​	以一种约定的形式保存小数点的位置

<img src="https://s1.ax1x.com/2020/06/13/tvBkmF.png" alt="tvBkmF.png" style="zoom:50%;" />

#### **原码表示法**

**整数**

如 x = +1110 [x]~原~ = 0，1110        用==逗号==将符号位和数值部分分隔开

​	 x = -1110  [x]~原~ = 1，1110

**小数**

x = +0.1101       [x]~原~=0.1101       用==小数点==将符号位和数值部分隔开

x = -0.1101        [x]~原~=1.1101  

x = +0.100000   [x]~原~=0.100000

x = - 0.100000   [x]~原~=1.100000  

**小结**

整数形式和小数形式的原码表示不同在于是否用逗号或者小数点隔开

<img src="https://s1.ax1x.com/2020/08/29/d7zq3Q.png" alt="d7zq3Q.png" style="zoom:50%;" />

<img src="https://s1.ax1x.com/2020/08/29/dHS94U.png" alt="dHS94U.png" style="zoom:50%;" />

原码表示法也会有问题，如下

<img src="https://s1.ax1x.com/2020/08/29/dHSnUK.png" alt="dHSnUK.png" style="zoom:50%;" />

能不能只做加法？

找到一个与负数等价的整数，来代替这个负数

就可以使==减法→加法==

#### 补码表示法

一个负数加上==“模”==即得该负数的补数

一个正数和一个负数互为补数时，他们绝对值之和即为==模==数

正数的补数即为其本身

**整数**

x = +1010		 [x]~补~=0,1010	用逗号将符号位与数值部分隔开

x = -1011000	[x]~补~=~[x]+1=0100111+1=1,0101000

**小数**

x = -0.1100000	[x]~补~ = 1.0100000

**举例**

[x]~补~=0.0001	x = +0.0001

[x]~补~=1.0001	x = - 0.1111

[x]~补~=1,1110	x = - 0010 (取反+1)

#### 补码和原码练习

求下列真值的补码

x = -70 =  -1000110		   1,0111010

| 真值               | [x]~补~   | [x]~原~   |
| ------------------ | --------- | --------- |
| x= +70 = 1000110   | 0,1000110 | 0,1000110 |
| x = -70 = -1000110 | 1,0111010 | 1,1000110 |
| 0.1110             | 0.1110    | 0.1110    |
| -0.1110            | 1.0010    | 1.1110    |
| 0.0000             | 0.0000    | 0.0000    |
| -0.0000            | 0.0000    | 1.0000    |
| -1.0000            | 1.0000    | 不能表示  |

#### 反码

x = +0.1101  [x]~反~=0.1101 用小数点将符号位与数值位隔开

x = -0.1010   [x]~反~=1.0101

**举例**

[x]~反~ = 0.1110   x = +1110

[x]~反~=1,1110     x= -0001

0的反码，设x = +0.0000   [+0.0000]~反~=0.0000

​					  x = -0.0000   [-0.0000]~反~=1.1111

==三种机器数的小结（原补反）==

- 最高位为符号位，书写用“，”（整数）或“.”（小数）将数值部分和符号位隔开

- 对于正数，原码 = 补码=反码

- 对于负数，符号位为1，其数值部分

  原码==除符号位外==每位取反末位加1→补码

  原码==除符号位外==每位取反→反码

**移码表示法**

补码表示很难直接判断其真值大小

<img src="https://s1.ax1x.com/2020/09/01/dxSIij.png" alt="dxSIij.png" style="zoom:50%;" />

<img src="https://s1.ax1x.com/2020/09/01/dxCBoF.png" alt="dxCBoF.png" style="zoom:50%;" />

<img src="https://s1.ax1x.com/2020/09/01/dxPmY4.png" alt="dxPmY4.png" style="zoom:50%;" />



### 2.数的定点表示和浮点表示

#### 定点表示

小数点按约定方式标出

#### 浮点表示

为什么引入浮点数表示？

1. 编程困难，程序员要调节小数点的位置
2. 数的表示范围很小，为表示两个相差很大的数据，需要很长的机器字长
3. 数据存储单元的利用率往往很低

<img src="https://s1.ax1x.com/2020/09/03/w9jmJH.png" alt="w9jmJH.png" style="zoom:50%;" />

**浮点数的表示形式**

<img src="https://s1.ax1x.com/2020/09/03/w9jYFg.png" alt="w9jYFg.png" style="zoom:50%;" />

<img src="https://s1.ax1x.com/2020/09/03/w9vHbV.png" alt="w9vHbV.png" style="zoom:50%;" />

为什么是4，15的二进制是1111

**浮点数的规格化形式**

r = 2	尾数最高位为1

r = 4	尾数最高2位不全为0	==基数不同，浮点数的规格化形式不同==

r = 8	尾数最高3位不全为0

**浮点数的规格化**

提高浮点数的表示精度

<img src="https://s1.ax1x.com/2020/09/03/w9xIiD.png" alt="w9xIiD.png" style="zoom:50%;" />

<img src="https://s1.ax1x.com/2020/09/03/wCSS76.png" alt="wCSS76.png" style="zoom:50%;" />

<img src="https://s1.ax1x.com/2020/09/03/wCSLUf.png" alt="wCSLUf.png" style="zoom:50%;" />

<img src="https://s1.ax1x.com/2020/09/04/wk3ZZ9.png" alt="wk3ZZ9.png" style="zoom:50%;" />



### 3.定点运算

1. 移位运算
2. 加减法运算
3. 乘法运算
4. 除法运算

**1.移位运算**

移位的意义：15.m = 1500.cm

机器用语：15相对于小数点左移2位（==小数点不动==）

左移	绝对值扩大

右移	绝对值缩小

在计算机中，移位与加减配合，能够实现乘除运算

**算术移位规则**

符号位不能变

<img src="https://s1.ax1x.com/2020/09/04/wkN3sf.png" alt="wkN3sf.png" style="zoom:50%;" />

<img src="https://s1.ax1x.com/2020/09/04/wkUbuV.png" alt="wkUbuV.png" style="zoom:50%;" />

<img src="https://s1.ax1x.com/2020/09/05/wVYfJJ.png" alt="wVYfJJ.png" style="zoom:50%;" />

#### 2.加减法运算

**加法**

整数：[A]~补~+[B]~补~=[A+B]~补~（mod2^n+1^）

小数：[A]~补~+[B]~补~=[A+B]~补~（mod2）

**减法**

A-B = A+(-B)

整数 [A-B]~补~=[A+(-B)]~补~=[A]~补~+[-B]~补~(mod 2^n+1^)

小数 [A-B]~补~=[A+(-B)]~补~=[A]~补~+[-B]~补~(mod 2)

==连同符号位一起相加，符号位产生的进位自然丢掉==

<img src="https://s1.ax1x.com/2020/09/05/wVdNCD.png" alt="wVdNCD.png" style="zoom:50%;" />

<img src="https://s1.ax1x.com/2020/09/05/wVBkDA.png" alt="wVBkDA.png" style="zoom:50%;" />

<img src="https://s1.ax1x.com/2020/09/05/wVBNCT.png" alt="wVBNCT.png" style="zoom:50%;" />

#### 3.乘法运算

**分析笔算乘法**

<img src="https://s1.ax1x.com/2020/09/09/w3NXC9.png" alt="w3NXC9.png" style="zoom:50%;" />

<img src="https://s1.ax1x.com/2020/09/09/w3UZvt.png" alt="w3UZvt.png" style="zoom:50%;" />

#### 4.除法运算

<img src="https://s1.ax1x.com/2020/09/09/w3r8TP.png" alt="w3r8TP.png" style="zoom:50%;" />

商的部分单独处理

数值部分为==绝对值==相除==x^*^/y^*^==

小数点定点除法==x^*^/y^*^==，整数定点除法==x^*^/y^*^==

被除数不等于0

除数不能为0

**1.恢复余数法**

y=0.1101 -y=1.1101  [-y]~补~=1.0010+1=1.0011

<img src="https://s1.ax1x.com/2020/09/09/w8tQBT.png" alt="w8tQBT.png" style="zoom:50%;" />

<img src="https://s1.ax1x.com/2020/09/09/w8thb8.png" alt="w8thb8.png" style="zoom:50%;" />

**2.不恢复余数法（加减交替法）**

<img src="C:\Users\10119\AppData\Roaming\Typora\typora-user-images\image-20200909222547735.png" alt="image-20200909222547735" style="zoom:50%;" />

<img src="C:\Users\10119\AppData\Roaming\Typora\typora-user-images\image-20200910113001709.png" alt="image-20200910113001709" style="zoom:50%;" />



#### 4.浮点运算

<img src="https://s1.ax1x.com/2020/09/10/wJMmjS.png" alt="wJMmjS.png" style="zoom:50%;" />

<img src="https://s1.ax1x.com/2020/09/10/wJQwM8.png" alt="wJQwM8.png" style="zoom:50%;" />

<img src="https://s1.ax1x.com/2020/09/10/wJlMYn.png" alt="wJlMYn.png" style="zoom:50%;" />

在S=-1/2和S = -1时，他们俩的补码不是规格化形式

<img src="https://s1.ax1x.com/2020/09/10/wJ1hE4.png" alt="wJ1hE4.png" style="zoom:50%;" />

知道了什么不是规格化，下面介绍如何规格化

注意，x+y原先是补码形式，后面减一，再取反

<img src="https://s1.ax1x.com/2020/09/10/wJ3gJA.png" alt="wJ3gJA.png" style="zoom:50%;" />

<img src="https://s1.ax1x.com/2020/09/10/wJYfhQ.png" alt="wJYfhQ.png" style="zoom:50%;" />

<img src="C:\Users\10119\AppData\Roaming\Typora\typora-user-images\image-20200910170843721.png" alt="image-20200910170843721" style="zoom:50%;" />

<img src="https://s1.ax1x.com/2020/09/10/wJwSwq.png" alt="wJwSwq.png" style="zoom:50%;" />

<img src="https://s1.ax1x.com/2020/09/10/wJ01U0.png" alt="wJ01U0.png" style="zoom:50%;" />



### 5.算术逻辑单元

1. ALU电路
2. 快速进位链
   1. 并行加法器
   2. 串行进位链
   3. 并行进位链

<img src="https://s1.ax1x.com/2020/09/10/wJBXlD.png" alt="wJBXlD.png" style="zoom:50%;" />

**双符号位**

“双符号位补码”又称为“变形补du码”。
用两个二进制位来表示数字的符号位，其余数值位与普通补码相同。
例如，用8位字长变形补码表示：
[+111011]补 =00111011 ， 左侧的00就是正数补码的双符号位
[-111011]补 =11000101 ， 左侧的11就是负数补码的双符号位
用变形补码进行加减运算时，可依据运算结果双符号位判断如下四种情况：
11 -----运算结果为负数，无溢出； 00 -----运算结果为正数，无溢出；
10 -----运算结果下溢（负数溢出）； 01 -----运算结果上溢（正数溢出）。