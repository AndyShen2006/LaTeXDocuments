证明的方法是运用反证法，反设定理不成立，然后用两种方法估计{\displaystyle {2n \choose n}}{2n \choose n}的上下界，得出矛盾的不等式

注：下面的证明中，都假设{\displaystyle p}p属于质数集。

不等式1
这条不等式是关于{\displaystyle {2n \choose n}}{2n \choose n}的下界的。

对于正整数{\displaystyle n}n，{\displaystyle {2n \choose n}\geq {\frac {4^{n}}{2n}}}{\displaystyle {2n \choose n}\geq {\frac {4^{n}}{2n}}}
证明 ：

对于 {\displaystyle k\leq 2n}{\displaystyle k\leq 2n} ， {\displaystyle {2n \choose n}\geq {2n \choose k}}{\displaystyle {2n \choose n}\geq {2n \choose k}}
若{\displaystyle k\neq n}{\displaystyle k\neq n}，{\displaystyle {2n \choose n}>{2n \choose k}}{\displaystyle {2n \choose n}>{2n \choose k}}
因此{\displaystyle 2n{2n \choose n}\geq \sum _{i=1}^{2n}{2n \choose i}+1=2^{2n}=4^{n}}{\displaystyle 2n{2n \choose n}\geq \sum _{i=1}^{2n}{2n \choose i}+1=2^{2n}=4^{n}}
引理1
{\displaystyle \prod _{k+1<p\leq 2k+1}p\ <4^{k}}{\displaystyle \prod _{k+1<p\leq 2k+1}p\ <4^{k}}
证明： 注意到所有大于 k+1 而小于 2k+1 的质数都在(2k+1)! 中而不在(k+1)! 或 k！ 中，于是{\displaystyle \prod _{k+1<p\leq 2k+1}p}{\displaystyle \prod _{k+1<p\leq 2k+1}p} 是{\displaystyle {{2k+1} \choose {k+1}}}{\displaystyle {{2k+1} \choose {k+1}}}的因子。

{\displaystyle \prod _{k+1<p\leq 2k+1}p\quad \left\vert \ {{2k+1} \choose {k+1}}\right.}{\displaystyle \prod _{k+1<p\leq 2k+1}p\quad \left\vert \ {{2k+1} \choose {k+1}}\right.}
同时又有 {\displaystyle 2{{2k+1} \choose {k+1}}={{2k+1} \choose {k+1}}+{{2k+1} \choose {k}}<\sum _{i=0}^{2k+1}{{2k+1} \choose {i}}=2\cdot 4^{k}}{\displaystyle 2{{2k+1} \choose {k+1}}={{2k+1} \choose {k+1}}+{{2k+1} \choose {k}}<\sum _{i=0}^{2k+1}{{2k+1} \choose {i}}=2\cdot 4^{k}}
于是就有 {\displaystyle \prod _{k+1<p\leq 2k+1}p\ \ \leq {{2k+1} \choose {k+1}}<4^{k}}{\displaystyle \prod _{k+1<p\leq 2k+1}p\ \ \leq {{2k+1} \choose {k+1}}<4^{k}}
定理1
这个定理和{\displaystyle {2n \choose n}}{2n \choose n}的上界有关。

对于所有正整数{\displaystyle n}n， {\displaystyle \prod _{p\leq n}p<4^{n}}{\displaystyle \prod _{p\leq n}p<4^{n}}
数学归纳法：

当{\displaystyle n=2}n=2，2 < 16，成立。

假设对于所有少于{\displaystyle n}n的整数，叙述都成立。

显然，若n>2且n是偶数，{\displaystyle \prod _{p\leq n}p=\prod _{p\leq n-1}p}{\displaystyle \prod _{p\leq n}p=\prod _{p\leq n-1}p}。对于奇数的n，设n=2k+1。

从引理1和归纳假设可得：

{\displaystyle \prod _{p\leq n}p=\prod _{p\leq 2k+1}p=\prod _{p\leq k+1}p\cdot \prod _{k+1<p\leq 2k+1}p<4^{k+1}\cdot 4^{k}=4^{2k+1}=4^{n}}{\displaystyle \prod _{p\leq n}p=\prod _{p\leq 2k+1}p=\prod _{p\leq k+1}p\cdot \prod _{k+1<p\leq 2k+1}p<4^{k+1}\cdot 4^{k}=4^{2k+1}=4^{n}}

系理1
首先的定理：

若{\displaystyle p}p是质数，{\displaystyle n}n是整数。设{\displaystyle s}s是最大的整数使得{\displaystyle p^{s}|n!}{\displaystyle p^{s}|n!} ，则{\displaystyle s=\sum _{i=1}^{\infty }{\lbrack {\frac {n}{p^{i}}}\rbrack }}{\displaystyle s=\sum _{i=1}^{\infty }{\lbrack {\frac {n}{p^{i}}}\rbrack }}
下面这些系理和{\displaystyle {2n \choose n}}{2n \choose n}的上界有关。


若{\displaystyle p}p为质数，设{\displaystyle s_{p}}{\displaystyle s_{p}}是最大的整数使得 {\displaystyle p^{s_{p}}}{\displaystyle p^{s_{p}}} 整除 {\displaystyle {2n \choose n}}{2n \choose n}，则：

{\displaystyle s_{p}=\sum _{i\geq 1}{(\lbrack {\frac {2n}{p^{i}}}\rbrack -2\lbrack {\frac {n}{p^{i}}}\rbrack )}}{\displaystyle s_{p}=\sum _{i\geq 1}{(\lbrack {\frac {2n}{p^{i}}}\rbrack -2\lbrack {\frac {n}{p^{i}}}\rbrack )}}
对于所有{\displaystyle x>0}x>0，{\displaystyle \lbrack 2x\rbrack -2\lbrack x\rbrack \leq 1}{\displaystyle \lbrack 2x\rbrack -2\lbrack x\rbrack \leq 1} ，所以

{\displaystyle s_{p}=\sum _{i\geq 1}{(\lbrack {\frac {2n}{p^{i}}}\rbrack -2\lbrack {\frac {n}{p^{i}}}\rbrack )}\leq max\left\{r|p^{r}\leq 2n\right\}}{\displaystyle s_{p}=\sum _{i\geq 1}{(\lbrack {\frac {2n}{p^{i}}}\rbrack -2\lbrack {\frac {n}{p^{i}}}\rbrack )}\leq max\left\{r|p^{r}\leq 2n\right\}}
于是得到三个上界：

{\displaystyle p^{s_{p}}\leq 2n}{\displaystyle p^{s_{p}}\leq 2n}
若 {\displaystyle {\sqrt {2n}}<p}{\displaystyle {\sqrt {2n}}<p} ， {\displaystyle s_{p}\leq 1}{\displaystyle s_{p}\leq 1}
若 {\displaystyle 2n/3<p\leq n}{\displaystyle 2n/3<p\leq n}，{\displaystyle s_{p}=0}{\displaystyle s_{p}=0}（因为 2n! 中只有两个 p，在 n! 中恰有一个 p）
核心部分
假设存在大于1的正整数{\displaystyle n}n，使得没有质数{\displaystyle p}p符合{\displaystyle n<p<2n}{\displaystyle n<p<2n}。根据系理1.2和1.3：

{\displaystyle {2n \choose n}=\prod _{p\leq 2n}p^{s_{p}}=\prod _{p\leq 2n/3}p^{s_{p}}\leq \prod _{p\leq {\sqrt {2n}}}p^{s_{p}-1}\cdot \prod _{p\leq 2n/3}p}{\displaystyle {2n \choose n}=\prod _{p\leq 2n}p^{s_{p}}=\prod _{p\leq 2n/3}p^{s_{p}}\leq \prod _{p\leq {\sqrt {2n}}}p^{s_{p}-1}\cdot \prod _{p\leq 2n/3}p}

再根据系理1.1和定理1： {\displaystyle {2n \choose n}\leq }{\displaystyle {2n \choose n}\leq } 上式最右方 {\displaystyle <(2n)^{{\sqrt {2n}}/2-1}\cdot 4^{2n/3}}{\displaystyle <(2n)^{{\sqrt {2n}}/2-1}\cdot 4^{2n/3}}

结合之前关于{\displaystyle 2n \choose n}{\displaystyle 2n \choose n}的下界的不等式1：

{\displaystyle (2n)^{-1}4^{n}<{2n \choose n}<(2n)^{{\sqrt {2n}}/2-1}\cdot 4^{2n/3}}{\displaystyle (2n)^{-1}4^{n}<{2n \choose n}<(2n)^{{\sqrt {2n}}/2-1}\cdot 4^{2n/3}}
{\displaystyle 4^{n}<(2n)^{{\sqrt {2n}}/2}\cdot 4^{2n/3}}{\displaystyle 4^{n}<(2n)^{{\sqrt {2n}}/2}\cdot 4^{2n/3}}
{\displaystyle 4^{2n/3}<(2n)^{\sqrt {2n}}}{\displaystyle 4^{2n/3}<(2n)^{\sqrt {2n}}}
两边取2的对数，并设{\displaystyle x={\sqrt {2n}}}{\displaystyle x={\sqrt {2n}}}：

{\displaystyle x\ln 2-3\ln x<0}{\displaystyle x\ln 2-3\ln x<0}。
显然{\displaystyle x\geq 16}{\displaystyle x\geq 16}，即{\displaystyle n\geq 128}{\displaystyle n\geq 128}时，此式不成立，得出矛盾。 因此{\displaystyle n\geq 128}{\displaystyle n\geq 128}时，伯特兰—切比雪夫定理成立。

再在{\displaystyle n<128}{\displaystyle n<128}时验证这个假设即可。