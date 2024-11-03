---
title: "11月5日　7-4"
code-fold: true
format:
  html: default
  revealjs:
    theme: [default, wara.scss]
    output-file: page-reveal.html
    smaller: true
    scrollable: true
    chalkboard: true
    toc: false
    html-math-method: mathjax
    eraser: { radius: 100}
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

まず二項分布における$p$ の推定量を$\displaystyle \hat{p}=\frac{X}{n}$ とおく。 $\displaystyle E_p[\hat{p}] = \frac{E_p[X]}{n}=\frac{np}{n}=p$ より不偏推定量である。

ちなみに不偏推定量の定義は、以下である。

::: {#thm-line}

<br/>

$\hat{\theta}$ が不偏推定量であるとは

$$
E_\theta[\hat{\theta}(X)] = \theta, \quad \delta\theta
$$

が成り立つことである。

:::



::: {.extra-space3}

:::


不偏推定量 $\displaystyle \hat{p}=\frac{X}{n}$ がUMVUであることを示すには、次の等式を満たす。

::: {#thm-line}


## クラメル・ラオの不等式を用いたUMVUの証明

<br/>

不偏推定量$\hat{\theta^*}$ が

$$
Var_\theta[\hat{\theta^*}] = \frac{1}{I_n(\theta)},\quad \delta\theta
$$

を満たせば、$\hat{\theta*}$はUMVUである。

:::

つまり、$\displaystyle Var_\theta \left[\hat{p}\right] = \frac{1}{I_n(\theta)}$ であることを示したい。

::: {.extra-space2}

:::



まず、推定量の分散は$\displaystyle Var[\hat{p}]=\frac{Var[X]}{n^2}=\frac{p(1-p)}{n}$ である。

::: {.extra-space1}

:::

次にフィッシャー情報量$I_n(\theta)$を求めたい。

::: {#thm-line}

## フィッシャー情報量の求め方

<br/>

$\ell'(\theta,X)$は対数充度関数$\ell(\theta,X)$ を$\theta$ で微分したものである。

$$
I_n(\theta) = E_\theta \left[(\ell'(\theta,X)^2)\right]
$$

:::



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

$E[(X-np)^2]$はテクニカル！


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

$E[(X-\mu)^2]$もテクニカル！