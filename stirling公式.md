## 高中范围的基本估计
高中范围内最简单的估计是基于基本不等式
$$
n!=1 \cdot 2  \cdots n < 
(\frac{1+2 \cdots +n}{n})^2=
(\frac{n+1}{2})^2
$$
更进一步的,我们有如下高考题的估计
## 2023天津高考
(2023年天津高考)证明:
$$ 
\frac{5}{6} < \ln(n!) - \left(n + \frac{1}{2}\right)\ln(n) + n \leqslant 1.
$$
这个题也就是要我们研究
$$
\ln(n!) - \left(n + \frac{1}{2}\right)\ln(n) + n
$$
的性质(记为$f(n)$)，我们先看单调性

$f(n+1)-f(n)$=
$$
\ln(n+1) + \ln(n!) - \left(n + \frac{3}{2}\right)\ln(n+1) + n + 1 - \ln(n!) + \left(n + \frac{1}{2}\right)\ln(n)-n
$$
即
$$
1 - \left(n + \frac{1}{2}\right)\ln\left(1 + \frac{1}{n}\right)
$$
利用导数容易发现$f(n+1)-f(n)<0$，故$f(n)$单调减

于是有
$$
f(n)\leq f(1)=1
$$
#### 不等式左边
对于左边则要复杂不少，

高中范围内这种类型问题相对普适的方法是作差分后逐项估计

具体的做法如下
$$
\frac{5}{6}= 1 - \frac{1}{6} \sum_{i=1}^{n-1} \left( \frac{1}{i} - \frac{1}{i+1} \right)
$$
$$
f(n)=f(1) - \sum_{i=1}^{n-1} \left( f(i) - f(i+1) \right)
$$
这样问题就变成了比较
$$\frac{1}{6}\left( \frac{1}{i} - \frac{1}{i+1} \right)$$
$$ \left( f(i) - f(i+1) \right)=
1 - \left(i + \frac{1}{2}\right)\ln\left(1 + \frac{1}{i}\right)$$
两者的大小关系，
这就是一个比较简单的求导问题了，接下来我们只需要构造函数求导即可（具体证明略）

可以看到，这种解法的核心有几个，一个是发现f(n)的单调性，另一个是作差分逐项估计的想法

延着这个想法，我们可以得到n！更加深入的估计



# stolz定理
设数列 ${b_n}$ 满足：
严格单调递增；
当 $n \to \infty$时，$b_n \to +\infty$（或 $-\infty$）。

若极限 
$$
\lim_{n \to \infty} \frac{a_{n+1} - a_n}{b_{n+1} - b_n} = l
$$
存在（$l$ 可以是有限数、$+\infty$ 或 $-\infty$），则

$$
\lim_{n \to \infty} \frac{a_n}{b_n} = l
$$

二、$\frac{0}{0}$ 型 Stolz 定理

设数列 ${b_n}$ 满足：

严格单调递减；

当 $n \to \infty$ 时，$a_n \to 0$ 且 $b_n \to 0$。

若极限
$$
\lim_{n \to \infty} \frac{a_{n+1} - a_n}{b_{n+1} - b_n} = l
$$
存在($l$ 可以是有限数、$+\infty$ 或 $-\infty$），则
$$
\lim_{n \to \infty} \frac{a_n}{b_n} = l
$$
这就是极限中差分想法的简单运用，沿着这条路，我们来看这个估计

求极限
$$
\lim_{n\to \infty}\frac{\sqrt[n]{n！}}{n}
$$
取对数
$$
\frac{\sqrt[n]{n}}{n!}=e^{\frac{1}{n}\ln n！-\ln n}
$$
由stolz
$$
\lim_{n \to \infty}\frac{1}{n}\ln n！-\ln n=
\lim_{n \to \infty}(n-1)\ln (\frac{n-1}{n})=-1
$$
于是
$$
\lim_{n\to \infty}\frac{\sqrt[n]{n！}}{n}=\frac{1}{e}
$$
也就是$\sqrt[n]{n！}\sim \frac{n}{e}$

接下来，我们将从积分的角度来看这个问题
### 和的积分估计
这个角度要求我们先把 $n!$ 改写为和的形式
$$
\ln n!=\sum_{i=1}^{n}\ln i

\sum_{i=1}^{n}\ln i < 
\int_1^n \ln x dx+\frac{1}{2}\ln n+1=
n\ln n -n+\frac{1}{2}\ln n+1
$$
在此基础上，我们考虑
$$
a_n=\frac{n!e^n}{n^n\sqrt{n}}
$$
考察它的单调性
$$
\frac{a_n}{a_{n+1}}=
\frac{n!e^n}{n^n\sqrt{n}}
\frac{(n+1)^{n+1}\sqrt{n+1}}{(n+1)!e^{n+1}}
$$
$$
=\frac{1}{n^n\sqrt{n}}
\frac{(n+1)^{n+1}\sqrt{n+1}}{(n+1)e}
=(\frac{n+1}{n})^{n+\frac{1}{2}}\frac{1}{e}
$$
取对有 (因为取对后能对指数取得一个很好的估计，正如我们现在对阶乘做的估计一样)
$$
\ln \frac{a_n}{a_{n+1}}= (n+\frac{1}{2})\ln \frac{n+1}{n}-1
$$
我们只要估计这个式子与 0 的大小关系就可以了
$$
(n+\frac{1}{2})\ln \frac{n+1}{n}-1 \sim 0
$$
这里 $\sim$ 表示比较大小
$$
(n+\frac{1}{2})\ln \frac{n+1}{n} \sim 1
$$
$$
\ln \frac{n+1}{n} \sim \frac{1}{n+\frac{1}{2}}
$$
$$
\ln 1+x \sim \frac{2x}{2+x}
$$
熟知
$$
\ln 1+x >  \frac{2x}{2+x}
$$
故
$$
\ln \frac{a_n}{a_{n+1}}=(n+\frac{1}{2})\ln \frac{n+1}{n}-1 > 0
$$
于是 $a_n$ 单调减且有下界

故 $a_n$ 收敛，有
$$
n! \sim C(\frac{n}{e})^n\sqrt{n}
$$
接下来的问题就是如何找到这个 c 了

---
### Wallis 定理
考虑
$$
I_n=\int_0^{\frac{\pi}{2}}sin^nx dx
$$
由分部积分 ($v=sin^{n-1} x,du=sin x$) 
$$
I_n=
uv_{x=0}^{\frac{\pi}{2}}-
\int_0^{\frac{\pi}{2}}(n-1)sin^{n-2}(-cos^2 x)dx  
$$
由$cos^2 x=1- sin^2 x$
$$
I_n=\int_0^{\frac{\pi}{2}}(n-1)sin^{n-2}(1- sin^2 x)dx
$$
$$
I_n=-(n-1)I_n+(n-1)I_{n-2}
$$
化简有
$$
I_n=\frac{(n-1)}{n}I_{n-2}
$$
解这个递推得到
$$
I_{2k} = \frac{(2k-1)!!}{(2k)!!} \frac{\pi}{2}
$$
$$
I_{2k+1} = \frac{(2k)!!}{(2k+1)!!}
$$
其中
$$
(2 k-1)!!=1\cdot 3 \cdot 5  \cdot\cdot\cdot (2 k-1),
2 k!!=2\cdot 4 \cdot\cdot\cdot 2 k
$$

又由
$$
sin^{n+1} x < sin^{n} x < sin^{n-1} x
$$
由于 $sin x$ 在 $(0,\frac{\pi}{2})$ 上 $\in (0,1)$,于是
$$
\int_0^{\frac{\pi}{2}}  sin^{n+1} x dx < 
\int_0^{\frac{\pi}{2}}  sin^{n} x   dx <
\int_0^{\frac{\pi}{2}}  sin^{n-1} x dx
$$
成立

故有
$$
I_{2k+1}=\frac{2k+1}{2k}I_{2k-1} < I_{2k} < I_{2k-1}
$$
即
$$
\lim_{n \to \infty}\frac{I_{2n}}{I_{2n-1}}=1
$$
把 $\frac{\pi}{2}$ 提取出来
$$
\frac{\pi}{2}=
\lim_{n \to \infty}
\frac{((2n)!!)^2}{(2n+1)!!(2n-1)!!}
$$
---
### 结果
我们把双阶乘改写为阶乘的格式
$$
(2n)!! = 2 \cdot 4 \cdot 6 \cdots (2n) = 2^n n!
$$
$$
(2n-1)!!=\frac{2n!}{2n!!}=\frac{2n!}{2^nn!}
$$
于是
$$
\frac{\pi}{2}=
\lim_{n \to \infty}
\frac{((2n)!!)^2}{(2n+1)!!(2n-1)!!}
=\lim_{n \to \infty}
\frac{(2^n n!)^2}{(2n+1)(\frac{2n!}{2^nn!})^2}
$$
进一步化简，利用等价无穷大替换得
$$
\sqrt{\frac{\pi}{2}}=
\lim_{n \to \infty}
\frac{2^{2n} (n!)^2}{\sqrt{2n+1}(2n)!} =
\lim_{n \to \infty}
\frac{2^{2n} \left[ C \sqrt{n} \left(\frac{n}{e}\right)^n \right]^2}
{\sqrt{2n+1}C \sqrt{2n} \left(\frac{2n}{e}\right)^{2n}}
$$
$$
\sqrt{\frac{\pi}{2}}=
\lim_{n \to \infty}
\frac{nC}{\sqrt{(2n+1)(2n)}}=
\frac{C}{2}
$$
即
$$
C=\sqrt{2\pi}
$$
于是我们就得到了 Stirling 公式：
$$
n！\sim \sqrt{2\pi n}(\frac{n}{e})^n
$$
