---
title: "11月5日　7-4"
code-fold: true
format:
  html: default
page-layout: article
date: 2024/11/05
toc: true
lang: ja
categories:
  - 現代数理統計学
status: "作成中"
---


# ２項分布

$
X \sim Bin(n,p)
$
とする。

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
I(p)=E[\ell'(p,X)^2]=\frac{E[(X-np)^2]}{(p(1-p))^2}
$$



