# 无限集和基数

## 知识回顾

### **定义 4.6** 

**设 $A$ 和 $B$ 是两个集合，若存在从 $A$ 到 $B$ 的内射，则称 $A$ 的基数小于或等于 $B$ 的基数，记为 $|A| \leq |B|$ 或 $|B| \geq |A|$。若 $|A| \leq |B|$ 且 $|A| \neq |B|$，则称 $A$ 的基数小于 $B$ 的基数，记为 $|A| < |B|$。**

### **定理 4.19（伯恩斯坦（F. Bernstein）定理）** 

**设 $A$ 和 $B$ 是两个集合，若 $|A| \leq |B|$，又 $|B| \leq |A|$，则 $|A| = |B|$。**

---

### **例** 证明 $\overline{\overline{\mathbb{R} \times \mathbb{R}}} = \overline{\overline{\mathbb{R}}}$

#### 1. 从 $\mathbb{\mathbb {R}}$ 到 $\mathbb{\mathbb {R}} \times \mathbb{\mathbb {R}}$ 的单射

定义
$$
f: \mathbb{\mathbb {R}} \to \mathbb{\mathbb {R}} \times \mathbb{\mathbb {R}},\qquad f(x) = (x, 0).
$$

显然 $f$ 是单射（不同的 $x$ 有不同的第一分量）。所以有 $|\mathbb{\mathbb {R}}| \le |\mathbb{\mathbb {R}} \times \mathbb{\mathbb {R}}|$。

#### 2. 从 $\mathbb{\mathbb {R}} \times \mathbb{\mathbb {R}}$ 到 $\mathbb{\mathbb {R}}$ 的单射

直接把 $\mathbb{\mathbb {R}} \times \mathbb{\mathbb {R}}$ 映入 $(0,1) \times (0,1)$ 再映入 $(0,1)$，最后用 $(0,1)$ 与 $\mathbb{\mathbb {R}}$ 的双射把值搬回去。

##### (a) $\mathbb{\mathbb {R}}$ 与 $(0,1)$ 之间的双射

定义双射（严格且连续）
$$
h: \mathbb{\mathbb {R}} \to (0,1),\qquad h(x) = \frac{1}{\pi} \arctan x + \frac{1}{2}.
$$
$h$ 是双射，故存在 $h^{-1}: (0,1) \to \mathbb{\mathbb {R}}$。

因此给出单射 $(h \times h): \mathbb{\mathbb {R}} \times \mathbb{\mathbb {R}} \to (0,1) \times (0,1)$。

下面只需构造单射 $\psi: (0,1) \times (0,1) \to (0,1)$。

##### (b) 用二进制展开交错构造 $\psi$

任取 $u, v \in (0,1)$。把它们写成二进制小数：
$$u = 0.u_1u_2u_3\cdots_2,\qquad v = 0.v_1v_2v_3\cdots_2,$$

其中 $u_i, v_i \in \{0,1\}$。

> **注意（唯一性处理）**：二进制展开有歧义的点是二进制的“有限展开”与“以全 1 结尾的无限展开”会表示同一个数（如 $0.01111\ldots_2 = 0.1000\ldots_2$）。为避免歧义，我们规定：对所有 dyadic（分母为 $2^k$ 的）有理数，我们**统一选择以无限 1 结尾的表示**。这样每个点在 $(0,1)$ 都有唯一规定的二进制表示。
>
> **举例**：
>
>  * $0.0101_2$（有限表示）替换为 $0.01001111\cdots_2$
>  * $0.1_2$（有限表示）替换为 $0.011111\cdots_2$

现在定义交错（interleaving）映射
$$\psi: (0,1) \times (0,1) \to (0,1),\qquad \psi(u,v) = 0.u_1v_1u_2v_2u_3v_3\cdots_2, $$

即把 $u$ 的第 1 位、第 2 位……与 $v$ 的第 1 位、第 2 位……交替拼成一个新二进制小数。

**断言：$\psi$ 是单射。**  
证明：若 $\psi(u,v) = \psi(u',v')$，则交错后的位序列完全相同，所以落在奇数位的比特分别相等，即 $u_i = u'_i$ 对所有 $i$ 成立，落在偶数位的比特分别相等，即 $v_i = v'_i$ 对所有 $i$ 成立。由我们对二进制表示的**唯一性选择**（排除了以全 1 结尾的表示）可得 $u = u'$ 且 $v = v'$。因此 $\psi$ 是单射。

##### (c) 组合得到所需单射

定义
$$G: \mathbb{\mathbb {R}} \times \mathbb{\mathbb {R}} \xrightarrow{h \times h} (0,1) \times (0,1) \xrightarrow{\psi} (0,1) \xrightarrow{h^{-1}} \mathbb{\mathbb {R}}.$$

把这三个映射串起来，得到 $G = h^{-1} \circ \psi \circ (h \times h)$，显然 $G$ 是单射（复合单射仍为单射）。于是 $|\mathbb{\mathbb {R}} \times \mathbb{\mathbb {R}}| \le |\mathbb{\mathbb {R}}|$。

由 Schröder–Bernstein 定理，存在 $\mathbb{\mathbb {R}}$ 与 $\mathbb{\mathbb {R}} \times \mathbb{\mathbb {R}}$ 之间的双射，因此
$$\big| \mathbb{\mathbb {R}} \times \mathbb{\mathbb {R}} \big| = \big| \mathbb{\mathbb {R}} \big|.$$

---


### **例 4.23** 证明实数序列所组成集合 $E_{\infty}$ 的基数为 $\aleph$，即
$$\overline{\overline{\mathbb {R} \times \mathbb {R} \times \cdots \times \mathbb {R} \times \cdots}} = \overline{\overline{\mathbb {R}}}$$（利用康托尔对角线法）

**证明**：

**首先**说明要证
$$\overline{\overline{\mathbb {R} \times \mathbb {R} \times \cdots \times \mathbb {R} \times \cdots}} = \overline{\overline{\mathbb {R}}}$$

即证 
$$\overline{\overline{(0,1) \times (0,1) \times \cdots \times (0,1) \times \cdots}} = \overline{\overline{(0,1)}}.$$
作双射
$$ f: (0,1) \to \mathbb {R} ， f(x) = \tan\left(\pi x - \frac{\pi}{2}\right) ，$$即知$\overline{\overline{\mathbb {R}}} = \aleph$。

设 $E_{\infty} = \{(x_1,x_2,\cdots,x_n,\cdots) | x_n \in \mathbb{R}, n = 1,2,\cdots\}$，又设 $$B = \{(x_1,x_2,\cdots,x_n,\cdots) | x_n \in (0,1), n = 1,2,\cdots\}.$$先证明 $|E_{\infty}| = |B|$。

作 $\varphi: B \to E_{\infty}$，$\varphi(x) = (f(x_1),f(x_2),\cdots,f(x_n),\cdots)$，对所有 $x = (x_1,x_2,\cdots,x_n,\cdots) \in B$ 成立，显然 $\varphi$ 是双射，所以 $|E_{\infty}| = |B|$。

**其次**证明 $|B| = \aleph$。

作函数 $$f_1: (0,1) \to B，f_1(x) = (x,x,\cdots,x,\cdots) \in B，$$对所有 $x \in (0,1)$ 成立，显然 $f_1$ 是内射，所以 $|(0,1)| \leq |B|$。

又对任意 $x = \{x_1,x_2,\cdots,x_n,\cdots\} \in B$，$x_n$ 用**十进制无限小数唯一表示**，有
$$
\begin{align*}
x_1&=0.x_{11}x_{12}x_{13}\cdots\\
x_2&=0.x_{21}x_{22}x_{23}\cdots\\
x_3&=0.x_{31}x_{32}x_{33}\cdots\\
&\cdots\\
x_n&=0.x_{n1}x_{n2}x_{n3}\cdots\\
&\cdots
\end{align*}
$$

作函数 $$f_2: B \to (0,1)，f_2(x) = 0.x_{11}x_{12}x_{21}x_{13}x_{22}x_{31}\cdots，$$它是由上述 $x_1,x_2,\cdots,x_n,\cdots$ 中小数部分按**对角线方法**排列而得的。$f_2(x) \in (0,1)$ 且 $x \neq y$ 时 $f_2(x) \neq f_2(y)$，所以 $|B| \leq |(0,1)|$。

由定理 4.19 可知 $|B| = |(0,1)|$，因此 $|B| = \aleph$。


#### 结论总结：

| 情形                | 结果      |
|---------------------|-----------|
| 两个可列集的积      | 可列      |
| 有限多个可列集的积  | 可列      |
| 可列多个可列集的积  | **不可列** |

---

### 定理4.21（康托尔定理） 对于任何集合$A$，必有$|A| < |\mathcal{P}(A)|$。

康托尔定理揭示了“集合与其幂集的基数严格不等”，是集合论中刻画无限层次的核心结论。以下按“构造单射→否定双射→得出严格序”的逻辑分步证明，并结合直觉解释关键思路。

#### 一、第一步：构造单射，证明 $|A| \le |\mathcal{P}(A)|$

要证"$A$ 的基数不大于其幂集的基数"，只需找到从 $A$ 到 $\mathcal{P}(A)$ 的单射（按基数序的定义：存在单射则基数≤）。

定义函数 $f: A \to \mathcal{P}(A)$ 为：
$$f(x) = \{x\}$$

即把 $A$ 中的每个元素 $x$，映射到 $\mathcal{P}(A)$ 中“仅含 $x$ 的单点集”。

若 $x_1 \neq x_2$（$x_1, x_2 \in A$），则单点集 $\{x_1\}$ 与 $\{x_2\}$ 显然不相等（元素不同，集合不同）。因此：
$$x_1 \neq x_2 \implies f(x_1) \neq f(x_2)$$

满足单射的定义，故 $|A| \le |\mathcal{P}(A)|$。


#### 二、第二步：反证法，否定双射存在（核心：对角化构造矛盾）

要证“$|A| \neq |\mathcal{P}(A)|$”，需说明**不存在从 $A$ 到 $\mathcal{P}(A)$ 的双射**。采用反证法：假设存在双射，通过构造“矛盾集合”导出逻辑冲突。

##### 1. 假设存在双射

假设存在双射 $g: A \to \mathcal{P}(A)$。双射意味着：
- $g$ 是单射（已满足“每个 $x$ 对应唯一子集”）；
- $g$ 是满射（$\mathcal{P}(A)$ 中的**所有子集**，都能被 $A$ 中的某个元素通过 $g$ 映射到）。

##### 2. 构造“矛盾子集” $B$

基于 $g$，定义 $A$ 的子集 $B \subseteq A$ 为：
$$B = \{ x \in A \mid x \notin g(x) \}$$
###### 直觉解释：$B$ 的含义
对 $A$ 中的每个元素 $x$，$g(x)$ 是 $\mathcal{P}(A)$ 中的一个子集（即 $x$ 的“像子集”）。我们按“$x$ 是否属于自己的像子集”给 $x$ 分类：
- 若 $x \notin g(x)$（$x$ 不在自己的像子集里），则把 $x$ 归入 $B$；
- 若 $x \in g(x)$（$x$ 在自己的像子集里），则不归入 $B$。

例如：若 $g(1) = \{2,3\}$（1 不在像子集里），则 $1 \in B$；若 $g(2) = \{1,2\}$（2 在像子集里），则 $2 \notin B$。

##### 3. 利用满射导出矛盾

因为 $g$ 是满射，$\mathcal{P}(A)$ 中的所有子集都能被 $g$ 映射到。而 $B \in \mathcal{P}(A)$（$B$ 是 $A$ 的子集），因此**存在某个 $b \in A$，使得 $g(b) = B$**（$b$ 是 $B$ 在 $A$ 中的“原像”）。

现在考察关键问题：$b$ 是否属于 $B$？无论回答“是”或“否”，都会导出矛盾：

###### 情况 1：假设 $b \in B$
由 $B$ 的定义（$B = \{x \mid x \notin g(x)\}$），若 $b \in B$，则 $b \notin g(b)$。但我们已知道 $g(b) = B$，因此 $b \notin B$——与“$b \in B$”的假设矛盾。

###### 情况 2：假设 $b \notin B$
同样由 $B$ 的定义，若 $b \notin B$，则 $b \in g(b)$（因为 $B$ 包含所有“不在自身像子集”的元素，不在 $B$ 中就意味着在自身像子集里）。但 $g(b) = B$，因此 $b \in B$——与“$b \notin B$”的假设矛盾。

##### 4. 结论：双射不存在

两种情况均矛盾，说明“存在双射 $g: A \to \mathcal{P}(A)$”的初始假设错误。因此，$|A| \neq |\mathcal{P}(A)|$。


#### 三、第三步：综合得严格序 $|A| < |\mathcal{P}(A)|$

由第一步，我们已证 $|A| \le |\mathcal{P}(A)|$；由第二步，又证 $|A| \neq |\mathcal{P}(A)|$。

按基数严格序的定义（$\kappa < \lambda \iff \kappa \le \lambda$ 且 $\kappa \neq \lambda$），最终得：
$$
|A| < |\mathcal{P}(A)|
$$



---

## 习题

4.1~4.5 证明略。

### 4.6 给出下列集合的递归定义

#### **(1) 可被 5 整除的正整数集。**

令集合 $S$ 表示所有被 $5$ 整除的正整数。给出递归定义如下。

- **基础（基例）**：$5 ∈ S$。
- **构造（归纳步）**：若 $n ∈ S$，则 $n + 5 ∈ S$。
- **结尾（闭包）**：$S$ 中的元素只由上述基例与构造规则生成。

> **说明**：由基例与构造规则，任取 $k ∈ \mathbb{N}$，有 $5,\ 10 = 5+5,\ 15 = 5+5+5,\ …$，即所有形如 $5k$ 的正整数都能被生成。反过来，若 $m$ 是被 $5$ 整除的任一正整数，则写成 $m = 5k$，按 $k$ 次应用构造规则从基例 $5$ 得到 $m$，因此定义恰好刻画了所求集合。

#### **(2) 十进制无符号整数集（可以由零带头）。**

以数值的角度给递归定义更简洁。

设 $D = \{0,1,2,3,4,5,6,7,8,9\}$。定义集合 $T$ 为所有十进制的无符号整数（即非负整数），允许字符串表示以零开头。

- **基础**：对每个数字 $d ∈ D$，令 $d ∈ T$（这里把单个十进制数字视为长度 $1$ 的十进制整数）。
- **构造**：若 $n ∈ T$ 且 $d ∈ D$，则 $10n + d ∈ T$。
- **闭包**：$T$ 中元素仅由上述基例与构造规则生成。

> **说明**：从单个数字通过不断按规则在右侧附加一位可以生成任意长度的十进制字符串表示的非负整数；因为我们把 $0$ 作为基例之一，所以允许以 $0$ 开头的表示形式（例如“$007$”对应数值 $7$，但作为字符串也是 $T$ 的元素）。如果把集合按“字符串表示”理解，上述定义恰好生成所有由数字串构成的十进制无符号整数表示。

#### **补充：字符串集合 $\Sigma^+$和 $\Sigma^*$ 的定义**

**例 4.5** 设 $\Sigma$ 是一个字母表，**$\Sigma$ 上所有的有限非空字符串集合记为 $\Sigma^+$**，递归定义如下。
（1）（基础）如果 $a \in \Sigma$，则 $a \in \Sigma^+$。
（2）（归纳）如果 $x \in \Sigma^+$，且 $a \in \Sigma$，则 $ax \in \Sigma^+$（$ax$ 表示字符 $a$ 与字 $x$ 毗连得到的新的字）。
（3）（闭合）除有限次应用（1）和（2）产生$\Sigma^+$中的字外，$\Sigma^+$中再没有其他字。

集合$\Sigma^+$包含长度为 1，2，3，$\cdots$ 的字，即$\Sigma^+$包含无限个字，但每个字的字符个数是有限的。例如，若 $\Sigma = \{0, 1\}$，则 $\Sigma^+ = \{0, 1, 00, 01, 10, 11, 000, 001, \cdots\}$。

**例 4.6** 设 $\Sigma$ 是一个字母表，**$\Sigma$ 上所有的有限字符串集合记为 $\Sigma^*$，$\Sigma^*$包含空串**，即 $\Sigma^* = \Sigma^+ \cup \{\wedge\}$，可递归定义如下。
（1）（基础）$\wedge \in \Sigma^*$。
（2）（归纳）如果 $x \in \Sigma^*$，且 $a \in \Sigma$，则 $ax \in \Sigma^*$。
（3）（闭合）除有限次应用（1）和（2）产生$\Sigma^*$中的字外，$\Sigma^*$中再没有其他字。

例如，若 $\Sigma = \{0, 1\}$，则 $\Sigma^* = \{\wedge, 0, 1, 00, 01, 10, 11, 000, 001\cdots\}$，是有限二进制序列的集合，其中包含空序列。


#### **(3) 十进制无符号偶整数集（除了单独一个零以外，不得由零带头）。**

在数值意义上，把集合 $E$ 定义为所有非负偶整数（按数值表示，数值没有“前导零”的问题），这样最直接且递归的定义为：

- **基础**：$0 ∈ E$。
- **构造**：若 $n ∈ E$，则 $n + 2 ∈ E$。
- **闭包**：$E$ 中元素仅由上述基例与构造规则生成。

> **说明**：此定义生成了所有形如 $2k$ 的非负整数。由于是用数值来表示集合元素，本身不存在“由零带头”的表示问题；若确实需要以“字符串”形式限定且禁止多位数以 $0$ 开头，则可以采用字符串版本的递归定义：基例为单个字符的偶数字符串 $\{"0","2","4","6","8"\}$，构造为在已有合法字符串左侧或右侧加任一十进制数字，并限定首位不得为 '$0$'（除单独 "$0$" 情形）。

---

### 4.7 证明第二数学归纳法是正确的

第二数学归纳法（强归纳法）假设：要证明命题 $P(n)$ 对所有自然数 $n$ 成立，证明步骤为：

**(a) 基例**：证明 $P(1)$ 成立（或从某个起点 $m_0$ 开始的基例）。

**(b) 归纳步（强归纳假设）**：假设对某固定 $n ≥ 1，P(1), P(2), ..., P(n)$ 都成立，证明 $P(n+1)$ 成立。

结论为：$P(n)$ 对所有自然数 $n$ 成立。

**证明（把强归纳推导自普通数学归纳法）**：令命题 $Q(n)$ 表示“$P(1), P(2), ..., P(n)$ 全都成立”。我们用普通归纳法证明 $Q(n)$ 对所有 $n$ 成立，从而得到 $P(n)$ 对所有 $n$ 成立。

- **基例**：$Q(1)$ 即 $P(1)$ 成立，这由强归纳的基例假设给出。

- **归纳步**：假设 $Q(n)$ 成立，即 $P(1),...,P(n)$ 都成立。由强归纳的归纳假设，已知只要 $P(1),...,P(n)$ 成立就可推出 $P(n+1)$。因此在 $Q(n)$ 的前提下推出 $P(n+1)$ 成立，从而 $Q(n+1)$（即 $P(1),...,P(n+1)$ 都成立）成立。

由普通归纳法得出 $Q(n)$ 对任意 $n$ 成立，因而对任意 $n$，$P(n)$（作为 $Q(n)$ 的一部分）成立。这样完整地证明了第二数学归纳法的正确性。

---

### ✅4.8 平面上顶点坐标为有理数的一切三角形所组成的集合的基数是什么？

记 $\mathbb{Q}$ 为有理数集，$\mathbb{Q} × \mathbb{Q}$ 表示平面上所有坐标为有理数的点，$\mathbb{Q} × \mathbb{Q}$ 是可列的（可列集合的笛卡尔积仍可列，或由 $\mathbb{Q}$ 与 $\mathbb{Q}$ 的可数列举直接得到）。

三角形由三点确定（注意应排除共线的三元组，但**去掉一个可列子集不会改变基数**），因此三角形集合可以视为 $(\mathbb{Q} × \mathbb{Q})³$ 的子集。

既然 $(\mathbb{Q} × \mathbb{Q})³$ 是可列集合的有限次笛卡尔积，仍然可列，去掉共线三元组只会删去可列子集的一部分，结果仍然是可列的。

> **定理**：若 $A$ 可列，且 $B \subseteq A$，则 $B$ 或是有限集，或是可列集。

#### 🤯 平面上顶点坐标为有理数的一切正三角形所组成的集合的基数是什么？

空集，基数为 $0$。

![](assets/4_Infinite_Set_exercises/103ed784-107c-43b5-a63e-fd4996b5c199.png)


---

###  补充：可列集直积的可数性分析


#### 一、两个可列集的直积

若 $A, B$ 都是可列集（即存在双射 $A \to \mathbb{N}$，$B \to \mathbb{N}$），则它们的笛卡尔积 $A \times B$ **也是可列的**。

证明思路：把 $A,B$ 的元素依次编号为  $A = \{a_1, a_2, \dots\},\ B = \{b_1, b_2, \dots\}$。

定义映射：  
$$f: \mathbb{N} \times \mathbb{N} \to A \times B,\quad f(i,j) = (a_i, b_j)$$

因为 $\mathbb{N} \times \mathbb{N}$ 可列（可用对角线法列出所有有序对$(1,1), (1,2), (2,1), (1,3), (2,2), (3,1), \dots $），所以 $A \times B$ 也是可列。

因此：  
$$
A,B \text{ 可列 } \Rightarrow A \times B \text{ 可列。}
$$


#### 二、有限多个可列集的直积

同理，若有有限个可列集 $A_1, \dots, A_n$，则 $A_1 \times A_2 \times \cdots \times A_n$ 仍然可列。

证明可用数学归纳法：  
- $A_1 \times A_2$ 可列，  
- 若 $A_1 \times \cdots \times A_k$ 可列，再与 $A_{k+1}$ 做直积仍可列（因为可列与可列的积是可列）。  

归纳得出有限个可列集的积是可列。


#### 三、**可列多个可列集的直积**（无穷可列积）

这里就**不同了**。

若我们取可列多个可列集的直积，比如：  
$$
\prod_{n=1}^\infty A_n
$$

其中每个 $A_n$ 都可列（如 $A_n = \mathbb{N}$），那么它的直积包含了所有**可数列**（序列）：  
$$
A_1 \times A_2 \times A_3 \times \cdots = \{ (a_1, a_2, a_3, \dots) : a_n \in A_n \}
$$

特别地，当 $A_n = \mathbb{N}$ 时，这个集合就是所有自然数序列的集合 $\mathbb{N}^{\mathbb{N}}$。

**这个集合是不可列的。**



---

### ✅4.9 证明由实数轴上互不相交的有限开区间所组成的集合至多是一个可列集

设 $\mathcal{I}$ 是一族两两不相交的有限开区间，每个区间形式为 $(a,b)$ 且 $b-a>0$ 且 $a,b ∈ \mathbb{R}$。
因为每个非空开区间都包含有理数（有理数在实数中稠密），对每个区间 $I ∈ \mathcal{I}$ 选择一个属于 $I$ 的有理数 $q_I$（选择函数的存在依赖选择公理，不过我们可用常规方法按兑换法对区间标注一个任意的内部有理数）。

> **选择公理**：设 $\{A_i\}_{i \in I}$ 是一个非空集合族（即索引集 I 非空，且对任意 $i \in I$，集合 $A_i$ 均非空），则存在一个选择函数 $f: I \to \bigcup_{i \in I} A_i$，使得对每个索引 $i \in I$，都有 $f(i) \in A_i$。
> 
> **“兑换法”选择的思路**
1. 把所有有理数排成一个序列：   
$$
   q_1, q_2, q_3, \dots
   $$
2. 对于每个区间 $I_\alpha$，从这个有理数序列中找出第一个落在 $I_\alpha$ 内的有理数：	   
$$
   f(\alpha) = q_k \text{，其中 } q_k\in I_\alpha \text{ 且 } k \text{ 是最小的可能值。}
   $$
3. 因为每个区间都是非空的开区间，所以必有有理数落入其中（稠密性保证）。
> 这个方法是 **构造性的**，即使没有选择公理，也能为每个区间确定唯一一个有理数。

若 $I ≠ J$，则 $I$ 与 $J$ 不相交，所选的 $q_I$ 与 $q_J$ 不能相同（否则该有理数同时属于两个不相交区间，矛盾）。因此映射 $I ↦ q_I$ 将 $\mathcal{I}$ 映射到有理数集 $\mathbb{Q}$ 中。

由此 $|\mathcal{I}| \leq |\mathbb{Q}| = \aleph_0$。也就是说，所有这样的互不相交的有限开区间族至多可列。

---

### ✅4.10 证明任一可列集的所有有限子集所组成的集合是可列集

设 $A$ 可列，则存在枚举 $A = \{a_1,a_2,a_3,\dots\}$。

每一个有限子集可以用它在这一枚举中的下标序列来描述：若 $F$ 是有限子集，则设 $F = \{a_{i_1},a_{i_2},\dots,a_{i_k}\}$，其中下标按增序排列 $i_1 < i_2 < ··· < i_k$。这样把每个有限子集与一个**有限的严格上升下标序列**一一对应。

集合有限的严格上升下标序列等价于 
$$\bigcup_{k=0}^{\infty} \{(i_1,\dots,i_k) : 1 \leq i_1 < \dots < i_k\}。$$

对于固定的 $k$，所有长度为 $k$ 的下标元组是 $\mathbb N^k$ 的一个子集，因而可列。**可列个可列集合的可数并仍然是可列的**，因此该并集可列。从而原集合可列。

#### 也可用**素数幂编码法**把有限子集映为自然数，从而直接得到可列性：

**证明目标**：若 $A$ 是可列集，则由 $A$ 的**所有有限子集**组成的集合（记作 $\mathcal{F}(A)$）是可列的。

**证明步骤**：

1. 先把自然数上的情形做掉。令 $p_1, p_2, p_3, \dots$ 为素数序列（$p_1 = 2, p_2 = 3, \dots$）。对任一有限子集 $S \subseteq \mathbb{N}$（允许 $S = \varnothing$），定义编码映射
   $$
   \phi(S) = \prod_{n \in S} p_n,
   $$
   并规定 $\phi(\varnothing) = 1$。

2. 验证 $\phi$ 是单射。若 $S \neq T$ 为两个有限子集，则某个素数 $p_k$ 在两者中的出现情况不同，于是由**算术基本定理（素因子唯一分解）**，$\prod_{n \in S} p_n \neq \prod_{n \in T} p_n$。因此不同的有限子集有不同的编码，$\phi$ 映射到 $\mathbb{N}$ 中。

3. 由此可得：有限子集的集合 $\mathcal{F}(\mathbb{N})$ 与其像 $\phi(\mathcal{F}(\mathbb{N})) \subseteq \mathbb{N}$ 存在一一对应，所以 $\mathcal{F}(\mathbb{N})$ 可列（实际上可数无限）。

4. 一般情形：设 $A$ 可列，取一个枚举双射 $g: \mathbb{N} \to A$。对任意 $T \in \mathcal{F}(A)$（即 $T$ 为 $A$ 的有限子集），把它映回自然数集：   
$$
   S = g^{-1}(T) \subseteq \mathbb{N},
   $$
   然后用第 1 步的编码$\phi(S)$作为$T$的编码。于是得到*注入*   
   $$
   \mathcal{F}(A) \hookrightarrow \mathcal{F}(\mathbb{N}) \xrightarrow{\ \phi\ } \mathbb{N},
   $$
   复合映射是单射。

    > ✅ **区分**：
    > - **映射（mapping）**：只是说“每个元素有像”，不保证唯一性。
    > - **注入（injection）**：比映射更强，要求不同元素的像也不同（即单射）。

5. 因为 $\mathbb{N}$ 可列，含入 $\mathbb{N}$ 的任意集合（包含 $\phi(\mathcal{F}(A))$）也是至多可列，所以 $\mathcal{F}(A)$ 可列。

**结论**：任一可列集 $A$ 的所有有限子集所组成的集合 $\mathcal{F}(A)$ 是可列的（即基数为 $\aleph_0$ 或更小；若 $A$ 无限则 $\mathcal{F}(A)$ 为可数无限）。

可以举个小例子说明编码：
若 $A = \{a_1, a_2, a_3, \dots\}$，有限子集 $\{a_2, a_5\}$ 对应的自然数为 $p_2 \cdot p_5 = 3 \cdot 11 = 33$。


---

### ✅4.11 证明二进制有限小数所组成的集合是可列集

所谓二进制有限小数，即那些在二进制表示下只有有限位小数尾数的数，它们都可以写成形如 $m/2^k$ 的有理数（$m ∈ \mathbb{Z}，k ∈ \mathbb{N}\cup\{0\}$）。因此全集为 $\bigcup_{k=0}^{\infty} \{m/2^k : m \in \mathbb{Z}\}$。

对固定 $k$，集合 $\{m/2^k : m ∈ \mathbb{Z}\}$ 与整数集 $\mathbb{Z}$ 有同样的基数，是可列的。**可列个可列集的并是可列集**（可利用对角线方法证明），因此所有二进制有限小数的集合是可列的。

---

### 4.12 设 $A$ 是平面上以有理数为中心、有理数为半径的圆所组成的集合，证明 $A$ 是可列集

每个这样的圆由三元组 $(p_x,p_y,r) ∈ \mathbb{Q} × \mathbb{Q} × \mathbb{Q}^+$ 唯一确定，其中 $(p_x,p_y)$ 为圆心坐标，$r$ 为半径。

$\mathbb{Q} × \mathbb{Q} × \mathbb{Q}^+$ 是**可列的有限次笛卡尔积**，仍然可列。由一一对应关系，集合 $A$ 可列。

---

### 4.13 证明：若直线上点集 $E$ 的任意两点之间的距离大于 $1$，则集合 $E$ 是有限的或可列的

对每个实数 $x$ 定义函数 $⌊x⌋$ 为其向下取整。若 $x,y ∈ E$ 且 $x ≠ y$，则 $|x-y| > 1$，故不能同时落在同一个区间 $[n,n+1)$（因为落在同一区间的两点距离 $< 1$）。因此不同的点 $x ∈ E$ 有不同的 $⌊x⌋$ 值。于是映射 $x ↦ ⌊x⌋$ 将 $E$ 注入到整数集 $\mathbb{Z}$ 中。

因此 $|E| ≤ |\mathbb{Z}|$，故 $E$ 至多可列（若 $E$ 有无穷个元素，则为可列）。这证明了题述结论。

---

### 4.14 设 $A_1, A_2, …, A_n$ 是可列集，证明 $A_1 × A_2 × ··· × A_n$ 是可列集

**先证明两集合的笛卡尔积是可列集**。设 $A$ 和 $B$ 可列，分别枚举 $A = \{a_0,a_1,a_2,\dots\}，B = \{b_0,b_1,b_2,\dots\}$，则$A\times B = \{a_0, b_0, a_1, b_1, a_2, b_2, \dots, \}$可列。

对任意有限 n，逐步应用上面的结论或用**归纳法**可得到 $A_1×⋯×A_n$ 可列。形式化的证明可以用归纳：若 $n=1$ 成立；若 $A_1×⋯×A_n$ 可列，则与 $A_{n+1}$ 的笛卡尔积仍可列，从而完成归纳。

---

### 💡4.15 构造双射 $f: [0,1] → \text{整个实数轴 } \mathbb{R}$

> 类似**例4.19**。

**说明与构造**：已知开区间 $(0,1)$ 与 $\mathbb{R}$ 等势，可以用明确的连续双射 $g:(0,1) → \mathbb{R}$ 定义为
$$ g(x) = \tan\bigl(\pi(x-1/2)\bigr). $$
这给出从 $(0,1)$ 到 $\mathbb{R}$ 的双射。要从闭区间 $[0,1]$ 到 $\mathbb{R}$ 构造双射，只需构造一个 $[0,1]$ 与 $(0,1)$ 的双射 $h$，然后取 $f = g ∘ h$。

下面给出 $h$ 的显式构造（**把 $[0,1]$ 与 $(0,1)$ 的一一对应通过移动可数点实现**）。因为有理数在 $(0,1)$ 中是可列的，取 $(0,1)$ 中的一个可数枚举 $\{q_1,q_2,q_3,\dots\}$。定义 $h$ 如下：
- $h(0) = q_1,$
- $h(1) = q_2,$
- $对每个 n ≥ 1，令 h(q_n) = q_{n+2},$
- $对其它 x（既不是 0、1，也不是任何 q_n）令 h(x) = x。$

这样的 $h$ 是双射：它把 $(0,1)$ 的有理数序列右移两位，把 $0$ 和 $1$ 移到两个被腾出的有理数位置，其余点不动。容易验证 $h$ 是单射且满射。

于是定义 $f = g ∘ h$ 就是一个从 $[0,1]$ 到 $\mathbb{R}$ 的双射。对 $f$ 的单射性与满射性的证明按复合函数的性质与上述 $h,g$ 的性质逐步检验即可。


---

### 4.16 构造双射 $f: [0,1] → [0,\infty)$

思路与上一题类似。先构造 $[0,1]$ 与 $(0,1)$ 的双射 $h$（可复用 **4.15** 中的 $h$）。再构造 $(0,1)$ 到 $(0,\infty)$ 的显式双射 $g$，例如

$$ g(x) = \frac{x}{1-x}, \qquad x \in (0,1), $$

它是 $(0,1)$ 到 $(0,\infty)$ 的双射。要得到到 $[0,\infty)$ 的双射，我们再对 $(0,\infty)$ 做一次“调整”来加入 $0$：因为 $(0,\infty)$ 与 $[0,\infty)$ 等势，我们可以用可数移动法构造双射 $p:(0,\infty) → [0,\infty)$。具体方法是枚举 $(0,\infty)$ 中的一列互不相同的点 $\{t_1,t_2,\dots\}$（例如选取一列有理数），然后定义
- $p(t_1) = 0,$
- $对 n ≥ 1 令 p(t_{n+1}) = t_n,$
- $对其它 x 令 p(x) = x.$

此 $p$ 为 $(0,\infty)$ 与 $[0,\infty)$ 的双射（把一列点按序搬移腾出 $0$ 的像位），进而复合得到
$$ f = p \circ g \circ h : [0,1] \to [0,\infty). $$
这个 $f$ 是双射，因为 $h$、$g$、$p$ 都是双射的复合。

---

### 4.17 构造双射 $f: [0,1] → (a,b)$

先构造 $[0,1]$ 与 $(0,1)$ 的双射 $h$（如 **4.15**），再用线性仿射把 $(0,1)$ 双射到 $(a,b)$：
$$ L(x) = a + (b-a)x, \qquad x \in (0,1). $$
于是 $f = L ∘ h$ 给出 $[0,1]$ 到 $(a,b)$ 的双射。

---

### 💡4.18 构造无理数集到实数集的一个双射

> 理论上我们已经知道（由**定理4.15**）：去掉一个可数集不会改变一个不可数集的基数，即 $\overline{\overline{\mathbb{I}}} = \overline{\overline{\mathbb{R}}}$。

设 $\mathbb{I}$ 为无理数集，则 $\mathbb{I}$ 为无限集，故 $\mathbb{I}$ 必存在一个可列子集 $B$。

因为有理数集 $\mathbb{Q}$ 为可列集，故 $\mathbb{Q} \cup B$ 也是可列集。

因此，$B$ 与 $\mathbb{Q} \cup B$ 等势，即存在**双射** $f: B \to \mathbb{Q} \cup B$。

定义映射 $g: \mathbb{I} \to \mathbb{R}$ 如下：
$$
g(x) = 
\begin{cases}
f(x), & x \in B \\
x, & x \in \mathbb{I} - B
\end{cases}
$$
显然，$g$ 是双射，且由 $\mathbb{Q} \cup B \cup (\mathbb{I} - B) = \mathbb{R}$ 可知，$g$ 是 $\mathbb{I} \to \mathbb{R}$ 的双射。

> **注**：
> - 对于 $x∈B$：我们用 $f(x)$ 把 $B$“映射”到 $\mathbb{Q}∪B$，因为 $f$ 是双射，所以覆盖了有理数集 $\mathbb{Q}$。可列集 $B⊆\mathbb{I}$ 中的无理数 是由 $B$ 内部的其他元素 通过**双射** $f:B→\mathbb{Q}∪B$ 映射过来的。
> - 对于 $x∈\mathbb{I}∖B$：我们不动它，直接映射到自身，保留了剩下的无理数。

---

### 4.19 实数轴上一切闭区间所组成集合的基数是什么？

任一闭区间可表示为 $[a,b]$（$a,b ∈ \mathbb{R}$，且 $a ≤ b$）。

映射 $[a,b] ↦ (a,b)$ 将闭区间集合注入到 $\mathbb {R}\times\mathbb {R}$。因此闭区间集合的基数 $≤ |\mathbb {R}^2|$。

同时，映射 $x ↦ [x,x]$ 将实数注入到闭区间集合，故基数 $≥ |\mathbb {R}|$。

已知 $|\mathbb {R}^2| = |\mathbb {R}| = c$，所以闭区间集合的基数为连续统 $c$。

设 $\mathcal{I}$ 表示实数轴上一切闭区间的集合：
$$
\mathcal{I} = \{ [a,b] : a,b \in \mathbb{R},\ a \le b \}.
$$

#### 或：利用 **Schröder–Bernstein（伯恩斯坦）定理** 

1. 映射 $f: \mathbb{R} \to \mathcal{I}$ 定为
   $$
   f(x) = [x, x+1].
   $$

   这是单射（不同的 $x$ 对应不同的点区间），所以 $|\mathbb{R}| \le |\mathcal{I}|$。

2. 映射 $g: \mathcal{I} \to \mathbb{R}^2$ 定为
   $$
   g([a,b]) = (a, b).
   $$

   这是单射，所以 $|\mathcal{I}| \le |\mathbb{R}^2|$。又已知 $|\mathbb{R}^2| = |\mathbb{R}|$（例如可用二进制位交错构造单射并应用 Schröder–Bernstein），因此 $|\mathcal{I}| \le |\mathbb{R}|$。

由 1、2 得到 $|\mathbb{R}| \le |\mathcal{I}| \le |\mathbb{R}|$。由 Schröder–Bernstein 定理或直接比较可得
$$
|\mathcal{I}| = |\mathbb{R}|.
$$

**补充说明**： 把 “闭” 改为 “开” 或 “半开” 也同样成立。

---

### ✅4.20 设 $\overline{\Sigma} = n, n \in \mathbb N$。求证 $\overline{\Sigma^{+}} = \aleph_0$

这里按常见约定理解 $\Sigma^{+}$ 为所有非空有限长字符串（词）在字母表 $\Sigma$ 上的集合。若 $|\Sigma| = n < \infty$ 且 $n ≥ 1$，则
$$
\Sigma^{+} = \bigcup_{k=1}^{\infty} \Sigma^k.
$$
对每个固定的 $k$，集合 $\Sigma^k$ 的大小为 $n^k$，是有限的。**可数个有限集合的并为可列集合**，因此 $\Sigma^{+}$ 是可列的。它显然是无限的（因为任意长度 $k$ 的词都存在），因此基数为 $\aleph_0$。

---

### ✅4.21 证明整系数多项式所组成的集合是可列集

设 $P$ 表示所有系数在 $\mathbb Z$ 的一元多项式集合。把多项式按次数分类：所有次数为 $k$ 的多项式对应 $\mathbb Z^{k+1}$（系数向量）。因为 $\mathbb Z$ 可列，有限笛卡儿积 $\mathbb Z^{k+1}$ 也可列。故
$$
P = \bigcup_{k=0}^{\infty} \mathbb Z^{k+1}
$$
是**可数个可列集合的并**，从而可列。这证明整系数多项式集合是可列的。

---

### ✅4.22 证明 $n$ 维欧氏空间的基数为 $c$

证明思路：使用**Schröder–Bernstein（伯恩斯坦）定理**。只需分别构造单射$\mathbb{R} \hookrightarrow \mathbb{R}^n$和$\mathbb{R}^n \hookrightarrow \mathbb{R}$，即可由该定理得出两者基数相等。

#### 1. 从$\mathbb{R}$到$\mathbb{R}^n$的单射（显然）

定义映射
$$
f: \mathbb{R} \to \mathbb{R}^n, \quad f(x) = (x, 0, 0, \dots, 0).
$$

显然 $f$ 是单射（不同的 $x$ 对应不同的 $n$ 维向量），因此 $|\mathbb{R}| \le |\mathbb{R}^n|$。


#### 2. 从 $\mathbb{R}^n$ 到 $\mathbb{R}$ 的单射（二进制交错法）

通过二进制位交错将 $n$ 个实数“拼接”为一个实数，步骤如下：

1. **转化到开区间**：  
   先利用双射 $h: \mathbb{R} \to (0,1)$（例如 $h(x) = \frac{1}{\pi}\arctan x + \frac{1}{2}$），将问题转化为构造单射 $(0,1)^n \to (0,1)$（因双射不改变基数关系）。

2. **二进制表示的唯一性**：  
   对任意 $(u_1, \dots, u_n) \in (0,1)^n$，将每个 $u_k$ 表示为二进制小数：
$$
   u_k = 0.u_{k,1}u_{k,2}u_{k,3}\dots_2, \quad u_{k,j} \in \{0,1\},
   $$
   其中对有限二进制表示的数（如 $0.1_2 = 0.0111\ldots_2$），统一采用**无限 1 结尾**的形式，确保每个数的二进制表示唯一。

4. **交错映射的定义**：  
   定义 $\psi: (0,1)^n \to (0,1)$ 为：
$$
\psi(u_1, \dots, u_n) = 0.u_{1,1}u_{2,1}\dots u_{n,1}u_{1,2}u_{2,2}\dots u_{n,2}u_{1,3}\dots_2,
$$

   即按列依次取各 $u_k$ 的二进制位拼接（先第 1 位的 $n$ 个数字，再第 2 位的 $n$ 个数字，以此类推）。

4. **单射性验证**：  
   若 $\psi(u_1, \dots, u_n) = \psi(v_1, \dots, v_n)$，则交错后的二进制位串完全相同，故每个 $u_k$ 与 $v_k$ 的对应位相等。由于二进制表示唯一，得 $u_k = v_k$ 对所有 $k$ 成立，因此 $\psi$ 是单射。

5. **复合单射**：  
   构造复合映射：$$
G: \mathbb{R}^n \xrightarrow{h \times \cdots \times h} (0,1)^n \xrightarrow{\psi} (0,1) \xrightarrow{h^{-1}} \mathbb{R},
$$   则 $G$ 是单射，故 $|\mathbb{R}^n| \le |\mathbb{R}|$。

#### 3. 应用 Schröder–Bernstein 定理

由前两步得：
$$|\mathbb{R}| \le |\mathbb{R}^n| \le |\mathbb{R}|.$$

根据伯恩斯坦定理，有：
$$\big|\mathbb{R}^n\big| = \big|\mathbb{R}\big| = c.$$

**备注**：基数算术中等式 $c^n = c$（对任意有限正整数 $n$）可直接得出结论，但上述构造法更直观，且显式展示了单射的存在性。

**结论**：对任意正整数 $n$，欧氏空间 $\mathbb{R}^n$ 的基数等于连续体基数 $c$。


---

### ✅4.23 设 $A = \mathbb{N}$，$B = (0,1)$，证明$\overline{\overline{A \times B}} = c$


采用构造性方法，通过建立双向单射，结合 Schröder–Bernstein 原理完成证明。

#### 1. 从 $B$ 到 $A \times B$ 的单射（确立下界）

定义映射：
$$\iota: B \to A \times B, \quad \iota(b) = (0, b)$$
- **单射验证**：若 $\iota(b_1) = \iota(b_2)$，则 $(0, b_1) = (0, b_2)$，直接得 $b_1 = b_2$，故 $\iota$ 是单射。  
- **基数关系推导**：由单射性质得 $|B| \le |A \times B|$。  
  又因 $B=(0,1)$ 与 $\mathbb{R}$ 等势（如通过 $h(x)=\frac{1}{\pi}\arctan x+\frac{1}{2}$ 建立双射），即 $|B|=c$，因此：
$$
c \le |A \times B|
$$

#### 2. 从 $A \times B$ 到 $\mathbb{R}$ 的单射（确立上界）

定义映射：
$$
\varphi: A \times B \to \mathbb{R}, \quad \varphi(n, b) = n + b
$$
- **单射验证**：假设 $\varphi(n_1, b_1) = \varphi(n_2, b_2)$，即 $n_1 + b_1 = n_2 + b_2$。  
  由于 $b_1, b_2 \in (0,1)$，则 $n_1 + b_1 \in (n_1, n_1+1)$，$n_2 + b_2 \in (n_2, n_2+1)$。  
  两个开区间 $(n_1, n_1+1)$ 与 $(n_2, n_2+1)$ 仅当 $n_1 = n_2$ 时重合，此时 $b_1 = b_2$，故 $\varphi$ 是单射。  
- **基数关系推导**：由单射性质得 $|A \times B| \le |\mathbb{R}|$，而 $|\mathbb{R}|=c$，因此：
$$|A \times B| \le c$$

#### 3. 应用 Schröder–Bernstein 原理得结论

结合步骤 1 和步骤 2 的结果：
$$c \le |A \times B| \le c$$

根据 Schröder–Bernstein 原理（若集合 $X$ 与 $Y$ 满足 $|X| \le |Y|$ 且 $|Y| \le |X|$，则 $|X|=|Y|$），最终得：
$$|A \times B| = c$$

---

### 4.24 设 $A = [0,1]$，证明 $\overline{\overline{A \times A}} = c$

因为 $A$ 的基数为 $c$，且有限笛卡儿积 $A×A$ 等势于 $\mathbb{R}^2$，又已知 $|\mathbb{R}^2| = c$，所以 $A×A$ 的基数为 $c$。也可以直接用 **4.22** 的结论得到相同结果。

---

### 4.25 证明在由基数所组成的集合上的关系 $≤$ 是偏序关系 (并在选择公理下为全序)，$<$ 是严格序关系

#### 1. ≤ 是偏序关系（自反、反对称、传递）
偏序关系需满足**自反性**、**反对称性**和**传递性**，逐一验证如下：

##### （1）自反性（Reflexive）  
对任意基数$\kappa$，取其代表集合 $A$（即$|A| = \kappa$）。  
考虑恒等映射$\mathrm{id}_A: A \to A$，显然$\mathrm{id}_A(x) = x$是单射（不同元素映射到不同元素）。  
由$\kappa \le \lambda$的定义（存在代表集间的单射），得$\kappa \le \kappa$，故自反性成立。

##### （2）反对称性（Antisymmetric）  
设$\kappa \le \lambda$且$\lambda \le \kappa$，取对应代表集$|A| = \kappa$，$|B| = \lambda$：  
- 由$\kappa \le \lambda$得单射$f: A \to B$；  
- 由$\lambda \le \kappa$得单射$g: B \to A$。  

根据 **Schröder–Bernstein 定理**（又称 Cantor–Schröder–Bernstein 定理）：若存在从$A$到$B$的单射和从$B$到$A$的单射，则存在$A$到$B$的双射。  
设该双射为$h: A \to B$，由$\kappa = \lambda$的定义（代表集间存在双射），得$\kappa = \lambda$，故反对称性成立。

##### （3）传递性（Transitive）  
设$\kappa \le \lambda$且$\lambda \le \mu$，取对应代表集：  
-$|A| = \kappa$，$|B| = \lambda$，由$\kappa \le \lambda$知存在单射$f: A \to B$；  
-$|C| = \mu$，由$\lambda \le \mu$知存在单射$g: B \to C$。  

考虑复合映射$g \circ f: A \to C$，由“单射的复合仍是单射”（若$g(f(x_1)) = g(f(x_2))$，则$f(x_1) = f(x_2)$，进而$x_1 = x_2$），得$g \circ f$是单射。  
由定义，$\kappa \le \mu$，故传递性成立。

综上，$\le$在基数集合上满足偏序关系的全部条件。


#### 2. < 是严格序关系（反自反、传递、反对称）
严格序 $<$ 定义为：$\kappa < \lambda \iff \kappa \le \lambda$ 且 $\kappa \neq \lambda$，需验证**反自反性**、**传递性**和**反对称性**。

##### （1）反自反性（Irreflexive）  
对任意基数 $\kappa$，若假设 $\kappa < \kappa$，则由定义需同时满足 $\kappa \le \kappa$（成立，自反性已证）和 $\kappa \neq \kappa$（矛盾，同一基数必相等）。  
因此不存在 $\kappa < \kappa$，反自反性成立。

##### （2）反对称性（Asymmetric）  
若 $\kappa < \lambda$，则不可能有 $\lambda < \kappa$。反设 $\lambda < \kappa$，则：  
- $\kappa < \lambda \implies \kappa \le \lambda$；  
- $\lambda < \kappa \implies \lambda \le \kappa$。  

由 $\le$ 的反对称性，得 $\kappa = \lambda$，与 $\kappa < \lambda$（要求 $\kappa \neq \lambda$）矛盾。  
因此 $\kappa < \lambda \implies \lambda \nless \kappa$，不对称性成立。

##### （3）传递性（Transitive）  
设 $\kappa < \lambda$ 且 $\lambda < \mu$，由定义：  
- $\kappa < \lambda \implies \kappa \le \lambda$ 且 $\kappa \neq \lambda$；  
- $\lambda < \mu \implies \lambda \le \mu$ 且 $\lambda \neq \mu$。  

第一步：由 $\kappa \le \lambda$ 和 $\lambda \le \mu$，结合 $\le$ 的传递性，得 $\kappa \le \mu$。  
第二步：证明 $\kappa \neq \mu$。反设 $\kappa = \mu$，则由 $\lambda \le \mu = \kappa$ 和 $\kappa \le \lambda$，结合 $\le$ 的反对称性，得 $\lambda = \kappa = \mu$，与 $\lambda \neq \mu$ 矛盾。  
因此 $\kappa \le \mu$ 且 $\kappa \neq \mu$，即 $\kappa < \mu$，传递性成立。