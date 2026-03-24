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