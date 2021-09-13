# 数学建模知识汇总



在线合作Markdown无法使用本地图片，请使用网络图床。

推一个不需要注册的免费图床链接[sm.ms](https://sm.ms)



## PART 1 Matlab基础

### （一）变量

#### 1.1 变量的命名规则

* 有效变量名称以字母开头，后跟字母、数字或下划线
* 有效变量不能出现标点符号和空格
* Matlab变量对大小写敏感
* 变量名称的最大长度为 namelengthmax 命令返回的值（R2018a版本为63）
* 变量名不能为保留字

#### 1.2 特殊变量

| 特殊变量 | 取     值                                   |
| -------- | ------------------------------------------|
| ans      | 用于结果的缺省变量名                         |
| pi       | 圆周率$\pi$                               |
| eps      | 计算机的最小数，和1相加时产生一个比1大的数      |
| flops    | 浮点运算数                                 |
| Inf      | 无穷大，如$1/0$                            |
| NaN      | 不定量，如$0/0$                            |
| i, j     | i=j=$\sqrt{-1}$                          |

----

### （二）数组

#### 2.1 数组的生成

`vector = [a,b,c] or [a b c]` $\Rightarrow vector = \left[\begin{matrix}a & b & c\end{matrix}\right]$​ （行向量）

`vector = [a；b；c]` $\Rightarrow vector = \left[\begin{matrix}a \\ b \\ c\end{matrix}\right]$​​ （列向量）

`vector = 1:100`  $\Rightarrow vector = \left[\begin{matrix}1&2&3&\cdots 100\end{matrix}\right]$​​​ （默认步长为 $1$​ 的长行向量）

`vector = 1:2:100`  $\Rightarrow vector = \left[\begin{matrix}1&3&5&\cdots 99\end{matrix}\right]$​ （设置步长为 $2$​ 的长行向量）

`vector = 100:-1:1`  $\Rightarrow vector = \left[\begin{matrix}100&99&98&\cdots 1\end{matrix}\right]$​ （逆序输出长行向量）

`vector = linspace(1,5,4)`  $\Rightarrow vector = \left[\begin{matrix}1.0000&2.3333&3.6667&5.0000\end{matrix}\right]$​ （从 $1$ 到 $5$，总个数为 $4$​​ 的行向量）

----

### （三）矩阵



#### 3.1 矩阵的生成
`matrix = [a,b,c;d,e,f]` $\Rightarrow matrix = \left[\begin{matrix}a&b&c\\d&e&f\end{matrix}\right]$​​（矩形矩阵）

`matrix = []`  $\Rightarrow matrix = \left[\begin{matrix}\end{matrix}\right]$​​​​（空矩阵，大小为0）

`matrix = diag([a,b,c,d,e,f])` $\Rightarrow matrix = \left[\begin{matrix}a&&&&&\\&b&&&&\\&&c&&&\\&&&d&&\\&&&&e&\\&&&&&f\end{matrix}\right]$​​​​（对角矩阵）

`matrix = zeros(a,b)`  $\Rightarrow matrix = \left[\begin{matrix}0&0&\cdots&0\\\vdots&\vdots&\vdots&\vdots\\0&0&\cdots&0\end{matrix}\right]_{a\times b}$​​​​（全零矩阵）

`matrix = ones(a,b)`  $\Rightarrow matrix = \left[\begin{matrix}1&1&\cdots&1\\\vdots&\vdots&\vdots&\vdots\\1&1&\cdots&1\end{matrix}\right]_{a\times b}$​​​​（全1矩阵）

`matrix = eye(a,b)`  $\Rightarrow matrix = \left[\begin{matrix}1&0&\cdots&0\\0&1&\cdots&0\\ \vdots & \vdots & \ddots & \vdots \\0&0&\cdots&1 
\end{matrix}\right]_{a\times b}$​​​​（单位矩阵，左对齐）

`matrix = rand(a,b)`  $\Rightarrow matrix = \left[\begin{matrix}random(0,1)&\cdots&random(0,1)\\\vdots&\vdots&\vdots&\\random(0,1)&\cdots&random(0,1)\end{matrix}\right]_{a\times b}$​（$(0,1)$均匀随机数矩阵）

`rand('seed',value)`  可以保证每次生成相同的随机数矩阵



#### 3.2 矩阵的形状

`matrix = [a,b,c;d,e,f]` `matrix = matrix'` $\Rightarrow matrix = \left[\begin{matrix}a&d\\b&e\\c&f\end{matrix}\right]$​​​​ （矩阵转置）​

`matrix = [a,b,c;d,e,f]` `matrix = matrix(:)` $\Rightarrow matrix = \left[\begin{matrix}a\\d\\b\\e\\c\\f\end{matrix}\right]$​​​​​ （矩阵变为列向量，列合并）

`matrix = [a,b,c;d,e,f;g,h,i]` `matrix = reshape(matrix, 1, 9)` $\Rightarrow matrix = \left[\begin{matrix}a&b&c&d&e&f&g&h&i\end{matrix}\right]$​​ （矩阵变为行向量，行合并）

- **reshape 函数的参数：reshape(待转换矩阵, 目标行数, 从待转换矩阵中攫取的元素个数)**

  

#### 3.3 矩阵的索引与切片

`matrix = [a,b,c;d,e,f;g,h,i]` `matrix = matrix(3, :)` $\Rightarrow matrix = \left[\begin{matrix}g&h&i\end{matrix}\right]$​​ （取第 $i$​​ 行的行向量）

`matrix = [a,b,c;d,e,f;g,h,i]` `matrix = matrix(:, 2)` $\Rightarrow matrix = \left[\begin{matrix}b\\e\\h\end{matrix}\right]$ （取第 $j$ 列的列向量）

`matrix = [a,b,c;d,e,f;g,h,i]` `matrix = matrix(1: 2, :)` $\Rightarrow matrix = \left[\begin{matrix}a&b&c\\d&e&f\end{matrix}\right]$​​ （取第 $i1$​​ 行到第 $i2$​​ 行的行向量组成的矩阵）

`matrix = [a,b,c;d,e,f;g,h,i]` `matrix = matrix(:, 1 : 2)` $\Rightarrow matrix = \left[\begin{matrix}a&b\\d&e\\g&h\end{matrix}\right]$​ （取第 $j1$​ 列到第 $j2$​​ 列的列向量组成的矩阵）

`matrix = [a,b,c;d,e,f;g,h,i]` `matrix = matrix([1,3], :)` $\Rightarrow matrix = \left[\begin{matrix}a&b&c\\g&h&i\end{matrix}\right]$​​ （取第 $i1$​​ 行和第 $i2$​​ 行的行向量组成的矩阵）

`matrix = [a,b,c;d,e,f;g,h,i]` `matrix = matrix(:, [1,3])` $\Rightarrow matrix = \left[\begin{matrix}a&c\\d&f\\g&i\end{matrix}\right]$​ （取第 $j1$​ 列和第 $j2$​​ 列的列向量组成的矩阵）

`matrix = [a,b,c;d,e,f;g,h,i]` `matrix = matrix(1:2, 1:2)` $\Rightarrow matrix = \left[\begin{matrix}a&b\\d&e\end{matrix}\right]$​ （取第 $i1$​ 行到第 $i2$​ 行，第 $j1$​ 列到第 $j2$​​ 列相交部分的矩阵）

`matrix = [a,b,c;d,e,f;g,h,i]` `matrix = diag(matrix)` $\Rightarrow matrix = \left[\begin{matrix}a\\e\\i\end{matrix}\right]$​ （取对角线元素）

`matrix = [a,b,c;d,e,f;g,h,i]` `matrix = diag(matrix,1)` $\Rightarrow matrix = \left[\begin{matrix}b\\f\end{matrix}\right]$​​ （取第 $1$​​ 条对角线元素）

`matrix = [a,b,c;d,e,f;g,h,i]` `matrix = diag(matrix,1)` $\Rightarrow matrix = \left[\begin{matrix}d\\h\end{matrix}\right]$​​ （取第 $-1$​​ 条对角线元素）



#### 3.4 矩阵的拼接

`a = [1,2,3]` `b = [-1,-2,-3]` `matrix = [a;b]` $\Rightarrow matrix = \left[\begin{matrix}1&2&3\\-1&-2&-3\end{matrix}\right]$ （列数相同矩阵，上下拼接）

`a = [1,2;3,4;5,6]` `b = [-1;-2;-3]` `matrix = [b,a]` $\Rightarrow matrix = \left[\begin{matrix}-1&1&2\\-2&3&4\\-3&5&6\end{matrix}\right]$​​ （行数相同矩阵，左右拼接）



#### 3.5 矩阵的删除

`matrix = [a,b,c;d,e,f;g,h,i]` `matrix(:, 3) = []` $\Rightarrow matrix = \left[\begin{matrix}a&b\\d&e\\g&h\end{matrix}\right]$​ （删除第 $3$​​​ 列）

`matrix = [a,b,c;d,e,f;g,h,i]` `matrix(2, :) = []` $\Rightarrow matrix = \left[\begin{matrix}a&b&c\\d&e&f\end{matrix}\right]$​ （删除第 $2$​​ 行）

`matrix = [a,b,c;d,e,f;g,h,i]` `matrix(6) = []` $\Rightarrow matrix = \left[\begin{matrix}a&d&g&b&e&c&f&i\end{matrix}\right]$​​ 

（删除第 $6$​​ 个元素，从上至下，从左至右数第 $6$​ 个元素 $h$​，之后，$matrix$​ 以一行行向量表示。

**若以 $0$​ 代替，则实际上做的并不是删除，而是用 $0$​​ 替换了原来的元素，意义不同**）

`matrix = [a,b,c;d,e,f;g,h,i]` `matrix(2，3) = 0` $\Rightarrow matrix = \left[\begin{matrix}a&b&c\\d&e&f\\g&0&i\end{matrix}\right]$ （$0$ 代替 $matrix(2,3)$ 的 $h$）



#### 3.6 矩阵的运算

##### 3.6.1 标量-矩阵运算

$a = \left[\begin{matrix}1&2\\3&4\end{matrix}\right], b = \left[\begin{matrix}-1&2\\-3&4\end{matrix}\right]$

`ans = a .* 2`$\Rightarrow ans = \left[\begin{matrix}2&4\\6&8\end{matrix}\right]$​​​​（对应元素与标量相乘）

`ans = a .^ 2`$\Rightarrow ans = \left[\begin{matrix}1&4\\9&16\end{matrix}\right]$​​​​（对应元素的标量次幂）

##### 3.6.2 矩阵-矩阵计算

下面的 $a = \left[\begin{matrix}1&2\\3&4\end{matrix}\right], b = \left[\begin{matrix}-1&2\\-3&4\end{matrix}\right]$

`ans = a .* b`$\Rightarrow ans = \left[\begin{matrix}-1&4\\-9&16\end{matrix}\right]$​​​​（对应元素相乘）

`ans = a * b`$\Rightarrow ans = \left[\begin{matrix}-1&4\\-9&16\end{matrix}\right]$​​​​（矩阵乘法）

`ans = a ./ b`$\Rightarrow ans = \left[\begin{matrix}-1&1\\-1&1\end{matrix}\right]$​​（对应元素相除）

`ans = a / b`$\Rightarrow ans = \left[\begin{matrix}5&-2\\12&5\end{matrix}\right]$​​（矩阵右除）

`ans = a \ b`$\Rightarrow ans = \left[\begin{matrix}-1&0\\0&1\end{matrix}\right]$​​（矩阵左除）

**A/B表示A乘B的逆，若XB=A 则X = A/B = A * inv(B)**

**A\B表示A的逆乘B，若AX=B 则X = A\B = inv(A) * B**


`ans = a.^b`$\Rightarrow ans = \left[\begin{matrix}1&4\\0.037&256\end{matrix}\right]$​​​​​（对应元素求幂）

`ans = a^2`$\Rightarrow ans = \left[\begin{matrix}	7 & 10\\15 & 22\end{matrix}\right]$​​​​​​​​​（ **方**阵乘幂）

##### 3.6.3 统计函数 
`ans = sum(a)` 或 `ans = sum(a, 1)`$\Rightarrow ans = \left[\begin{matrix}4 & 6\end{matrix}\right]$​​（按列计算和）

`ans = sum(a, 2)` $\Rightarrow ans = \left[\begin{matrix}3\\7\end{matrix}\right]$​（按行计算和）

`ans = sum(sum(a))` $\Rightarrow ans = 10$​​​​（计算矩阵所有元素之和）

`ans = cumsum(a)` 或 `ans = cumsum(a, 1)` $\Rightarrow ans = \left[\begin{matrix}1&2\\4&6\end{matrix}\right]$（按列由上至下，迭代计算从本数开始以上所有数的和）

`ans = cumsum(a, 2)` $\Rightarrow ans = \left[\begin{matrix}1&3\\3&7\end{matrix}\right]$（按行由左至右，迭代计算从本数开始以左所有数的和）

----

下面的 $matrix = \left[\begin{matrix}4&8&6\\1&2&9\\7&5&3\end{matrix}\right]$​​。​​​​

`ans = max(matrix)` $\Rightarrow ans = \left[\begin{matrix}7&8&9\end{matrix}\right]$​​ （取每一列的最大元素）

`ans = min(matrix)` $\Rightarrow ans = \left[\begin{matrix}1&2&3\end{matrix}\right]$ （取每一列的最小元素）

`[ans,line] = max(matrix)` $\Rightarrow ans = \left[\begin{matrix}7&8&9\end{matrix}\right], line = \left[\begin{matrix}3&1&2\end{matrix}\right]$ （取每一列的最大元素及每个元素的所在行数）

`[ans,line] = min(matrix)` $\Rightarrow ans = \left[\begin{matrix}1&2&3\end{matrix}\right], line = \left[\begin{matrix}2&2&3\end{matrix}\right]$​​ （取每一列的最小元素及每个元素的所

在行数）

`ans = min(min(matrix))` $\Rightarrow ans = 1$​​​​ （取矩阵最小元素）

`[x, y] = find(matrix == min(min(matrix)))` $\left\{\begin{aligned}x = 2\\y = 1\end{aligned}\right.$​​ （取矩阵最小元素位置）

##### 3.6.4 矩阵的属性量
`ans = inv(matrix)` $\Rightarrow ans = \left[\begin{matrix}-0.1444&0.0222&0.0222\\0.0222&-0.1111&-0.1111\\-0.0333&0.1333&-0.0000\end{matrix}\right]$​ （矩阵求逆）

-  当然之后还可以 `format long` `ans` 得到小数点位数更多的矩阵表示形式 

  $\left[\begin{matrix}0.144444444444444&0.022222222222222&0.222222222222222\\0.222222222222222&-0.111111111111111&-0.111111111111111\\-0.033333333333333&0.133333333333333&-0.000000000000000\end{matrix}\right]$

`ans = det(matrix)` $\Rightarrow ans = 270$​​​​​ （ **方**阵求行列式）

- 求 $n$​​ 阶主子式：`ans = det(matrix(1:n,1:n))` $\Rightarrow ans = 0\ (n = 2)$​​​​​
- 求余子式（以 $matrix$ 中数字 $9$ 为例）：`matrix(2, :) = []` `matrix(:, 3) = []` `ans = det(matrix)`$\Rightarrow ans = -36$​
- 求代数余子式（以 $matrix$​​ 中数字 $9$​​​ 为例）：用上文的 $ans = -36$​​， 再 $\times(-1)^{3+2} = -1$​，则 $ans = 36$​​​

---

下面的 $matrix = \left[\begin{matrix}4&8&6&11\\1&2&9&-1\\7&5&19&3\end{matrix}\right]$​。

`ans = length(matrix)` $\Rightarrow ans = 4$ （取矩阵中行数与列数的较大值）

`ans = size(matrix)` $\Rightarrow ans = \left[\begin{matrix}3&4\end{matrix}\right]$​​ （取矩阵行数与列数）

`ans = mean(matrix)` 或 `ans = mean(matrix, 1)` $\Rightarrow ans = \left[\begin{matrix}4.0000&5.0000&11.3333&4.3333\end{matrix}\right]$​ （按列计算平均值）

 `ans = mean(matrix, 2)` $\Rightarrow ans = \left[\begin{matrix}7.2500\\2.7500\\8.5000\end{matrix}\right]$​​​ （按行计算平均值）

 `ans = mean(mean(matrix))` $\Rightarrow ans = 6.1667$​​​ （计算矩阵元素平均值）

-----

下面的 $matrix = \left[\begin{matrix}4&8&-1\\1&2&0\\3&7&-3\end{matrix}\right]$​​。

`[x, y] =eig(matrix) `  $\Rightarrow x = \left[\begin{matrix}-0.8447&-0.8743 &   0.1961\\
   -0.2326&    0.4520 &  -0.0418\\
   -0.4822 &   0.1766&    0.9797\\\end{matrix}\right], y = \left[\begin{matrix}    5.6319     &    0  &       0\\
         0  &  0.0658     &    0\\
         0        & 0 &  -2.6977\\\end{matrix}\right]$ （计算特征根、特征向量；两矩阵列对应）

- 此时，计算最大特征根即取 $y$ 的对角线，$max$ 即可。

  `ans = max(diag(y))` $\Rightarrow ans = 5.6319$

------

### （四）读取文件

读入 $.xls$：

- 主界面上方导航栏-导入数据-$xls$​​​-划分范围-**选择输出类型为数值矩阵**-保存即可
- `matrix = xlsread('path');` 记住，一定要加分号，不然会将所有读入内容输出于Console，变慢很多

-------

### （五）绘图

~~离散点系列就不纳入了~~

#### 二维函数图像

- 参数可分离

`x start : step : end; ` `y = f(x);` `plot(x, y);` 即可绘制函数图像

- 参数不可分离

  - 参数方程

    `a=` `b=` `t=0:0.01*pi:2*pi` `x=a*cos(t)` `y=b*sin(t)` `plot(x,y)`  **椭圆**

  - 无参数方程

    - `syms x y` `f = 'EQUATION' ` `ezplot(f, X-RANGE, Y-RANGE)` `(axis equal)` 
    **EQUATION 中，等号直接写 =**

----

#### 三维函数图像

- 参数可分离

$eg:\left\{\begin{aligned}&x = \sin{t} + t\cos{t}\\&y= \cos{t} - t\sin{t}\\&z = t\end{aligned}\right.\ \ \ \ (0\leq t\leq 10\pi)$​

`t=linspace(0, 10*pi, 300)` `x=sin(t)+t.*cos(t)` `y=cos(t)-t.*sin(t)` `z=t`	**记得是 .*** 

`subplot(1,2,1) % 子图1` `plot3(x,y,z)` `grid on` 

`subplot(1,2,1) % 子图2` `plot3(x(1:4:200),y(1:4:200),z(1:4:200))` `grid on` 

- 参数不可分离

  - 参数方程

    `a=` `b=` `t=0:0.01*pi:2*pi` `x=a*cos(t)` `y=b*sin(t)` `plot(x,y)`  **椭圆**

  - 无参数方程

    - $z = f(x,y)$ 形式

      `[x,y] = meshgrid(X-RANGE, Y-RANGE)` `z = f(x,y)` `mesh(x,y,z)`

      $eg:\ $​

      `[x,y] = meshgrid(-2:0.1:2, -2:0.1:2)` `z = y .* exp(-x.^2 + -y.^2)` `mesh(x,y,z)`

    - $f(x,y,z)=  0$ 形式

      `fwf`



## PART 2 运筹优化类

* 规划类问题大致可看成目标函数在约束条件下的最值问题。
* 优化模型：$min\ or\ max\ \ z=f(x)\\x =\begin{Bmatrix}
  x_{1},x_{2}...,x_{n} \end{Bmatrix}^{T}\\s.t.\ \ g_{i}(x)\le 0\ \ \ i = 1,2,3...m\\其中z为目标函数，x为决策变量，s.t.为约束条件$ 
* 按模型特点可分为线性规划（LP)、非线性规划(NLP)、整数规划（IP)、动态规划(DP)等



### （一）线性规划

#### 1.1 概念

* 目标函数与约束条件均为线性函数的规划称为线性规划。若可行解限制为整数，则成为整数线性规划，属于规划类里最基础的类型

* 三要素：决策变量、目标函数与约束条件

* 应用：运输、生产、销售问题

#### 1.2 标准型

$$
min\ \ \  c^Tx\ \ \ \ \ \ 
\left\{
\begin{aligned}
&A \cdot x\leq b\\
&Aeq\ x = beq\\
&lb \leq x \leq ub
\end{aligned}
\right.
$$

#### 1.3 Matlab模型描述

`[x,fval] = linprog(c, A, b, Aeq, beq, lb, ub, (x0, options))` 函数用于解决线性规划问题

`[x,fval] = intlinprog(c, intcon, A, b, Aeq, beq, lb, ub, (x0, options))` 函数用于解决整数线性规划问题

- c：目标式中的各变量系数（列向量，**若求最大值，需要将 c 中所有值加负号**）
- intcon：`intlinprog`中，约束哪一个变量有整数的条件。例如 $x_1,x_2, x_3$中，仅$x_3$有整数的要求的话，`intcon=3`，若$x_2,x_3$有整数要求的话，`intcon=[2,3]`
- A：所有不等式(**必须转换为左 $\leq$​​ 右的形式**)的系数矩阵
- b：不等式右侧的常数矩阵
- Aeq：所有等式的系数矩阵(**没有的话记空矩阵[]**)
- beq：等式的常数矩阵(**没有的话记空矩阵[]**)
- lb：对 $x$​​ 的限制下界(**没有的话记空矩阵[]**)
- ub：对 $x$​ 的限制上界(**没有的话记空矩阵[]**)
- $x_0$​​：$x$​​​ 的迭代开始点(**如果有的话，用列向量标出迭代开始点；可以没有**)
- options：控制参数（**可以缺省**）

#### 1.4 例题
$eg: Work\ out:$
$$
\underline{min}\ z = 7x_1+5x_2+9x_3+6x_4+3x_5\ \ \ \ \\
\\ $$ $$ 
s.t.
\left\{
\begin{aligned}
&56x_1 + 20x_2+54x_3+42x_4+15x_5\leq 100\\
&x_1+4x_2+x_3\leq4\\
&x_1+2x_2+x_4+2x_5\geq 2\\
&\underline{x_1,x_2,x_3,x_4,x_5 \in \{0, 1\}}
\end{aligned}
\right.
$$
MATLAB 如下：

````matlab
c=[7,5,9,6,3];
intcon=[1,2,3,4,5];							% 如果是 max 要反过来
A=[56,20,54,42,15;1,4,1,0,0;-1,-2,0,-1,-2];	% 有一组要反过来
b=[100;4;-2];								% 有一个要反过来
lb=zeros(5,1);								% [0;0;0;0;0] 
ub=ones(5,1);								% [1;1;1;1;1]
[x,fval,flag]=intlinprog(c,intcon,A,b,[],[],lb,ub)   % 无等式
````

$$
\Rightarrow
\left\{
\begin{aligned}
& x = \left[\begin{matrix}0\\0\\0\\0\\1\end{matrix}\right]\\
& fval = 3
\end{aligned}
\right.
$$

对于非线性函数，可以使用对数等等手段变为线性函数之类。

**线性投资问题看《数学建模与MATLAB应用》$P_{14}$​​​​**

------

### （二）非线性规划

#### 2.1 概念

* 目标函数或约束条件中包含非线性函数的规划称为非线性规划（国赛中的大部分规划题都为非线性规划，难度较大，求解较困难，有时也会转化成启发式算法求解）

* 三要素：决策变量、目标函数与约束条件

* 应用：投资决策等大部分规划

#### 2.2 标准型

$$
\ min\ f(x) \ \ s.t.\left\{\begin{aligned}&Ax\leq B\\&Aeq\cdot x=Beq\\&C(x)\leq0\\&Ceq(x) = 0 \\&lb\leq x\leq ub\end{aligned}\right.
$$
#### 2.3 Matlab模型描述

`x = fmincon(FUN, X0, A, B, Aeq, Beq, LB, UB, NONLCON, OPTIONS)`

- FUN：函数 $f(x)$​​​ **（求max要取负）**
- X0：$x$​ 初始值（不可为空，不知道填啥就用随机数 `rand()`）
- A：所有**线性**不等式（**必须转换为左 $\leq$​ 右的形式**）的系数矩阵（没有的话记空矩阵[]）
- B：**线性**不等式右侧的常数矩阵（**没有的话记空矩阵[]**）
- Aeq：所有**线性**等式的系数矩阵（**没有的话记空矩阵[]**）
- Beq：**线性**等式的常数矩阵（**没有的话记空矩阵[]**）
- LB：对 $x$​​​ 的限制下界（**没有的话记空矩阵[]**）
- UB：对 $x$​​ 的限制上界**（**没有的话记空矩阵[]**）
- NONLCON：其中包括**非线性**不等式函数 $C(x)$，**非线性**等式函数 $Ceq(x)$
- options：控制参数（**可以缺省**）

#### 2.4 例题

$eg: Work\ out:$
$$
\underline{min}\ f(x) = x_1^2+x_2^2+x_3^2+8\ \ \ \ ,
\left\{
\begin{aligned}
&x_1^2-x_2+x_3^2\geq 0\\
&x_1+x_2^2+x_3^2\leq 20\\
&-x_1-x_2^2+2=0\\
&x_2+2x_3^2=3\\
&x_1,x_2,x_3 \geq 0
\end{aligned}
\right.
$$
MATLAB 如下：

- 首先创建目标函数 fun1.m（函数不支持直接上下文创建）：

  ````matlab
  function f = fun1(x);
  f = sum(x.^2) + 8;
  ````

- 再创建非线性函数 fun2.m：

  ````matlab
  function [g, h] = fun2(x);
  g = [-x(1)^2+x(2)-x(3)^2
      x(1)+x(2)^2+x(3)^3-20];
  h = [-x(1)-x(2)^2+2
       x(2)+2*x(3)^2-3];
  ````

- 最后写主函数

  ````matlab
  options = optimset('largescale','off');
  [x,y] = fmincon('fun1',rand(3,1),[],[],[],[],zeros(3,1),[],'fun2',options);
  ````
$$
\Rightarrow
\left\{
\begin{aligned}
& x = \left[\begin{matrix}0.5522\\1.2033\\0.9478\end{matrix}\right]\\
\\
& fval = 10.6511
\end{aligned}
\right.
$$
注意：所有函数的.m文件应当放在同一文件夹内

### （三）目标规划

#### 3.1 概念

目标规划是线性规划的一种特殊类型，能够处理单个主目标和多个次目标并存的问题。

----



## PART 3 评价决策类

### （一）AHP 层次分析法

- 划分指标（$n$ 个，指标用 $A_i$ 表示，以 $5$ 个为例）
- 建立指标权重比较用矩阵（成对比较阵 ，$n\times n$​ 方阵 ）

|       | $A_1$ | $A_2$ | $A_3$ | $A_4$ | $A_5$ |
| :---: | :---: | :---: | :---: | :---: | :---: |
| $A_1$ |   1   |       |       |       |       |
| $A_2$ |       |   1   |       |       |       |
| $A_3$ |       |       |   1   |       |       |
| $A_4$ |       |       |       |   1   |       |
| $A_5$ |       |       |       |       |   1   |

![屏幕截图 2021-08-23 172042.png](https://i.loli.net/2021/08/24/AvLctkgT2zZhMHs.png)

左侧为 $i$ 标号，右侧为 $j$​ 标号。

在进行第二步的时候，仅仅根据个人分析进行得出，可能有不一致的情况（$eg:$​​​ 某些比例关系可以根据其他关系计算出来，计算结果与直观感受得出的结果不一致），此时需要进行**一致性检验**。

$Saaty$ 等提出使用方阵的**最大特征值 $\lambda_{max}$** 帮助判断。当 $\lambda_{max} = n$ 时，判断该矩阵一致。此时，当 $\lambda_{max} >> n$ 时，矩阵不一致情况严重。此时提出使用一致性指标 $CI = \frac{\lambda_{max}-n}{n - 1}$ 来进行衡量，$CI = 0$ 时，矩阵严格一致。为了有一定的容错性，$Saaty$ 引入随机一致性指标 $RI$​​：

|      |  3   |  4   |  5   |  6   |  7   |  8   |  9   |  10  |  11  |  12  |  13  |  14  |
| :--: | :--: | :--: | :--: | :--: | :--: | :--: | :--: | :--: | :--: | :--: | :--: | :--: |
| $RI$ | 0.58 | 0.9  | 1.12 | 1.24 | 1.32 | 1.41 | 1.45 | 1.49 | 1.52 | 1.56 | 1.58 | 1.59 |

引入 $CR(Coherence\ Rate) = \frac{CI}{RI}$​​。当 $CR < 0.1$​​ 时，判定该矩阵不一致程度在容错范围内。

- 计算权重

权重向量所对应的是在计算 $\lambda_{max}$ 时所对应的相同位置的列的当中每一个量占该列值总和的比重。

- 算所选事物的具体指标值

若有 $n$ 个事务待筛选，每个事务下有 $m$ 个指标用于概括和建立模型，则最终需建立 $m$ 个 $n \times n$​ 的矩阵用于计算指标值。

$eg:\ $ 去哪里旅游（视频教程内例子）

给定三个地点，苏州、杭州、桂林。

- **建立**五个指标（景色、费用、居住、饮食、旅途）用于概括。

-----

以下为比较不同的指标，从而得出指标的权重。（比较指标）

- **直观建立**成对比较阵（$need\ to\ revise$​）

|       |     $A_1$     |     $A_2$     |     $A_3$     | $A_4$ | $A_5$ |
| :---: | :-----------: | :-----------: | :-----------: | :---: | :---: |
| $A_1$ |       1       | $\frac{1}{4}$ | $\frac{1}{4}$ |   2   |   2   |
| $A_2$ |       4       |       1       |       1       |   6   |   6   |
| $A_3$ |       4       |       1       |       1       |   6   |   6   |
| $A_4$ | $\frac{1}{2}$ | $\frac{1}{6}$ | $\frac{1}{6}$ |   1   |   1   |
| $A_5$ | $\frac{1}{2}$ | $\frac{1}{6}$ | $\frac{1}{6}$ |   1   |   1   |

`a = [1, 1/4, 1/4, 2, 2; 4, 1, 1, 6, 6; 4, 1, 1, 6, 6; 1/2, 1/6, 1/6, 1, 1; 1/2, 1/6, 1/6, 1, 1]` 

- 验证一致性
$$
\lambda_{max} = 5.0133\\
CI = \frac{5.0133 - 5}{5-1} = 0.0033157\\
CR = \frac{0.0033}{1.12} = 0.0029605 < 0.1
$$
 一致性检验通过。

````matlab
n = length(a); 						% 取n
[v,d]=eig(a); 						% 计算特征根和特征向量
[r,loc] = max(max(d));				% 返回最大特征向量及其所在列数
									% r = 5.0133, loc = 1 (第一列)
CI=(r-n)/(n-1);
RI=[0 0 0.58 0.90 1.12 1.24 1.32 1.41 1.45 1.49 1.52 1.54 1.56 1.58 1.59];
CR=CI/RI(n);						% 取 CR 的第 n 个元素
if  CR<0.10 || n==2
    CR_Result='通过';
   else
    CR_Result='不通过';   
end
````

- 得到权值向量

已知 $\lambda_{max} = 5.0133$，所对应的列元素为 $w = \left[\begin{matrix}0.1929\\0.6854\\0.6854\\0.1078\\0.1078\end{matrix}\right]$，此时计算每个元素的占总和比即可

````matlab
w=v(:,loc)/sum(v(:,loc));			% 个体除以总和
w=w';								% 转置
````
$$
w = \left[\begin{matrix}0.10839 & 0.38521 & 0.38521 & 0.060598 & 0.060598\end{matrix}\right]
$$
-----

以下为对于每一个指标，比较三个城市。（比较城市）

- 按照不同的指标（景色、费用、居住、饮食、旅途）， 对每一个城市依次**直观建立**成对比较阵

$B_1:$​

| 景色 |     苏州      |     杭州      | 桂林 |
| :--: | :-----------: | :-----------: | :--: |
| 苏州 |       1       |       2       |  5   |
| 杭州 | $\frac{1}{2}$ |       1       |  2   |
| 桂林 | $\frac{1}{5}$ | $\frac{1}{2}$ |  1   |

后同（使用视频例子）：
$$
B_2 = \left[\begin{matrix}
1 & \frac{1}{3} & \frac{1}{8} \\
3 & 1 & \frac{1}{3} \\
8 & 3 & 1 \\
\end{matrix}\right],\ 

B_3 = \left[\begin{matrix}
1&1&3 \\
1&1&3 \\
\frac{1}{3} & \frac{1}{3} & 1 \\
\end{matrix}\right],\ 

B_2 = \left[\begin{matrix}
1&3&4 \\
\frac{1}{3} & 1 & 1 \\
\frac{1}{4} & 1 & 1 \\
\end{matrix}\right],\ 

B_2 = \left[\begin{matrix}
1 & 1 & \frac{1}{4} \\
1 & 1 & \frac{1}{4} \\
4 & 4 & 1 \\
\end{matrix}\right]
$$

- 对每一个矩阵进行一致性验证、计算权值向量（略），结果如下

|          | 景色  | 费用  | 居住  | 饮食  | 旅途  |
| :------: | :---: | :---: | :---: | :---: | :---: |
| **苏州** | 0.595 | 0.082 | 0.429 | 0.633 | 0.166 |
| **杭州** | 0.277 | 0.236 | 0.429 | 0.193 | 0.166 |
| **桂林** | 0.129 | 0.682 | 0.142 | 0.175 | 0.668 |

----

- 计算模型评判值

| 苏州     | $0.10839*0.595+0.38521*0.082+0.38521*0.429+0.060598*0.633+0.060598*0.166= 0.309752162$ |
| -------- | ------------------------------------------------------------ |
| **杭州** | **$0.10839*0.277+0.38521*0.236+0.38521*0.429+0.060598*0.193+0.060598*0.166= 0.307943362$​** |
| **桂林** | **$0.10839*0.129+0.38521*0.682+0.38521*0.142+0.060598*0.175+0.060598*0.668= 0.382479464$​​** |

综上，选桂林。
