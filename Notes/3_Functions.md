# 第3章 函数

> 本章内容较为简单，大家在中学阶段或者在大一年级学习高等数学时就很熟悉，故仅列举重要的定义。

## 3.1 函数的基本概念

#### 定义3.1

设$A$和$B$是两个任意集合，$f$是从$A$到$B$的二元关系。若$f$具有如下性质：
(1) $f$的定义域$\text{Dom} f = A$；
(2) 如果$(a, b), (a, b') \in f$，则$b = b'$。
则称关系$f$是从$A$到$B$的**函数**，记为$f: A \to B$；并称$b$为$a$的**象**，$a$为$b$的**原象**，记为$b = f(a)$ （$b$ 是唯一的）。$f$的值域记为$R_f$。也可以称$f$是从$A$到$B$的映射。

即：
$$\forall a \in A, \exists! b \in B, a \xrightarrow{f} b$$

从定义3.1可知，函数是一种特殊的关系：如果$f$是从集合$A$到集合$B$的二元关系，为了使$f$也是一个函数，$f$的定义域必须等于$A$，并且$A$中的每个元素只能与$B$中的一个元素有关系$f$。

> 函数$\subset$关系，函数$\neq$关系。

#### 定义3.2

设函数$f: A \to B$，$X \subseteq A$，$Y \subseteq B$，定义$f(X) = \{f(a) \mid a \in X\}$，称$f(X)$是在$f$下$X$的**象**；$f^{-1}(Y) = \{a \in A \mid f(a) \in Y\}$，称$f^{-1}(Y)$是在$f$下$Y$的**原象**。

#### 定义3.3

(1) 设函数$f: A \to B$，若$R_f = B$，则称$f$为**满射**，或称$f$为到上的。
(2) 设函数$f: A \to B$，若$a_1, a_2 \in A$，$a_1 \neq a_2$有$f(a_1) \neq f(a_2)$，则称$f$为**单射**（内射），或称$f$为一对一的。
(3) 设函数$f: A \to B$，若$f$是满射，又是内射，则称$f$为**双射**，或称$f$为一一对应的。


---

## 3.2 逆函数与复合函数

### 逆函数

设$f \subseteq A \times B$为函数，$f^{-1}$也为函数的条件：
① $\text{Dom} f^{-1} = B \Leftrightarrow \text{Ran} f = B \Leftrightarrow f$是满射；
② 若$(b, a_1) \in f, (b, a_2) \in f^{-1}$，则$a_1 = a_2 \Leftrightarrow$若$(a_1, b) \in f, (a_2, b) \in f$，则$a_1 = a_2 \Leftrightarrow f$是单射。

如果$f$是从$A$到$B$的双射，则$f$的逆关系是从$B$到$A$的函数（证明留作习题）。于是定义逆函数如下。

#### 定义3.5

设函数$f: A \to B$是双射，$f$的逆关系称为$f$的**逆函数**，$f^{-1}: B \to A$。若记$f(a) = b$，则记$f^{-1}(b) = a$。

### **复合函数**

设$f \subseteq A \times B$为函数，$g \subseteq B \times C$为函数，定义$f \circ g = \{(a,c) \mid \exists b \in B, \text{使}(a,b) \in f, (b,c) \in g\}$。
记号：$(a,c) \in f \circ g \to a \ f \circ g \ c$，$c = (f \circ g)(a) = (g f)(a) = g(f(a))$

#### 定理3.3

设函数$g: A \to B$，$f: B \to C$，则从$A$到$C$的复合关系$g \circ f$是从$A$到$C$的函数。
