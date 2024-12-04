---
title: "12月3日　ワルド型の検定"
code-fold: true
format:
  revealjs:
    theme: [default, wara.scss]
    output-file: page-reveal.html
    smaller: true
    scrollable: false
    chalkboard:
      theme: whiteboard
    toc: false
    html-math-method: mathjax
revealjs-plugins:
  - pointer
page-layout: article
date: 2024/11/12
toc: true
lang: ja
categories:
  - 現代数理統計学
status: "完了"
---


# ワルド型検定


尤度比検定を中心に説明してきたが、近似的な検定手法を与える方法としてMLEや標本平均に基づいたワルド型の検定についてこの節で説明する。

## 最尤推定量に基づいた検定

$X_1,\dots,X_n$を独立にそれぞれパラメトリックな確率（密度）関数$f(x|\theta)$に従うとし、$\theta$を１次元のパラメーターとする。$\theta$のMLEを$\hat{\theta}$とすると、定理8.15より適当な正則条件のもとで$n \to \infty$のとき$\sqrt{n}(\hat{\theta}-\theta) \to_d N(0, \frac{1}{I(\theta)}) $が成り立つ。

定理6.10のスラツキーの定理より

\begin{equation}
  \sqrt{n}\sqrt{I(\hat{\theta})}(\hat{\theta}-\theta) \to_d N(0,1) 
\end{equation}

に収束することがわかる。

\begin{thm}
  スラツキーの定理

  
\end{thm}


したがって、定数$\theta_0$に対して$H_0:\theta = \theta_0 \quad vs. H_1: \theta \neq \theta_0$のような両側検定については、有意水準$\alpha$の近似的な棄却域は

\begin{equation}
  R=\left\{x|\sqrt{n}\sqrt{I(\hat{\theta})}|\hat{\theta}-\theta_0|>z_{\frac{\alpha}{2}}\right\}
\end{equation}

となる。このような検定をワルド検定と呼ぶ。

例9.6

$X_1,\dots,X_n$が独立にベルヌーイ分布$Ber(\theta)$に従う時、両側検定$H_0:\theta=\theta_0 \quad vs. \quad H_1: \theta \neq \theta_0$を考えてみよう。$\theta$のMLEは$\bar{X}$であり、フィッシャー情報量は$I(\theta)=\left[\theta(1-\theta)\right]^{-1}$となるので

\begin{equation*}
  \frac{\sqrt{n}(\bar{X}-\theta_0)}{\sqrt{\bar{X}(1-\bar{X})}} \to_d N(0,1)
\end{equation*}

のように近似できる。したがってワルド検定の近似的な棄却域は

\begin{equation*}
  R=\left\{x|\sqrt{n}|\bar{x}-\theta_0|> \sqrt{\bar{x}(1-\bar{x})}z_{\frac{\alpha}{2}}\right\}
\end{equation*}

とかける。

## 標本平均に基づいた検定


中心極限定理を持ちいれば標本平均に基づいた近似的な検定を行うことができる。$X_1,\dots,X_n$が独立に同一分布に従い、平均が$\mu$,分散が$\sigma^2$であるとし、特にパラメトリックな分布は仮定しない。定理6.7の中心極限定理より$\sqrt{n}(\bar{X}-\mu) \to_d N(0, \sigma^2)$に収束するので、$S^2=n^{-1} \sum_{i=1}^{n}(X_i-\bar{X})^2$とおくと、

\begin{equation*}
  \frac{\sqrt{n}(\bar{X}-\mu)}{S} \to_d N(0,1)
\end{equation*}

となる。したがって、あたえられた定数$\mu_0$に対して両側検定$H_0:\theta=\theta_0 \quad vs. \quad H_1: \theta \neq \theta_0$を考えると、ワルド型の検定の棄却域は次のように考えられる。


\begin{equation*}
  R=\left\{x|\sqrt{n}|\bar{x}-\mu_0|> S z_{\frac{\alpha}{2}}\right\}
\end{equation*}

例9.7 対のあるデータの同等性検定

夫婦の間で内閣支持率に差があるかを検定する問題を考える。夫の支持率を$\theta_1$,妻の支持率を$\theta_2$とし、$n$組の夫婦についてデータが取られたとする。$(X_1,Y_1),\dots,(X_n,Y_n)$が互いに独立で、

とすると、$E[X_i]=\theta_1$,$E[Y_i]=\theta_2$である。夫婦のペアについては$X_i,Y_i$が必ずしも独立とは限らない点に注意する。このとき両側検定$H_0:\theta=\theta_0 \quad vs. \quad H_1: \theta \neq \theta_0$を考える。

この問題は、$Z_i=X_i-Y_i$とおくと１標本の問題に帰着できる。$Z_i$の平均は$E[Z_i]=E[X_i]-E[Y_i]=\theta_1-\theta_2$であり、その分散を$\sigma^2=Var(Z_i)$とする。

$\bar{Z}=n^{-1} \sum_{i=1}^{n} Z_i$、$S^2=n^{-1} \sum_{i=1}^{n} (Z_i-\bar{Z})^2$とおくとき、$S^2 \to_p \sigma^2$より

\begin{equation*}
  \frac{\sqrt{n}\left\{(\bar{X}-\bar{Y})-(\theta_1-\theta_2)\right\}}{S} \to_d N(0,1)
\end{equation*}

が成り立つ。したがって、有意水準$\alpha$の近似的な棄却域は


\begin{equation*}
  R=\left\{(x,y)|\sqrt{n}|\bar{x}-\bar{y}|> S z_{\frac{\alpha}{2}}\right\}
\end{equation*}


で与えられる。

