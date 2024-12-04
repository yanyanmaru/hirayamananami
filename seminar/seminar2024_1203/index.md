---
title: "12月3日　ワルド型の検定"
code-fold: true
format:
  html:
    grid:
      margin-width: 350px         # <1>
reference-location: margin        # <2>
citation-location: margin         # <2>
date: 2024/12/3
toc: true
lang: ja
categories:
  - データ解析のための数理統計入門
status: "作成中"
---


# ワルド型検定


尤度比検定を中心に説明してきたが、近似的な検定手法を与える方法としてMLEや標本平均に基づいたワルド型の検定についてこの節で説明する。

## 最尤推定量に基づいた検定

$X_1,\dots,X_n$を独立にそれぞれパラメトリックな確率（密度）関数$f(x|\theta)$に従うとし、$\theta$を１次元のパラメーターとする。$\theta$のMLEを$\hat{\theta}$とすると、定理8.15より適当な正則条件のもとで$n \to \infty$のとき$\sqrt{n}(\hat{\theta}-\theta) \to _d N(0, \frac{1}{I(\theta)})$が成り立つ。

$\hat{\theta}$(MLE)の一致性により、$I(\hat{\theta}) \to_p I(\theta)$ に確率収束します。

また正規分布の性質(命題2.15)により、正規分布を$\frac{1}{\sigma}=\sqrt{I(\hat{\theta})}$倍して標準正規分布に変換します。

定理6.10のスラツキーの定理[^1]より

\begin{equation}
  \sqrt{n}\sqrt{I(\hat{\theta})}(\hat{\theta}-\theta) \to_d N(0,1) 
\end{equation}

に収束することがわかる。

[^1]: スラツキーの定理　<br> $U_n \to_d U$, $V_n \to_p \alpha$ とするとき、以下が成り立つ:
\begin{align*}
U_n + V_n &\to_d U + \alpha, \\
U_n V_n &\to_d \alpha U
\end{align*}

したがって、定数$\theta_0$に対して$H_0:\theta = \theta_0 \quad vs. H_1: \theta \neq \theta_0$のような両側検定については、有意水準$\alpha$の近似的な棄却域は

\begin{equation}
  R=\left\{x|\sqrt{n}\sqrt{I(\hat{\theta})}|\hat{\theta}-\theta_0|>z_{\frac{\alpha}{2}}\right\}
\end{equation}

となる。このような検定をワルド検定と呼ぶ。

### 例9.6

$X_1,\dots,X_n$が独立にベルヌーイ分布$Ber(\theta)$に従う時、両側検定$H_0:\theta=\theta_0 \quad vs. \quad H_1: \theta \neq \theta_0$を考えてみよう。$\theta$のMLEは$\bar{X}$であり、フィッシャー情報量は$I(\theta)=\left[\theta(1-\theta)\right]^{-1}$となる（例8.17参照）ので

\begin{equation*}
  \frac{\sqrt{n}(\bar{X}-\theta_0)}{\sqrt{\bar{X}(1-\bar{X})}} \to_d N(0,1)
\end{equation*}

のように近似できる。したがってワルド検定の近似的な棄却域は

\begin{equation*}
  R=\left\{x|\sqrt{n}|\bar{x}-\theta_0|> \sqrt{\bar{x}(1-\bar{x})}z_{\frac{\alpha}{2}}\right\}
\end{equation*}

とかける。

## 標本平均に基づいた検定


中心極限定理を用いれば標本平均に基づいた近似的な検定を行うことができる。$X_1,\dots,X_n$が独立に同一分布に従い、平均が$\mu$,分散が$\sigma^2$であるとし、特にパラメトリックな分布は仮定しない。


定理6.7の中心極限定理より$\sqrt{n}(\bar{X}-\mu) \to_d N(0, \sigma^2)$に収束する。標準正規分布の形にしたいので、$S^2=n^{-1} \sum_{i=1}^{n}(X_i-\bar{X})^2$とおき、$S^2 \to_p \sigma^2$ に確率収束するので、$S \to_p \sigma$に確率収束する。

また同様にスラツキーの定理より

\begin{equation*}
  \frac{\sqrt{n}(\bar{X}-\mu)}{S}\to_d  \frac{N(0,\sigma^2)}{\sigma} \sim N(0,1)
\end{equation*}

となる。したがって、あたえられた定数$\mu_0$に対して両側検定$H_0:\theta=\theta_0 \quad vs. \quad H_1: \theta \neq \theta_0$を考えると、ワルド型の検定の棄却域は次のように考えられる。


\begin{equation*}
  R=\left\{x|\sqrt{n}|\bar{x}-\mu_0|> S z_{\frac{\alpha}{2}}\right\}
\end{equation*}

### 例9.7 対のあるデータの同等性検定

夫婦の間で内閣支持率に差があるかを検定する問題を考える。夫の支持率を$\theta_1$,妻の支持率を$\theta_2$とし、$n$組の夫婦についてデータが取られたとする。$(X_1,Y_1),\dots,(X_n,Y_n)$が互いに独立で、


::: {layout-ncol=2}
$$
X_i =
\begin{cases}
1 & (\text{夫が支持する}) \\
0 & (\text{夫が支持しない})
\end{cases}
$$


$$
Y_i =
\begin{cases}
1 & (\text{妻が支持する}) \\
0 & (\text{妻が支持しない})
\end{cases}
$$

:::






とすると、$E[X_i]=\theta_1$,$E[Y_i]=\theta_2$である。夫婦のペアについては$X_i,Y_i$が必ずしも独立とは限らない点に注意する。このとき両側検定$H_0:\theta_1=\theta_2 \quad vs. \quad H_1: \theta_1 \neq \theta_2$を考える。

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

