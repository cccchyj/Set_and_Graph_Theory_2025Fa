# 第 7 章 生成函数与递推关系

---

## 7.1 幂级数型生成函数

---

### 7.1 定理 7.1
设数列 $\{a_n\}$，$\{b_n\}$，$\{c_n\}$ 的生成函数分别是 $f(x)$，$g(x)$ 和 $h(x)$，$r$ 为常数。

$f(x)=\sum_{n\ge0}a_nx^n$，$g(x)=\sum_{n\ge0}b_nx^n$，$h(x)=\sum_{n\ge0}c_nx^n$。

#### 1. 如果 $b_n = r a_n$，则 $g(x) = r f(x)$。

若 $b_n=ra_n$，则 $g(x)=\sum_{n\ge0}b_nx^n=\sum_{n\ge0}r a_n x^n=r\sum_{n\ge0}a_nx^n=r f(x)$。

#### 2. 如果 $c_n = a_n + b_n$，则 $h(x) = f(x) + g(x)$。

若 $c_n=a_n+b_n$，则 $h(x)=\sum c_nx^n=\sum(a_n+b_n)x^n=\sum a_nx^n+\sum b_nx^n=f(x)+g(x)$。


#### 3. 如果 $c_n = \sum_{i = 0}^n a_i b_{n - i}$，则 $h(x) = f(x) \cdot g(x)$。

若 $c_n=\sum_{i=0}^n a_i b_{n-i}$，则
$$h(x)=\sum_{n\ge0}c_nx^n=\sum_{n\ge0}\Big(\sum_{i=0}^n a_i b_{n-i}\Big)x^n.$$

交换求和得
$$h(x)=\sum_{i\ge0}\sum_{j\ge0} a_i b_j x^{i+j}=\Big(\sum_{i\ge0}a_i x^i\Big)\Big(\sum_{j\ge0}b_j x^j\Big)=f(x)g(x),$$

即系数卷积对应乘法。


#### 4. 如果 $b_n = \begin{cases} 0 & n < l \\ a_{n - l} & n \geqslant l \end{cases}$ ，则 $g(x) = x^l \cdot f(x)$。

若 $b_n=0$ 当 $n<l$，且 $b_n=a_{n-l}$ 当 $n\ge l$，则
$$g(x)=\sum_{n\ge0}b_nx^n=\sum_{n\ge l}a_{n-l}x^n=x^l\sum_{m\ge0}a_m x^m=x^l f(x).$$


#### 5. 如果 $b_n = a_{n + l}$，则 $g(x) = \frac{f(x) - \sum_{n = 0}^{l - 1} a_n x^n}{x^l}$.

若 $b_n=a_{n+l}$，则
$$g(x)=\sum_{n\ge0}a_{n+l}x^n=\frac{1}{x^l}\Big(\sum_{n\ge0}a_{n}x^{n}-\sum_{n=0}^{l-1}a_nx^n\Big)=\frac{f(x)-\sum_{n=0}^{l-1}a_nx^n}{x^l}.$$


#### $\star$ 6. 如果 $b_n = \sum_{i = 0}^n a_i$，则 $g(x) = \frac{f(x)}{1 - x}$.

当 $|x|\lt 1$ 时，已知几何级数公式：
$$\frac{1}{1-x} = \sum_{i=0}^\infty x^i \quad (|x|<1)$$

那么：
$$\frac{f(x)}{1-x} = \left(\sum_{i=0}^\infty{x^i}\right)\cdot\left(\sum_{i=0}^\infty{a_ix^i}\right) = \sum_{i=0}^\infty{\left(\sum_{j=0}^{i}{a_j}\right)\cdot x^i} = g(x).$$

第二个等号由观察两个幂级数相乘时，$x^n$ 的系数得到：
$$\begin{matrix}
x^0 & x^1 & x^2 & x^3 & x^4 & \cdots \\
a_0 & a_1 & a_2 & a_3 & a_4 & \cdots \\
    & a_0 & a_1 & a_2 & a_3 & \cdots \\
    &     & a_0 & a_1 & a_2 & \cdots \\
    &     &     & a_0 & a_1 & \cdots \\
    &     &     &     & a_0 & \cdots \\
\end{matrix}$$

每一列 $x^n$ 的系数是这一列从上到下所有项的和。

#### $\star$ 7. 如果 $b_n = \sum_{i = 0}^\infty a_i$，且 $f(1) = \sum_{n = 0}^\infty a_n$ 收敛，则 $g(x) = \frac{f(1) - x f(x)}{1 - x}$.

若 $b_n=\sum_{i=0}^\infty a_i$（与 $n$ 无关）并且 $S:=\sum_{n\ge0}a_n=f(1)$ 收敛，则对每一 $n$ 有 $b_n=S$。

$$\begin{aligned}
\frac{f(1)-xf(x)}{1-x}
&= \frac{\sum\limits_{i=0}^\infty{a_i}-\sum\limits_{i=0}^\infty{a_ix^i}}{1-x^{i+1}}\\
&= \frac{\sum\limits_{i=0}^\infty{a_i(1-x^{i+1})}}{1-x}\\
&= \sum_{i=0}^\infty{a_i(1+x+x^2+\cdots+x^i)}\\
&= \sum_{i=0}^\infty{\left(\sum_{j=i}^\infty{a_j}\right)x^i}\\
&= \sum_{i=0}^\infty{b_ix^i} = g(x).
\end{aligned}$$

<!-- 我们从下面这个恒等式出发：
$$f(1) - x f(x) = \sum_{n \ge 0} a_n - x \sum_{n \ge 0} a_n x^n = \sum_{n \ge 0} a_n (1 - x^{n+1}).$$
把它写成：
$$f(1) - x f(x) = (1 - x) \sum_{n \ge 0} (a_0 + a_1 + \cdots + a_n) x^n.$$
两边除以$（1 - x)$，得：
$$\frac{f(1) - x f(x)}{1 - x} = \sum_{n \ge 0} (a_0 + a_1 + \cdots + a_n) x^n.$$
这表示的是当 $b_n = \sum_{i = 0}^{n} a_i$ 时的生成函数（即定理 7.1 第 6 条）。
而如果 $\sum_{i = 0}^{\infty} a_i = S$ 收敛，则当 $n \to \infty$，部分和 $\sum_{i = 0}^n a_i \to S$，所以极限情形（即第 7 条）变成：
$$g(x) = \frac{f(1) - x f(x)}{1 - x}.$$ -->


#### 8. 如果 $b_n = r^n a_n$，则 $g(x) = f(r x).$

若 $b_n=r^n a_n$，则
$$g(x)=\sum_{n\ge0} r^n a_n x^n=\sum_{n\ge0} a_n (r x)^n=f(r x).$$
#### 9. 如果 $b_n = n a_n$，则 $g(x) = x f'(x) .$

若 $b_n=n a_n$，则
$$
g(x)=\sum_{n\ge0} n a_n x^n = x\frac{d}{dx}\sum_{n\ge0} a_n x^n = x f'(x).
$$
#### 10.  如果 $b_n = \frac{a_n}{n + 1}$，则 $g(x) = \frac{1}{x} \int_0^x f(x) \, dx$。

计算右边积分：
$$\int_0^x f(t)dt = \int_0^x \sum_{n=0}^\infty a_n t^n dt = \sum_{n=0}^\infty a_n \int_0^x t^n dt
= \sum_{n=0}^\infty a_n \frac{x^{n+1}}{n+1}.$$

两边同时除以 $x$：
$$\frac{1}{x}\int_0^x f(t)dt = \sum_{n=0}^\infty \frac{a_n}{n+1} x^n = \sum_{n=0}^\infty b_n x^n = g(x).$$

---

### 7.2 一袋内装有 5 个红球，4 个白球，3 个黑球。

#### (1) 从袋中任取 5 个球有多少种不同的取法？

设$（r,w,b)$ 为取到的三色球数，满足
$$r+w+b=5,\quad 0\le r\le5,\ 0\le w\le4,\ 0\le b\le3.$$

只需数满足上述约束的非负整数解个数。枚举 $b=0,1,2,3$，对每一固定 $b$，$w$ 的取值为 $0\le w\le\min(4,5-b)$，并且 $r=5-w-b$ 自动确定。列举计数可得共有 $17$ 种不同取法。

#### (2) 又若要求从袋中取 8 个球，但至少有两个白球，共有多少种取法？

若取 8 个球且至少有两个白球，仍设 $r+w+b=8$，并加约束 $w\ge2$，同时 $r\le5,w\le4,b\le3$。枚举满足约束的非负解得到共有 $11$ 种取法。

##### 或用母函数的方法：

(1) 设母函数 $\displaystyle f(x)=(\sum_{i=0}^5{x^i}) \cdot (\sum_{i=0}^4{x^i}) \cdot (\sum_{i=0}^3{x^i})=(1+x+...+x^5 )(1+x+x^2 +x^3 +x^4 )(1+x+x^2 +x^3 )$，所求方法数为 $f(x)$中$x^5$ 的系数。

(2) 设母函数 $\displaystyle f(x)=(\sum_{i=0}^5{x^i}) \cdot (\sum_{i=2}^4{x^i}) \cdot (\sum_{i=0}^3{x^i})=(1+x+...+x^5 )(x^2 +x^3 +x^4 )(1+x+x^2 +x^3 )$，所求为 $f(x)$ 中 $x^8$ 的系数。

---

### 7.3 某单位有 9 位先生，5 位女士，要从他们中产生一个小组，规定先生必须偶数个，女士至少要有两位，问有多少种产生小组的方法？

允许选择任意规模的小组（只要满足条件）。

这里我们认为先生之间地位等同，女士之间地位等同。例如，2位先生和3位女士构成了一个小组，但是具体是哪两位先生和哪三位女士无所谓，算作一种。

设母函数$$\displaystyle f(x) = \left(\sum_{i=0}^4{x^{2i}}\right) \cdot \left(\sum_{i=2}^5{x^i}\right) = (1+  x^ {2}  +  x^ {4}  +  x^ {6}  +  x^ {8}  )(  x^ {2}  +  x^ {3}  +  x^ {4}  +  x^ {5}  )$$

所求为$f(x)$展开式中各项系数之和，也即$f(1)$的值，$f(1)=20$。

如果考虑先生之间不同，女士之间不同，那就按照正常的排列组合加法乘法原理去做：
$$\displaystyle \left(\sum_{i=0}^4{{9 \choose i}}\right) \cdot \left(\sum_{i=2}^5{{5 \choose i}}\right)=6656.$$

---

### ✅7.4 一只兔子的寿命恰好 10 年。假如开始时，有两只刚出生的小兔，并且以后每年出生的兔子数是前一年出生的兔子数的两倍。求第$r$年兔子的总数。

设第$n$年兔子总数为$a_n$. 由题意，第$n$年有$2^n$兔子出生.

当$1\leq n\leq 10$时，没有兔子死亡，其递推关系式为$a_n=a_{n-1}+2^n$.
$$
\begin{matrix}
a_n-a_{n-1}=2^n \\
\cdots \\
a_2-a_1=4
\end{matrix}
$$$$a_n=a_1+\frac{4-4\cdot 2^{n-1}}{1-2}=2^{n+1}-2$$

当$n\gt 10$时，开始有兔子死亡了，其递推关系式为$a_n=a_{n-1}+2^n-2^{n-10}$.
$$
\begin{matrix}
a_n-a_{n-1}=2^{n-10}\cdot 1023 \\
\cdots \\
a_{11} - a_{10} = 2\cdot 1023
\end{matrix}
$$

$$a_n = a_{10}+1023\cdot \frac{2 - 2\cdot 2^{n-10}}{1-2}= 1023\cdot 2^{n-9}$$

<!-- 
记第$k$年出生的兔子数为$B_k$，题给$B_0=2$，且$B_k=2B_{k-1}$，所以$B_k=2^{k+1}$。

每只兔子寿命 10 年（含出生年共 10 年），因此第$r$年存活的兔子为最近 10 年内出生的个体的和。

若$r\le 10$，则从第 0 年到第$r$年的出生都还活着，总数为
$$
T_r=\sum_{i=0}^r B_i=\sum_{i=0}^r 2^{i+1}=2\sum_{i=0}^r 2^i=2(2^{r+1}-1).
$$

若$r\ge9$，则只有过去 10 年（含当年）出生的兔子存活，即出生年索引从$r-9$到$r$，于是
$$
T_r=\sum_{i=r-9}^{r}2^{i+1}=2^{r-8}\big(2^{10}-1\big).
$$
 -->

---

### $\star$ ✅7.5 在无限多的红球、白球、蓝球和黄球中选取$r$个球，使得这$r$个球必须满足：红球是偶数个且蓝球是奇数个，或者白球是偶数个且蓝球是奇数个，或者白球是偶数个且黄球是奇数个。设$a_r$表示满足上述条件的选取方式数。

#### 1. 求生成函数$f(y)$。

##### 单色生成函数  
- 任取非负个数：$\displaystyle \sum_{k\ge0} y^{k} = 1 + y + y^2 + y^3 + \dots =\frac{1}{1-y}$  
- 偶数个：$\displaystyle  \sum_{k\ge0} y^{2k} = 1 + y^2 + y^4 + \dots = \frac{1}{1-y^2}$  
- 奇数个：$\displaystyle \sum_{k\ge0} y^{2k+1} = y + y^3 + \dots = \frac{y}{1-y^2}$  

##### 各事件的生成函数（乘法规则）  

设$A_{1}$为所有$r$个球中红球为偶数个，蓝球为奇数个的组合的集合。
$A_{2}$为所有$r$个球中白球为偶数个，蓝球为奇数个的组合的集合。
$A_{3}$为所有$r$个球中白球为偶数个，黄球为奇数个的组合的集合。

-$F_{A_1}(y)$（红偶、蓝奇，白黄任意）：  
$$F_{A_1}(y) = \frac{1}{1-y^2} \cdot \frac{y}{1-y^2} \cdot \frac{1}{1-y} \cdot \frac{1}{1-y} = \frac{y}{(1-y)^2(1-y^2)^2}$$
-$F_{A_2}(y)$（白偶、蓝奇，红黄任意）、$F_{A_3}(y)$（白偶、黄奇，红蓝任意）与$F_{A_1}(y)$形式相同，均为：  
$$F_{A_2}(y) = F_{A_3}(y) = \frac{y}{(1-y)^2(1-y^2)^2}$$
##### 交集的生成函数  
-$F_{A_1 \cap A_2}(y)$（红偶、白偶、蓝奇，黄任意）：  
$$F_{12} = \frac{1}{1-y^2} \cdot \frac{1}{1-y^2} \cdot \frac{y}{1-y^2} \cdot \frac{1}{1-y} = \frac{y}{(1-y)(1-y^2)^3}$$
-$F_{A_1 \cap A_3}(y)$（红偶、白偶、蓝奇、黄奇）：  
$$F_{13} = \frac{1}{1-y^2} \cdot \frac{1}{1-y^2} \cdot \frac{y}{1-y^2} \cdot \frac{y}{1-y^2} = \frac{y^2}{(1-y^2)^4}$$
-$F_{A_2 \cap A_3}(y)$（白偶、蓝奇、黄奇，红任意）：  
$$F_{23} = \frac{1}{1-y} \cdot \frac{1}{1-y^2} \cdot \frac{y}{1-y^2} \cdot \frac{y}{1-y^2} = \frac{y^2}{(1-y)(1-y^2)^3}$$
- 三重交集$F_{A_1 \cap A_2 \cap A_3}(y)$与$F_{13}$相同：  
$$F_{123} = \frac{y^2}{(1-y^2)^4}$$
##### 容斥原理合并  
$$a_r = |A_{1} \cup A_{2} \cup A_{3}| = |A_{1}| + |A_{2}| + |A_{3}| - |A_{1} \cap A_{2}| - |A_{1} \cap A_{3}| - |A_{2} \cap A_{3}| + |A_{1} \cap A_{2} \cap A_{3}|$$
则
$$f(y) = F_{A_1} + F_{A_2} + F_{A_3} - (F_{12} + F_{13} + F_{23}) + F_{123}$$
代入化简后得：  
$$\boxed{f(y) = \frac{2y}{(1-y)^4(1+y)^2}}$$
<br>

#### 2. 写出$a_r$的表达式，并计算$r = 23$时的值。

##### 展开生成函数  

利用恒等式拆分：  
$$
\frac{2y}{(1-y)^4(1+y)^2} = \frac{1}{2} \left( \frac{1}{(1-y)^4} - \frac{1}{(1-y^2)^2} \right)
$$
由广义二项式定理 $$(1+x)^a = \sum_{n=0}^\infty \binom{a}{n} x^n \quad (|x| < 1)$$

可得幂级数展开 
$$
\begin{align*}
\displaystyle \frac{1}{(1-y)^4} &= (1 - y)^{-4} = \sum_{n=0}^\infty \binom{-4}{n} y^n \\
&= \sum_{n=0}^\infty \frac{(-4)(-4-1)(-4-2)\cdots(-4 - n + 1)}{n!} y^n \\
&= \sum_{n=0}^{\infty} (-1)^n \cdot \frac{(n + 3)!}{3! \cdot n!} y^n = \sum_{n=0}^\infty \binom{n+3}{3} y^n, \\
\frac{1}{(1-y^2)^2} &= (1 - y^2)^{-2} = \sum_{k=0}^\infty \binom{-2}{k} y^{2k} = \sum_{k=0}^{\infty} (-1)^k \cdot \frac{2 \cdot 3 \cdots (k + 1)}{k!} y^{2k} = \sum_{k=0}^\infty (k+1) y^{2k}.
\end{align*}
$$

##### $a_r$的显式公式  
$$\boxed{a_r = \frac{1}{2}\binom{r+3}{3} - \begin{cases} 
\frac{1}{2}\left( \frac{r}{2} + 1 \right), & r \text{ 为偶数} \\0, & r \text{ 为奇数}
\end{cases}}$$

##### 计算$a_{23}$（$r=23$为奇数，第二项为 0）  
$$a_{23} = \frac{1}{2} \binom{23+3}{3} = \frac{1}{2} \cdot \frac{26 \cdot 25 \cdot 24}{6} = \frac{2600}{2} = \boxed{1300}$$
<br>

##### 或：

由（1），$a_n$是$\displaystyle 2x\cdot \left(\sum_{i=0}^\infty{x^{2i}}\right)^2 \cdot \left(\sum_{i=0}^\infty{x^i}\right)^2$中$x_n$的系数.
先看第一个平方
$$
\begin{matrix}
1 & x^2 & x^4 & x^6 & x^8 & \cdots \\
1 & 1   & 1   & 1   & 1 & \cdots \\
  & 1   & 1   & 1   & 1 & \cdots \\
  &     & 1   & 1   & 1 & \cdots \\ 
1 & 2   & 3   & 4   & 5 & \cdots
\end{matrix}
$$
再看第二个平方
$$\begin{matrix}
1 & x & x^2 & x^3 & x^4 & \cdots \\
1 & 1   & 1   & 1   & 1 & \cdots \\
  & 1   & 1   & 1   & 1 & \cdots \\
  &     & 1   & 1   & 1 & \cdots \\
1 & 2   & 3   & 4   & 5 & \cdots
\end{matrix}
$$
两者相乘
$$\begin{matrix}
1          & x         & x^2        & x^3        & x^4       & \cdots \\
1\times 1  & 1\times 2 & 1\times 3  & 1\times 4  & 1\times 5 & \cdots \\
           &           & 2\times 1  & 2\times 2  & 2\times 3 & \cdots \\
           &           &            &            & 3\times 1 & \cdots \\
\end{matrix}
$$
所以
$$
\begin{aligned}
f(x)&=2x\sum_{i=0}^\infty{\left(\sum_{j=1}^{\lceil (i+1)/2 \rceil}{j(i+1-2(j-1))}\right)x^i}\\
&=\sum_{i=0}^\infty{2\left(\sum_{j=1}^{\lceil (i+1)/2 \rceil}{j(i+1-2(j-1))}\right)x^{i+1}}.
\end{aligned}
$$
现在要求 $x_{23}$ 的系数，令 $i+1=23$，则 $i=22$ ，代入求得 $x_{23} = 1300$。

---

## 7.2 指数型生成函数

---

### 7.6 定理 7.2
设$\{a_n\}$，$\{b_n\}$的指数生成函数分别为$f_e(x)$和$g_e(x)$，则
$$f_e(x) \cdot g_e(x) = \sum_{n = 0}^\infty C_n \frac{x^n}{n!}$$

其中
$$C_n = \sum_{k = 0}^n C(n, k) a_k b_{n - k}$$

##### 证明：

定义指数生成函数
$$f_e(x)=\sum_{k\ge0} a_k\frac{x^k}{k!},\qquad g_e(x)=\sum_{j\ge0} b_j\frac{x^j}{j!}.$$

两式相乘：
$$f_e(x)g_e(x) = \sum_{k\ge0}\sum_{j\ge0} a_k b_{j} \frac{x^{k+j}}{k!j!}$$

把双和按总指数 $n=k+j$ 合并：
$$f_e(x)g_e(x)=\sum_{n\ge0}\left(\sum_{k=0}^n a_k b_{n-k}\frac{1}{k!(n-k)!}\right)x^n$$

把每一项写成 $\dfrac{C_n}{n!}x^n$ 的形式，比较系数得
$$\frac{C_n}{n!}=\sum_{k=0}^n \frac{a_k b_{n-k}}{k!(n-k)!}$$

因此
$$C_n=n!\sum_{k=0}^n \frac{a_k b_{n-k}}{k!(n-k)!} = \sum_{k=0}^n \binom{n}{k} a_k b_{n-k}.$$

代入回去就得到
$$f_e(x)g_e(x)=\sum_{n\ge0}C_n\frac{x^n}{n!}$$

正是定理要证明的结论。


---

### ✅7.7 有 5 个数字，其中有两个 1，两个 2 和一个 3。问这 5 个数字能组成多少不同的 4 位数？

#### 方法一：指数型生成函数

三种符号的 EGF（**注意：多重集的组合问题用幂级数型生成函数，多重集的排列问题用指数型生成函数**）:
$$E_1(x)=1+x+\frac{x^2}{2!},\qquad E_2(x)=1+x+\frac{x^2}{2!},\qquad E_3(x)=1+x.$$
因此总体 EGF：
$$
F(x)=\bigg(1+x+\frac{x^2}{2}\bigg)^2(1+x).
$$

我们要求长度为 $4$ 的不同序列数 $a_4 = 4!\cdot [x^4]F(x)$，记 $A = 1+x+\frac{x^2}{2}$.

计算系数，先展开
$$\left(1+x+\frac{x^2}{2}\right)^2
=1+2x+2x^2+1x^3+\frac{1}{4}x^4,$$

再乘以$（1+x)$，得到 $F(x)$ 的 $x^4$ 系数
$$
[x^4]F(x) = [x^4]\big(A^2(1+x)\big) = [x^4]A^2 + [x^3]A^2 = \frac{1}{4} + 1 = \frac{5}{4}.
$$

于是
$$
a_4 = 4!\cdot \frac{5}{4} = 24\cdot\frac{5}{4}=30.
$$
#### 方法二：计算每种组合的排列数

情况 A：1,1,2,3   $\quad \frac{4!}{2!}= \frac{24}{2} = 12$

情况 B：1,2,2,3   $\quad \frac{4!}{2!}=12$

情况 C：1,1,2,2   $\quad \frac{4!}{2!2!} = \frac{24}{4}=6$

总和： $12 + 12 + 6 = 30$


---

### ✅7.8 在由$A = \{0, 1, 2, 3\}$中的数生成的 $r$-位数字序列（0 可在首位）中，0 可出现任意次，而 1，2，3 至少出现 1 次。求$A$的 $r$-位数字序列的个数。

#### 方法一：指数型生成函数

原问题相当于求解 $\displaystyle \left(\sum_{i=1}^\infty{\frac{x^i}{i!}}\right)^3 \cdot \left(\sum_{i=0}^\infty{\frac{x^i}{i!}}\right)$ 中 $\displaystyle \frac{x^r}{r!}$ 的系数.
$$
\begin{aligned}
\left(\sum_{i=1}^\infty{\frac{x^i}{i!}}\right)^3 \cdot \left(\sum_{i=0}^\infty{\frac{x^i}{i!}}\right)
&=e^x\cdot (e^x-1)^3 \\
&=e^x\cdot (e^{3x} - 3e^{2x} + 3e^{x} - 1) \\
&=e^{4x} - 3e^{3x} + 3e^{2x} - e^x \\
&=\sum_{i=0}^\infty{(4^i - 3^{i+1} + 3\cdot 2^i - 1)\frac{x^i}{i!}},
\end{aligned}
$$

所以 $a_r=4^r-3\cdot 3^r+3\cdot 2^r-1.$


#### 方法二：容斥原理

全集中长度为$r$的所有序列数为$4^r$。

用容斥法减去缺少某些必需符号的序列：
- 缺少某一个（例如缺 1）的序列数为$3^r$（从剩下 3 个符号取序列）；
- 缺少两个数字的序列为 $2^r$；
- 缺少 1、2、3 三个中全部三个显然只剩下 0，一种序列即$1^r=1$。

由容斥公式：
$$
\text{所求数}=4^r-3\cdot 3^r+3\cdot 2^r-1.
$$

---

### 7.9 设 $f(y) = \sum_{r\ge0}a_r y^r = (1 + y)^{2n} + y(1 + y)^{2n - 1} + \cdots + y^r(1 + y)^{2n - r} + \cdots + y^n(1 + y)^n$

#### 1. 证明 $a_r = \begin{cases} C(2n + 1, r) & 0 \leqslant r \leqslant n \\ C(2n + 1, r) - C(n, r - n - 1) & n + 1 \leqslant r \leqslant 2n + 1 \\ 0 & 其他 \end{cases}$

化简：
$$
\begin{align*}
f(y) &= (1 + y)^n \left[(1 + y)^n + y(1 + y)^{n - 1} + \dots + y^r(1 + y)^{n - r} + \dots + y^n\right] \\
&= (1 + y)^n \left[\frac{(1 + y)^{n + 1} - y^{n + 1}}{(1 + y) - y}\right] \\
&= (1 + y)^{2n + 1} - y^{n + 1}(1 + y)^n
\end{align*}
$$
因为 $y^{n + 1}(1 + y)^n$ 中每一项次数均不小于 $n + 1$，所以：

- 当 $0 \leq r \leq n$ 时，$a_r$ 仅来自于$（1 + y)^{2n + 1}$，$a_r = \mathrm{C}(2n + 1, r)$；
- 当 $n + 1 \leq r \leq 2n + 1$ 时，$a_r = \mathrm{C}(2n + 1, r) - \mathrm{C}(n, r - n - 1)$；
- 当 $r \geq 2n + 1$ 时，$a_r = 0$。


#### 2. 求下式的和 $C(2n, n) + C(2n - 1, n - 1) + \cdots + C(2n - i, n - i) + \cdots + C(n, 0)$

记 $$S = \binom{2n}{n}+\binom{2n-1}{n-1}+\cdots+\binom{n}{0}$$

##### 方法一

比较幂次可见
$$
[y^n]f(y)=\sum_{r=0}^n [y^{n-r}](1+y)^{2n-r}=\sum_{r=0}^n \binom{2n-r}{n-r}=S.
$$
但我们已在第 1 问中化简出一个更简洁的表达式：
$$
f(y)=(1+y)^{2n+1}-y^{n+1}(1+y)^n.
$$
因此 $y^n$ 的系数由第一项贡献，第二项由于至少含 $y^{n+1}$ 不影响：
$$
[y^n]f(y)=[y^n](1+y)^{2n+1}=\binom{2n+1}{n}.
$$
##### 方法二

利用 **Hockey-stick identity** $$\displaystyle \sum_{k=r}^{n} \binom{k}{r} = \binom{n+1}{r+1}\quad \text{ 或 }\quad \sum_{k=0}^m C(n+k,k) = C(n+m+1, m)\ \text{(定理6.8(8))}$$

---

## 7.3 递推关系

---

### ✅7.10 解下述递推关系

#### 1.$a_r - 7a_{r - 1} + 10a_{r - 2} = 3^r$；这里$a_0 = 0$，$a_1 = 1$。

特征方程$t^2 - 7t + 10 = 0$有根$t = 5, 2$。齐次解$a_r^{(h)} = A5^r + B2^r$。

对非齐次项$3^r$试特解$C3^r$。代入可得
$$
C3^r - 7C3^{r-1} + 10C3^{r-2} = -2C3^{r-2} = 3^r
$$

从而$-2C = 9 \Rightarrow C = -\frac{9}{2}$。因此通解
$$
a_r = A5^r + B2^r - \frac{9}{2}3^r.
$$

用初值求$A, B$：

$r = 0$得$A + B - \frac{9}{2} = 0 \Rightarrow A + B = \frac{9}{2}$。

$r = 1$得$5A + 2B - \frac{9}{2} \cdot 3 = 1 \Rightarrow 5A + 2B = \frac{29}{2}$。

解得
$$
A = \frac{11}{6}, \qquad B = \frac{8}{3}.
$$

故
$$
\boxed{a_r = \frac{11}{6}5^r + \frac{8}{3}2^r - \frac{9}{2}3^r.}
$$
<br>

#### 2. $a_r - 2a_{r - 1} + 2a_{r - 2} - a_{r - 3} = 0$；这里$a_0 = 0$，$a_1 = 1$，$a_2 = 1$。

该齐次递推关系对应的**特征方程**是：
$$
t^3 - 2t^2 + 2t - 1 = 0.
$$
特征多项式$t^3 - 2t^2 + 2t - 1 = (t - 1)(t^2 - t + 1)$。

二次方程 $t^2 - t + 1 = 0$ 的解为：
$$
t = \frac{1 \pm \sqrt{1 - 4}}{2} = \frac{1 \pm \sqrt{-3}}{2} = \frac{1 \pm i\sqrt{3}}{2} = e^{\pm i\pi/3}.
$$
三个特征根：
$$
\lambda_1 = 1, \quad \lambda_2 = e^{i\pi/3}, \quad \lambda_3 = e^{-i\pi/3}
$$
所以**通解**：
$$
a_r = A \cdot 1^r + B e^{i\pi r/3} + C e^{-i\pi r/3}
$$
利用欧拉公式 $e^{i\theta} = \cos\theta + i\sin\theta$，可写成实数形式：
$$
a_r = A + B' \cos\left(\frac{\pi r}{3}\right) + C' \sin\left(\frac{\pi r}{3}\right)
$$
其中 $B' = B + C$，$C' = i(B - C)$ 为实数（因为 $a_r$ 是实数）。

**初始条件**：
$$
\begin{align}
a_0 = 0&:& \quad &A + B' \cos 0 + C' \sin 0 = A + B' = 0 \quad \Rightarrow \quad B' = -A\\
a_1 = 1&:& \quad &A + B' \cos\frac{\pi}{3} + C' \sin\frac{\pi}{3} = A + \frac{B'}{2} + \frac{\sqrt{3}}{2}C' = 1\\
a_2 = 1&:& \quad &A + B' \cos\frac{2\pi}{3} + C' \sin\frac{2\pi}{3} = A - \frac{B'}{2} + \frac{\sqrt{3}}{2}C' = 1\\
(1)代入(2)&:& \quad &\frac{A}{2} + \frac{\sqrt{3}}{2}C' = 1 \quad \Rightarrow \quad A + \sqrt{3} C' = 2\\
(1)代入(3)&:& \quad &\frac{3A}{2} + \frac{\sqrt{3}}{2}C' = 1 \quad \Rightarrow \quad 3A + \sqrt{3} C' = 2\\
(5)-(4)&:& \quad &2A = 0 \quad \Rightarrow \quad A = 0, \quad 由(1)有B' = -A = 0\\
(6)代入(4)&:& \quad &0 + \sqrt{3} C' = 2 \quad \Rightarrow \quad C' = \frac{2}{\sqrt{3}}
\end{align}
$$

**最终通解**:
$$
\boxed{a_r = \frac{2}{\sqrt{3}} \sin\left(\frac{\pi r}{3}\right)}
$$

##### 或：

该递推关系的通解可写成
$$
\displaystyle a_r=c_1\cdot 1^n + c_2\cdot \left(\frac{1+\sqrt{3}i}{2}\right)^r + c_3\cdot \left(\frac{1-\sqrt{3}i}{2}\right)^r,
$$

代入 $a_0=0$，$a_1=1$，$a_2=1$，求得 $\displaystyle c_1=0$，$\displaystyle c_2=-\frac{i}{\sqrt{3}}$，$\displaystyle c_3=\frac{i}{\sqrt{3}}$.

所以
$$
\displaystyle a_r=-\frac{i}{\sqrt{3}}\cdot \left(\frac{1+\sqrt{3}i}{2}\right)^r + \frac{i}{\sqrt{3}}\cdot \left(\frac{1-\sqrt{3}i}{2}\right)^r.
$$

<br>

#### 3. $a_r - 7a_{r - 1} + 10a_{r - 2} = f(r)$；这里$a_0 = a_1 = 0$，并且  $f(r) = \begin{cases}  1 & r = 2 \\ 0 & 其他 \end{cases}$

##### **齐次方程**：
$$
a_r - 7a_{r-1} + 10a_{r-2} = 0
$$
特征方程：
$$
\lambda^2 - 7\lambda + 10 = 0 \quad\Rightarrow\quad (\lambda - 2)(\lambda - 5) = 0 \quad\Rightarrow\quad \lambda = 2, \quad \lambda = 5
$$
齐次通解：
$$
a_r^{(h)} = A \cdot 2^r + B \cdot 5^r
$$
**非齐次项处理**：$f(r)$只在$r=2$时为 1，其余为 0。  我们可以直接递推求出前几项，然后确定齐次解系数。

递推公式：
$$
a_r = 7a_{r-1} - 10a_{r-2} + f(r)
$$
已知：
$$
\begin{align}
a_0 &=& &0, \quad a_1 = 0\\
a_2 &=& &7a_1 - 10a_0 + f(2) = 0 - 0 + 1 = 1\\
a_3 &=& &7a_2 - 10a_1 + f(3) = 7\cdot 1 - 0 + 0 = 7\\
a_4 &=& &7a_3 - 10a_2 + 0 = 7\cdot 7 - 10\cdot 1 = 49 - 10 = 39\\
a_5 &=& &7a_4 - 10a_3 = 7\cdot 39 - 10\cdot 7 = 273 - 70 = 203
\end{align}
$$

##### **确定通解（分段法）**：

原递推是对冲激序列$\delta_{r2}$的响应。对$r \ge 3$递推为齐次方程：
$$
a_r - 7a_{r-1} + 10a_{r-2} = 0 \quad \text{当 } r \ge 3
$$

所以当$r \ge 3$时，解为齐次形式：
$$
a_r = A\cdot 2^r + B\cdot 5^r
$$

我们可以用$a_1, a_2$作为初始条件来定系数，因为从$r \ge 3$开始，递推是齐次的（但$r=2$时非齐次项已计入$a_2$的值）。

利用$a_1 = 0$和$a_2 = 1$求$A, B$：
$$
\begin{align}
a_1 &=& &2A + 5B = 0 \quad&\Rightarrow&\quad &2A + 5B = 0 \quad\\
a_2 &=& &4A + 25B = 1 \quad&\Rightarrow&\quad &4A + 25B = 1 \quad
\end{align}
$$

由 (13) 得$A = -\frac{5}{2}B$，代入 (14)：
$$
4\left(-\frac{5}{2}B\right) + 25B = -10B + 25B = 15B = 1\\
B = \frac{1}{15}, \quad A = -\frac{5}{2} \cdot \frac{1}{15} = -\frac{1}{6}
$$

所以：
$$
a_r = -\frac{1}{6} \cdot 2^r + \frac{1}{15} \cdot 5^r, \quad r \ge 3
$$

##### **验证**：
-$r=1$：$a_1 = -\frac{1}{6} \cdot 2 + \frac{1}{15} \cdot 5 = -\frac{1}{3} + \frac{1}{3} = 0$✅  
-$r=2$：$a_2 = -\frac{1}{6} \cdot 4 + \frac{1}{15} \cdot 25 = -\frac{2}{3} + \frac{5}{3} = 1$✅  
-$r=3$：$a_3 = -\frac{1}{6} \cdot 8 + \frac{1}{15} \cdot 125 = -\frac{4}{3} + \frac{25}{3} = 7$✅（与递推一致）  
-$r=0$时公式不适用，因为$a_0 = 0$是初始条件，公式给出$-\frac{1}{6} + \frac{1}{15} = -\frac{1}{10} \neq 0$。

##### **最终答案**：
$$
\boxed{a_r = -\frac{1}{6} \cdot 2^r + \frac{1}{15} \cdot 5^r \quad (r \ge 1), \quad a_0 = 0}
$$

---

### 7.11 求例 7.6 的解（斐波那契数列的通项）

**例 7.6** 13 世纪初意大利数学家 Fibonacci 研究过著名的兔子繁殖数目问题。设一对雌雄小兔刚满 2 个月时，便可繁殖出一雌一雄一对小兔。以后每隔 1 个月生一雌一雄一对小兔。由一对刚出生的小兔开始饲养到第$n$个月，有多少对兔子？

**解**：设第$n$个月有$F_n$对兔子，它由两部分组成：

1. 新生出的小兔，其数目等于能生小兔的大兔对数目，由于小兔满两个月才能繁殖，故数目为第$(n - 2)$个月时的兔对数目，即为$F_{n - 2}$。

2. 原有小兔，其数目等于上月（即第$n - 1$个月）的兔对数目，即为$F_{n - 1}$。因此可建立如下的递推关系：
$$ F_n = F_{n - 2} + F_{n - 1} $$

并有初始条件：$F_1 = F_2 = 1$。即这是一个带有初值的递推关系。满足这种递推关系的数列称为Fibonacci数列。

对应的**特征方程**为：
$$
t^2 - t - 1 = 0
$$
利用求根公式解出特征根：
$$
\alpha = \frac{1 + \sqrt{5}}{2}, \quad \beta = \frac{1 - \sqrt{5}}{2}.
$$
齐次线性递推的通解为：
$$
F_n = A \alpha^n + B \beta^n
$$
利用初始条件求常数$A $、$ B$。

当$n = 0$：
$$
F_0 = A + B = 0 \quad \Rightarrow \quad B = -A.
$$
当$n = 1$：
$$
F_1 = A\alpha + B\beta = 1.
$$
代入$B = -A$：$A(\alpha - \beta) = 1.$ 由于$\alpha - \beta = \sqrt{5}$，得到：
$$
A = \frac{1}{\sqrt{5}}, \quad B = -\frac{1}{\sqrt{5}}.
$$
**得到通项公式（Binet 公式）**：
$$
\boxed{
F_n = \frac{1}{\sqrt{5}}\left(\alpha^n - \beta^n\right)
= \frac{1}{\sqrt{5}}\left[\left(\frac{1+\sqrt{5}}{2}\right)^n - \left(\frac{1-\sqrt{5}}{2}\right)^n\right].
}
$$

---

### ⭐7.12 求由$A = \{0, 1, 2, 3\}$中的数构成的（$n$位数的首位数字不能是0）

#### 1. 具有偶数个 $0$ 的$n$位数的个数。

我们把“首位不是 0”的条件单独处理：首位只能取 $1,2,3$，共 $3$ 种情况；而首位确定后，其余 $n−1$ 位可以是 $0,1,2,3$。

于是我们只需要知道：长度为 $m=n−1$ 的序列（首位允许为 0）中，偶数个 $0$ 的个数。

设 $a_n$ 表示由数字 $A = \{0,1,2,3\}$ 组成的 $n$ 位数中，0 出现偶数次的个数。

##### **方法一：递推**

设：
- $a_n$ = 长度为 $n$，0 出现偶数次（包括 0 次）的字符串个数。
- $b_n$ = 长度为 $n$，0 出现奇数次的字符串个数。

从 $a_{n-1}$（偶数个 0）：
- 加一个非 0 数字（3 种） → 仍偶数个 0：贡献 $3 a_{n-1}$ 到 $a_n$
- 加一个 0（1 种） → 变成奇数个 0：贡献 $1 a_{n-1}$ 到 $b_n$

从 $b_{n-1}$（奇数个 0）：
- 加一个非 0 数字（3 种） → 仍奇数个 0：贡献 $3 b_{n-1}$ 到 $b_n$
- 加一个 0（1 种） → 变成偶数个 0：贡献 $1 b_{n-1}$ 到 $a_n$

所以：
$$
a_n = 3 a_{n-1} + 1 \cdot b_{n-1}\\
b_n = 1 \cdot a_{n-1} + 3 b_{n-1}
$$

初始条件：$a_1$ = 偶数个 0（即没有 0 或 2 个 0 等，但长度 1 时偶数个 0 就是数字 1,2,3 共 3 种），$b_1$ = 奇数个 0（即数字 0 共 1 种）。

所以：
$$
a_1 = 3, \quad b_1 = 1
$$

由对称性或观察：$a_n + b_n = 4^n$（所有字符串数），并且 $a_n - b_n$ 满足：
$$
a_n - b_n = (3a_{n-1} + b_{n-1}) - (a_{n-1} + 3b_{n-1}) = 2a_{n-1} - 2b_{n-1} = 2(a_{n-1} - b_{n-1})
$$

所以：
$$
a_n - b_n = 2^{n-1} (a_1 - b_1) = 2^{n-1} \cdot (3 - 1) = 2^n
$$

解得：
$$
a_n = \frac{4^n + 2^n}{2}, \quad b_n = \frac{4^n - 2^n}{2}
$$

因此，偶数个 0 的 $n$ 位字符串数（首位允许为 0）为 $\frac{4^n + 2^n}{2}$。

所求首位不能是 0 的 $n$ 位数的个数为：
$$
\boxed{\frac{3}{2}(4^{n-1} + 2^{n-1})}
$$

##### **方法二：指数型生成函数**

若该数码有偶数个，则生成函数为： $$1 + \frac{x^2}{2!} + \frac{x^4}{4!} + \cdots = \sum_{k=0}^{\infty} \frac{x^{2k}}{(2k)!} = \frac{e^x + e^{-x}}{2}$$

否则，生成函数为：$$1 + x + \frac{x^2}{2!} + \frac{x^3}{3!} + \cdots = \sum_{k=0}^{\infty} \frac{x^{k}}{k!} = e^x$$

设 $a'_n$ 是长度为 $n$ 的，可以有前导 $0$ 的，$0$ 出现偶数次的 $n$ 位数的个数。令 $a'_0 = 1$，则：
$$A(x) = \Big(\frac{e^x + e^{-x}}{2}\Big) (e^x)^3 = \frac{e^{4x} + e^{2x}}{2} = \sum_{k=0}^{\infty} \frac{4^k + 2^k}{2} \cdot \frac{x^k}{k!}$$

故 $$a'_n = \frac{4^n + 2^n}{2}.$$

所求首位不能是 0 的 $n$ 位数的个数为：
$$
\boxed{a_n = 3a'_{n-1} = \frac{3}{2}(4^{n-1} + 2^{n-1})}
$$

<br>

#### 2. 具有偶数个 0 和偶数个 1 的 $n$ 位数的个数。

利用**指数型生成函数**。设 $b'_n$ 是长度为 $n$ 的，可以有前导 0 的，0 和 1 出现次数都为偶数次的 $n$ 位数的个数。令 $b'_0 = 1$，则：
$$B(x) = \Big(\frac{e^x + e^{-x}}{2}\Big)^2 (e^x)^2 = \frac{e^{4x} + e^{2x} + 1}{4} = \sum_{k=0}^{\infty} \frac{4^k + 2 \times 2^k + 0^k}{4} \cdot \frac{x^k}{k!}$$

故 $$b'_n = \frac{4^n + 2^{n+1} + 0^n}{4}.$$

所求首位不能是 0 的 $n$ 位数，有以下两种情形：

- 后 $n-1$ 位数有偶数个 0 和 1，在第一位加 2 或 3。
- 后 $n-1$ 位数有偶数个 0 和奇数个 1（相当于从偶数个 0 而不限制 1 的次数中，减去偶数个 0 和偶数个 1 的情况），在第一位加 1。

其个数为：
$$
\begin{align*}
b_n &= 2b'_{n-1} + (a'_{n-1} - b'_{n-1}) = a'_{n-1} + b'_{n-1} \\
&= \frac{4^{n-1} + 2^{n-1}}{2} + \frac{4^{n-1} + 2^{n} + 0^{n-1}}{4} \\
&= \begin{cases} 2,\ n = 1\\ 3 \times 4^{n-2} + 2^{n-1},\ n \geq 2 \end{cases}
\end{align*}
$$

---

### 7.13 核反应器问题（两类粒子按给定分裂规则）
在一个核反应器内有两类粒子，在每一秒钟里，1 个$\alpha$粒子分裂为 3 个$\beta$粒子，1 个$\beta$粒子分裂为 1 个$\alpha$粒子和 2 个$\beta$粒子。如果在时间$t = 0$时，反应器里只有 1 个$\alpha$粒子，则在时间$t = 100$时，总共有多少粒子？

#### 方法一：线性变换

##### 每秒的线性变换（递推关系的矩阵形式）

根据分裂规则，考虑从 $t$ 到 $t+1$ 的变化：

$$
\begin{align*}
\alpha_{t+1} &= 0 \cdot \alpha_t + 1 \cdot \beta_t = \beta_t\\
\beta_{t+1} &= 3 \cdot \alpha_t + 2 \cdot \beta_t
\end{align*}
$$

若状态向量为$v_t = (\alpha_t, \beta_t)^T$，则
$$
v_{t+1} = M v_t, \qquad M = \begin{pmatrix} 0 & 1 \\ 3 & 2 \end{pmatrix}.
$$

初始$v_0 = (1, 0)^T$。

##### **对角化 $M$**

求特征值：$\det(M - \lambda I) = \lambda^2 - 2\lambda - 3 = 0$， 解得 $\lambda = 3, \quad \lambda = -1$。

- 对于 $\lambda_1 = 3$，解$（M - 3I)x = 0$：
$$
\begin{pmatrix} -3 & 1 \\ 3 & -1 \end{pmatrix} \to x_1 = \begin{pmatrix} 1 \\ 3 \end{pmatrix}
$$

- 对于 $\lambda_2 = -1$，解$（M + I)x = 0$：
$$
\begin{pmatrix} 1 & 1 \\ 3 & 3 \end{pmatrix} \to x_2 = \begin{pmatrix} 1 \\ -1 \end{pmatrix}
$$


所以$M$对角化，特征值为$3$和$-1$，对应特征向量可选为$[1, 3]^T$（对应 3）和$[-1, 1]^T$（对应$-1 $）。

##### **用特征向量表示初始向量**

设：
$$
v_0 = c_1 \begin{pmatrix} 1 \\ 3 \end{pmatrix} + c_2 \begin{pmatrix} 1 \\ -1 \end{pmatrix}
$$

即：
$$
\begin{cases}
c_1 + c_2 = 1 \\
3c_1 - c_2 = 0
\end{cases}
$$

解得：
$$
c_1 = \frac14, \quad c_2 = \frac34
$$

因为 $M x_1 = 3 x_1$，$M x_2 = (-1) x_2$，所以：
$$
v_t = M^t v_0 = c_1 3^t x_1 + c_2 (-1)^t x_2
$$

代入得到时间演化关系：
$$
v_t = \frac14 \cdot 3^t \begin{pmatrix} 1 \\ 3 \end{pmatrix} + \frac34 \cdot (-1)^t \begin{pmatrix} 1 \\ -1 \end{pmatrix}
$$

##### 总粒子数

粒子总数为两类之和。求和得到
$$
\text{总数} = \frac{1}{4}3^t(1 + 3) + \frac{3}{4}(-1)^t(1 - 1) = 3^t.
$$

因此在$t = 100$时总粒子数为
$$
\boxed{3^{100}.}
$$



#### 方法二：

由递推关系式得 $b_t=3a_{t-1}+2b_{t-1}=3b_{t-2}+2b_{t-1},\ t\geq 2$。

特征方程：$x^2-2x-3=0$，解得特征根 $x_1=3$，$x_2=-1$，其通项可以写成 $b_t=c_13^t+c_2(-1)^t$.

`Solve[0==c1+c2 && 3==3c1-c2, {c1, c2}]`

代入初始条件计算得 $\displaystyle b_t=\frac{3}{4}\cdot 3^t-\frac{3}{4}\cdot (-1)^{t}$.

所以
$$
\begin{cases}
a_t=\dfrac{1}{4}\cdot 3^t - \dfrac{3}{4}\cdot (-1)^{t-1}\\
b_t=\dfrac{3}{4}\cdot 3^t-\dfrac{3}{4}\cdot (-1)^{t}
\end{cases}
,\ t\geq 0.
$$

#### 方法三：

$$
\begin{align*}
\alpha_{t+1} &= 0 \cdot \alpha_t + 1 \cdot \beta_t = \beta_t\\
\beta_{t+1} &= 3 \cdot \alpha_t + 2 \cdot \beta_t
\end{align*}
$$

两式相加得到总的粒子数 $a_t + b_t$ 的递推关系
$$a_{t+1} + b_{t+1} = 3 \cdot (a_t + b_t)$$

已知 $a_0 + b_0 = 1$，所以 $$a_t + b_t = 3^t$$

因此在$t = 100$时总粒子数为
$$
\boxed{3^{100}.}
$$

---

### 7.14 用生成函数的方法解下列递推关系。

#### 1.$a_n = 5a_{n - 1} - 6a_{n - 2} (n \geqslant 2)$，这里$a_0 = 1$，$a_1 = -2$。

设 $a_n$ 的生成函数 $\displaystyle f(x)=\sum_{i=0}^\infty{a_ix^i}$.

$$
\begin{matrix}
f(x) &= &a_0 &+ &a_1x &+ &a_2x^2 &+ &a_3x^3 &+ &a_4x^4 &+ &\cdots\\
-5xf(x) &= & & &-5a_0x &+ &-5a_1x^2 &+ &-5a_2x^3 &+ &-5a_3x^4 &+ &\cdots\\
+6x^2f(x) &= & & & & &6a_0x^2 &+ &6a_1x^3 &+ &6a_2x^4 &+ &\cdots\\
\end{matrix}
$$

将上式加和得
$$
\begin{aligned}
(1-5x+6x^2)f(x) &= 1-7x\\
f(x) &= \frac{1-7x}{(1-3x)(1-2x)}\\
f(x) &= \frac{A}{1-3x} + \frac{B}{1-2x}
\end{aligned}
$$

代入初始条件$a_0 = 1$，$a_1 = -2$计算得
$$
f(x) = \frac{-4}{1-3x} + \frac{5}{1-2x} = -4\sum_{i=0}^\infty{3^ix^i} + 5\sum_{i=0}^\infty{2^ix^i}
$$

所以
$$
a_n=-4\cdot 3^n + 5\cdot 2^n.
$$

<br>

#### 2.$a_n = \sum_{k = 1}^{n - 1} a_k a_{n - k} (n \geqslant 2)$，这里$a_1 = 1$。

设$a_n$的生成函数$\displaystyle f(x)=\sum_{i=1}^\infty{a_ix^i}$，$a_n$就是$x^n$的系数，则

##### 思路一

$$
\begin{align*}
f(x) \cdot f(x) &= \left(\sum_{i=1}^\infty{a_ix^i}\right) \cdot \left(\sum_{i=1}^\infty{a_ix^i}\right)\\
&= a_1^2 x^2 + (a_1 a_2 + a_2 a_1) x^3 + (a_1 a_3 + a_2 a_2 + a_3 a_1) x^4 + (a_1 a_4 + a_2 a_3 + a_3 a_2 + a_4 a_1) x^5 + \cdots \\
&= a_2 x^2 + a_3 x^3 + a_4 x^4 + a_5 x^5 + \cdots \\
&= f(x) - x
\end{align*}
$$

令 $\displaystyle y = f(x) = \sum_{i=1}^\infty{a_ix^i}$，则有 $y^2 = y - x$，即
$$
y^2 - y + x = 0,
$$

解得 $\displaystyle y=\frac{1\pm\sqrt{1-4x}}{2}$。

##### 思路二

$$
\begin{matrix}
f(x) &= &a_1x &+ &a_2x^2 &+ &a_3x^3 &+ &a_4x^4 &+ &a_5x^5 &+ &\cdots\\
-a_1xf(x) &= & & &-2a_1a_1x &+ &-a_1a_2x^3 &+ &-a_1a_3x^4 &+ &-a_1a_4x^5 &+ &\cdots\\
-a_2x^2f(x) &= & & & & &-a_2a_1x^3 &+ &-a_2a_2x^4 &+ &-a_2a_3x^5 &+ &\cdots\\
\cdots
\end{matrix}
$$

$$
(1-f(x))f(x)=a_1x=x \\
f^2(x)-f(x)+x=0
$$

$$f(x)=\frac{1\pm\sqrt{1-4x}}{2}.$$

注意到当 $x\rightarrow 0$ 时，$f(x)\rightarrow 0$，所以 $\displaystyle f(x) = y = \frac{1-\sqrt{1-4x}}{2}$.

接下来展开上式，当 $|x| < \frac{1}{4}$ 时有：
$$
\begin{aligned}
f(x)&=\frac{1-\sqrt{1-4x}}{2}\\
&=\frac{1}{2}-\frac{1}{2}(1-4x)^{1/2}\\
&=\frac{1}{2}-\frac{1}{2}\left(1+\sum_{i=1}^\infty{{\frac{1}{2} \choose i}(-4x)^i}\right)\\
&=-\frac{1}{2}\left(\sum_{i=1}^\infty{{\frac{1}{2} \choose i}(-4x)^i}\right)\\
&=-\frac{1}{2}\left(\sum_{i=1}^\infty{\frac{\frac{1}{2}\cdot \frac{-1}{2}\cdot \frac{-3}{2}\cdot \cdots \cdot \frac{3-2i}{2}}{i!}(-4x)^i}\right)\\
&=\frac{1}{2}\left(\sum_{i=1}^\infty{\frac{\frac{1}{2}\cdot \frac{1}{2}\cdot \frac{3}{2}\cdot \cdots \cdot \frac{2i-3}{2}}{i!}(4x)^i}\right)\\
&=\frac{1}{2}\left(\sum_{i=1}^\infty{\frac{1\cdot 1\cdot 3\cdot \cdots \cdot (2i-3)}{i!}(2x)^i}\right)\\
&=\sum_{i=1}^\infty{\frac{1\cdot 1\cdot 3\cdot \cdots \cdot 2i-3}{i!}\cdot
\frac{2(i-1)\cdot 2(i-2)\cdot \cdots \cdot 2}{(i-1)\cdot (i-2)\cdot \cdots \cdot 1}x^i}\\
&=\sum_{i=1}^\infty{\frac{(2i-2)!}{i!(i-1)!}x^i}\\
&=\sum_{i=1}^\infty{{2i-2 \choose i-1}\cdot \frac{1}{i}x^i}
\end{aligned}
$$

所以，$\displaystyle a_n=\frac{1}{n}{2n-2 \choose n-1},n\geq 1$. 这个数又叫**卡特兰数**（Catalan numbers）.

<br>

#### 3.$a_n = 2a_{n - 1} + 2a_{n - 2}$，这里$a_1 = 3$，$a_2 = 8$。

设$a_n$的生成函数$\displaystyle f(x)=\sum_{i=0}^\infty{a_ix^i}$.

$$
\begin{matrix}
f(x) &= &a_0 &+ &a_1x &+ &a_2x^2 &+ &a_3x^3 &+ &a_4x^4 &+ &\cdots\\
-2xf(x) &= & & &-2a_0x &+ &-2a_1x^2 &+ &-2a_2x^3 &+ &-2a_3x^4 &+ &\cdots\\
-2x^2f(x) &= & & & & &-2a_0x^2 &+ &-2a_1x^3 &+ &-2a_2x^4 &+ &\cdots\\
\end{matrix}
$$

将上式加和得
$$
(1-2x-2x^2)f(x) = 3+2x\\
f(x) = \frac{C}{1-Ax} + \frac{D}{1-Bx}
$$

特征多项式（分母对应）为
$$
1 - 2x - 2x^2 = (1 - r_1 x)(1 - r_2 x),
$$

其中 $r_1,r_2$ 是二次方程 $t^2 - 2t - 2 = 0$ 的根：
$$
r_{1,2} = 1 \pm \sqrt{3}.
$$

因此可以用部分分式表示
$$
f(x) = \frac{3 + 2x}{(1 - r_1 x)(1 - r_2 x)}
= \frac{C}{1 - r_1 x} + \frac{D}{1 - r_2 x} = \frac{C}{1-(1-\sqrt{3})x} + \frac{D}{1-(1+\sqrt{3})x}.
$$

我们要解出 $C$ 与 $D$，把两边通分、比较多项式系数：
$$
3 + 2x = C(1 - r_2 x) + D(1 - r_1 x)
= (C + D) - (C r_2 + D r_1)x.
$$

比较常数项与 $x$ 项，得到
$$
C = \frac{9 + 5\sqrt{3}}{6},\quad
D = \frac{9 - 5\sqrt{3}}{6}.
$$

代入后利用几何级数展开：
$$
f(x) = \frac{1}{6}(9-5\sqrt{3})\sum_{i=0}^\infty{(1-\sqrt{3})^ix^i} + \frac{1}{6}(9+5\sqrt{3})\sum_{i=0}^\infty{(1+\sqrt{3})^ix^i}
$$

所以
$$
a_n=\frac{1}{6}(9-5\sqrt{3})\cdot (1-\sqrt{3})^n + \frac{1}{6}(9+5\sqrt{3})\cdot (1+\sqrt{3})^n
$$

---

### 7.15 平面上有$n$条直线，任意两条不平行，任意三条不交于一点。

#### (1) 这$n$条直线共有多少个交点？

设这$n$条直线共有$a_n$个交点。

第$n$条直线交于$n-1$条直线会多产生$n-1$个交点，
则$a_n=a_{n-1}+n-1$，$a_0=a_1=0$，$a_2=1$，不难求得
$$a_n=\frac{n(n-1)}{2}.$$

#### (2) 这些直线把平面分割成多少个不相交的区域？

设这$n$条直线共把平面分割成$b_n$个不相交的区域。
第$n$条直线交于$n-1$条直线会穿过原来的$n$个区域（被$n-1$条直线分成了$n$段，每段分割一个原有的区域），那么就会多出$n$个区域。

所以$b_n=b_{n-1}+n$，$b_0=1$，不难求得
$$b_n=\frac{n(n+1)}{2}+1.$$
