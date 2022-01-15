## LaTex公式总结



#### 一、希腊字母

**小写字母**：按照希腊字母对照表正常输入即可。

**大写字母**：只需将对应小写字母的首字母大写即可。

要注意希腊字母的变体。
$$
\delta ,\lambda \\
\Delta, \Lambda \\
\alpha,\beta \\
\Alpha,\Beta \\
\phi, \varphi \\
\epsilon, \varepsilon
$$
**希腊字母对照表**

<img src="/Users/macbook/Desktop/截屏2022-01-14 11.23.02.png" alt="截屏2022-01-14 11.23.02" style="zoom: 33%;" />





#### 二、上下标

**下标**：使用下划线_

**上标**：使用^

当上下标多余一个字符时，需要用**大括号**括起。

表示变量时才可以使用斜体，其他情况下都使用罗马体。常用\rm 或\text表示直立体。

二者的区别是：

在没有大括号时，\rm会将其后的所有字母都变为直立体；而\text只会将其后第一个字母变为直立体。

在有大括号时，\rm无视空格，而\text不忽略空格。


$$
x^2\\
a_0\\
x^{e^x}\\
a_{i^k}\\
x_i,x_{\rm i},x_{\text i}\\
\text{A B},\rm{A B}\\
\text AB,\rm AB
$$


#### 三、分式与根式

分式采用\frac{}{}来表示，其中第一个大括号为分子，第二个大括号为分母。

根式采用\sqrt[]{}表示，其中第一个中括号表示开几次方根，第二个大括号表示被开方数。
$$
\frac{a}{b},\frac 1 2, \frac{x}{x+\frac{1}{y}}\\
\sqrt{2},\sqrt[3]{4}
$$

#### 四、普通运算符

 **运算类**

| 运算符 | latex公式表示 | 渲染效果       |
| ------ | ------------- | -------------- |
| 加法   | +             | $+$            |
| 减法   | -             | $-$            |
| 乘法   | \times,\cdot  | $\times,\cdot$ |
| 除法   | \div          | $\div$         |
| 正负   | \pm           | $\pm$          |
| 负正   | \mp           | $\mp$          |



**关系类**

| 运算符   | latex公式表示 | 渲染效果  |
| -------- | ------------- | --------- |
| 大于     | >             | $>$       |
| 小于     | <             | $<$       |
| 大于等于 | \ge           | $\ge$     |
| 小于等于 | \le           | $\le$     |
| 远大于   | \gg           | $\gg$     |
| 远小于   | \ll           | $\ll$     |
| 不等于   | \ne           | $\ne$     |
| 约等于   | \approx       | $\approx$ |
| 恒等于   | \equiv        | $\equiv$  |



**集合类**

| 运算符 | latex公式表示 | 渲染效果      |
| ------ | ------------- | ------------- |
| 交集   | \cap          | $\cap$        |
| 并集   | \cup          | $\cup$        |
| 属于   | \in           | $\in$         |
| 不属于 | \notin        | $\notin$      |
| 子集   | \subseqeq     | $\subseteq$   |
| 真子集 | \\subsetneq   | $\subsetneq$  |
| 空集   | \varnothing   | $\varnothing$ |
| 数集   | \mathbb{}     | $\mathbb{R}$  |



**逻辑类**

| 运算符 | latex公式表示 | 渲染效果     |
| ------ | ------------- | ------------ |
| 任意   | \forall       | $\forall$    |
| 存在   | \exists       | $\exists$    |
| 不存在 | \nexists      | $\nexists$   |
| 因为   | \because      | $\because$   |
| 所以   | \therefore    | $\therefore$ |



**乱七八糟类**

| 运算符     | latex公式表示 | 渲染效果   |
| ---------- | ------------- | ---------- |
| 无穷       | \infty        | $\infty$   |
| 横向省略号 | \cdots        | $\cdots$   |
| 纵向省略号 | \vdots        | $\vdots$   |
| 斜向省略号 | \ddots        | $\ddots$   |
| 偏微分     | \partial      | $\partial$ |
| 微分算子   | \nabla        | $\nabla$   |



**函数类**

三角函数：$\sin x,\cos x,\cosh x$

对数函数：$\log_2{x},\ln x,\lg x$

极限符号：$\lim_{x \to 0} \frac{\sin x}{x} ,\lim_\limits{x\to 0} \frac{\sin x}{x}$

注意，通常情况下极限符号的逼近条件显示在lim的右侧，如果想让其显示在下侧，需要在lim后加\limits



#### 五、大型运算符

| 运算符   | latex公式表示 | 渲染效果 |
| -------- | ------------- | -------- |
| 求和     | \sum          | $\sum$   |
| 求积     | \prod         | $\prod$  |
| 一重积分 | \int          | $\int$   |
| 二重积分 | \iint         | $\iint$  |
| 三重积分 | \iiint        | $\iiint$ |
| 回路积分 | \oint         | $\oint$  |

求和号的上下界表示：$\sum_{i = 0}^N,\sum\limits_{i = 0}^N $

积分上下界表示：$\int_{-\infty}^{\infty}f(x)\,\text dx$

积分的d通常要用直立体，并且在d前，应该有一个小空格，使用\, 来打出这个空格。



#### 六、标注符号 

| 运算符     | latex公式表示   | 渲染效果              |
| ---------- | --------------- | --------------------- |
| 单字符向量 | \vec            | $\vec{a}$             |
| 多字符向量 | \overrightarrow | $\overrightarrow{AB}$ |
| 单字符均值 | \bar            | $\bar{a}$             |
| 多字符均值 | \overline       | $\overline{a+b}$      |

**标注符号参考表**

![截屏2022-01-14 12.43.41](/Users/macbook/Library/Application Support/typora-user-images/截屏2022-01-14 12.43.41.png)



#### 七、箭头

| 运算符     | latex公式表示   | 渲染效果          |
| ---------- | --------------- | ----------------- |
| 左箭头     | \leftarrow      | $\leftarrow$      |
| 右箭头     | \rightarrow     | $\rightarrow$     |
| 右双箭头   | \Rightarrow     | $\Rightarrow$     |
| 左双箭头   | \Leftarrow      | $\Leftarrow$      |
| 左右双箭头 | \Leftrightarrow | $\Leftrightarrow$ |

<img src="/Users/macbook/Library/Application Support/typora-user-images/截屏2022-01-14 12.55.22.png" alt="截屏2022-01-14 12.55.22" style="zoom: 50%;" />

#### 八、括号 

| 运算符 | latex公式表示    | 渲染效果          |
| ------ | ---------------- | ----------------- |
| 小括号 | ()               | $()$              |
| 中括号 | []               | $[]$              |
| 大括号 | \ { \ }          | $\{\}$            |
| 上取整 | \rceil,\lceil    | $\lceil,\rceil$   |
| 下取整 | \rfloor, \lfloor | $\lfloor,\rfloor$ |

界定符的大小自适应：$\left(0,\frac{1}{a}\right],\left . \frac{\partial y}{\partial x}\right|_{x = 0}$



#### 九、多行公式

$$
\begin{align}
a &= b+c+d \\
&= e +f
\end{align}
$$

 &用于对齐



#### 十、大括号

$$
f(x) = 
\begin{cases}
\sin x,& -\pi\leq x \leq \pi \\
0,& \text{其他}
\end{cases}
$$



#### 十一、矩阵

**matrix**:无括号矩阵
$$
\begin{matrix}
a & b & \cdots & c \\ 
\vdots & \vdots & \ddots & \vdots\\
e & f & \cdots & g

\end{matrix}
$$
**bmatrix**：方括号矩阵
$$
\begin{bmatrix}
a & b & \cdots & c \\ 
\vdots & \vdots & \ddots & \vdots\\
e & f & \cdots & g

\end{bmatrix}
$$
**pmatrix**：圆括号矩阵
$$
\begin{pmatrix}
a & b & \cdots & c \\ 
\vdots & \vdots & \ddots & \vdots\\
e & f & \cdots & g

\end{pmatrix}
$$
**vmatrix**：行列式形式
$$
\begin{vmatrix}
a & b & \cdots & c \\ 
\vdots & \vdots & \ddots & \vdots\\
e & f & \cdots & g

\end{vmatrix}
$$
矩阵的表示：通常用粗体的直立的罗马体。\bf表示
$$
\bf A,\bf A^{\rm T}
$$

#### 实践

<img src="/Users/macbook/Library/Application Support/typora-user-images/截屏2022-01-15 12.53.32.png" alt="截屏2022-01-15 12.53.32" style="zoom:33%;" />
$$
f(x) = \frac{1}{\sqrt{2\pi}\sigma}\text e^{-\frac{(x-\mu)^2}{2\sigma^2}}
$$

<img src="/Users/macbook/Library/Application Support/typora-user-images/截屏2022-01-15 12.57.12.png" alt="截屏2022-01-15 12.57.12" style="zoom: 25%;" />
$$
\lim\limits_{N \to \infty} P\left \{\left|\frac{I(\alpha_i)}{N}-H(s)\right|<\varepsilon\right\}  = 1
$$


​                                    

​																					<img src="/Users/macbook/Library/Application Support/typora-user-images/截屏2022-01-15 13.00.06.png" alt="截屏2022-01-15 13.00.06" style="zoom: 33%;" />         
$$
x(n) = \frac{1}{2\pi}\int_{-\pi}^{\pi}X\,\left(\text e^{\text j\omega}\right)\text e^{\text j \omega n} \,\text d\omega
$$

<img src="/Users/macbook/Library/Application Support/typora-user-images/截屏2022-01-15 13.05.00.png" alt="截屏2022-01-15 13.05.00" style="zoom:25%;" />
$$
\begin{align}
\vec B(\vec r) &= \frac{\mu_0}{4\pi}\oint_C  \frac{I\,\text d\vec l\times\vec R}{R^3}\\
&= \frac{\mu_0}{4\pi}\int_V \frac{\vec J_V \times\vec R}{R^3} \, \text dV' 

\end{align}
$$
