---
title: "11月5日　7-4"
code-fold: true
format:
  html: default
  typst:
    toc: true
page-layout: article
date: 2024/11/05
toc: true
lang: ja
categories:
  - 現代数理統計学
status: "作成中"
---


## ２項分布

$X \sim Bin(n,p)$とする。

$p$ の推定量 $\displaystyle \hat{p}=\frac{X}{n}$ は $\displaystyle E_p[\hat{p}] = \frac{E_p[X]}{n}=\frac{np}{n}=p$ より不偏推定量である。

推定量の分散は$\displaystyle Var[\hat{p}]=\frac{Var[X]}{n^2}=\frac{p(1-p)}{n}$ である。

２項分布の確率変数
$f(x,p)=p^x(1-p)^{n-x}\begin{pmatrix}
n  \\
x  \\
\end{pmatrix}
$の対数を$p$ で微分すると

$$
\begin{aligned}
    \ell'(p, x) &= \frac{\partial}{\partial p} \left( x \log p + (n - x) \log (1 - p) + \log \binom{n}{x} \right) \\
    &= \frac{x}{p}+\frac{-(n-x)}{1-p} = \frac{x-np}{p(1-p)}
\end{aligned}
$$

となる。従ってフィッシャー情報量は

$$
I(p)=E[\ell'(p,X)^2]=\frac{E[(X-np)^2]}{(p(1-p))^2} =\frac{np(1-p)}{(p(1-p))^2} = \frac{n}{p(1-p)}
$$




となり、これは$\displaystyle \frac{1}{Var_p[\hat{p}]}$ に一致する。したがって$\hat{p}$は$UMVU$であることが確かめられた。


## 正規分布

次に正規分布の母平均$\mu$の推定において標本平均$\bar{X}$ がUMVUであることを示す。

まず、$\mu$ に関するフィッシャー情報量を求める。

$$
\ell(\mu,x)= - \frac{(x-\mu)^2}{2\sigma^2} - \frac{1}{2} \log(2\pi \sigma^2)
$$

を$\mu$ で偏微分すると$\displaystyle \ell'(\mu,x)=\frac{x-\mu}{\sigma^2}$ を得る。したがって、

$$
I(\mu)=\frac{E[(X-\mu)^2]}{\sigma^4} = \frac{1}{\sigma^2}
$$

となり、$\bar{X}$ がUMVUであることが示された。