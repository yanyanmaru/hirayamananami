---
title: "12月10日　10.1.3"
code-fold: true
header-includes:
    - \usepackage{bm}
format:
  html:
    grid:
      margin-width: 350px         # <1>
reference-location: margin        # <2>
citation-location: margin         # <2>
date: 2024/12/10
toc: true
lang: ja
categories:
  - データ解析のための数理統計入門
status: "作成中"
---

# 10.1.3 尤度比検定とカイ2乗適合度検定

### この章でやること

カイ2乗適合度検定は多項分布に基づいた仮説検定であることを学んだ。
しかし、カイ2乗適合度検定の形や自由度についてもう少し説得力のある説明をする。（なぜカイ2乗に近似できるのかを証明する）
ここでは、9.10の尤度比検定とカイ2乗適合度検定との関係について調べてみることにする。


<br />

### 前提

確率変数$\mathbf{X}=(X_1,\dots,X_m)$が多項分布$Mult_m(n,\mathbf{p})$に従うとする。ただし$\mathbf{p}=(p_1,\dots,p_m)$であり、$p_1+\dots+p_m=1$,$X_1+\dots+X_m=n$を満たしているとする。

より一般的な仮説検定は

$H_0:p_1=p_1(\mathbf{\theta}),\dots,p_m=p_m(\mathbf{\theta}) \quad vs. H_1:あるiに対してp_i \neq p_i(\mathbf{\theta})$


と表すことができる。ここで、$\mathbf{\theta} =(\theta_1, \dots, \theta_k)$,$k < m$は未知のパラメーターであり、帰無仮説$H_0$は$p_i$が$\theta$の既知の関数を用いて$p_i(\theta)$で与えられることを示している。

<br />

### 10.1.1、10.1.2に当てはめると...


例えば、10.1.1項の帰無仮説は$k=0$で$\pi(\theta)=\pi_i$が定数の場合に対応している。（$k=0$は未知のパラメーターがないこと。）

10.1.2項の帰無仮説は$m=4,k=2,p_{11}=\theta_1\theta_2$、$p_{12}=\theta_1(1-\theta_2)$,$p_{21}=(1-\theta_1)\theta_2$,$p_{22}=(1-\theta_1)(1-\theta_2)$に対応している。（$2 \times 2$のクロス表で$m=4$、$\theta_1,\theta_2$という未知のパラメーターが２つある。）

<br />


### 尤度比検定

制約無しの時の$\mathbf{p}$ のMLEは例8.13より$\mathbf{\hat{p}} =(\hat{p_1},\dots,\hat{p_m})$,$\hat{p_i}=\frac{X_i}{n}$となる。




帰無仮説$H_0$のもとでの$\theta$のMLE $\mathbf{\hat{\theta}}$ は

$$
L(p(\theta)\mid X)=\frac{n!}{X_1!\dots X_m!} \left\{p_1(\theta) \right\}^{X_i} \dots \left\{p_m(\theta) \right\}^{X_m}
$$


を最大化する解として与えられるので、(9.10)の尤度比は


$$
\Lambda(\mathbf{X})=\frac{L(p(\hat{\theta})\mid X)}{L(\hat{p}\mid X)} = \Pi^m_{i=1} \left(\frac{p_i(\hat{\theta})}{\hat{p_i}}\right)^{X_i}
$$

とかける。$X_i=n\hat{p_i}$より次のように表すことができる。

$$
-2 \log \Lambda(\mathbf{X}) = 2n\sum_{i=1}^m \hat{p_i} \log \left(\frac{\hat{p_i}}{p_i(\hat{\theta})}\right)
$$


<br />

ここで$\log(x)$を$x=x_0$の周りでテーラー展開すると

$$
\log(x) \approx \log(x_0)+\frac{1}{x_0}(x-x_0)-\frac{1}{2x_0^2}(x-x_0)^2
$$

で近似することができる。

$$
\begin{aligned}
  x\log(\frac{x}{x_0}) &= x \left\{\log(x_0)+\frac{1}{x_0}(x-x_0)-\frac{1}{2x_0^2}(x-x_0)^2\right\} - x\log(x_0) \\
  &= \frac{x}{x_0} (x-x_0)-\frac{x}{2x_0^2}(x-x_0)^2 \\
  &= \frac{x-x_0+x_0}{x_0} (x-x_0)-\frac{x}{2x_0^2}(x-x_0)^2 \\
  &= \frac{(x-x_0)^2}{x_0}+(x-x_0)-\frac{x-x_0+x_0}{2x_0^2}(x-x_0)^2 \\
  &= \frac{(x-x_0)^2}{x_0}+(x-x_0)-\frac{(x-x_0)^3}{2x_0^2}-\frac{(x-x_0)^2}{2x_0} \\
  &= (x-x_0)+\frac{(x-x_0)^2}{2x_0}-\frac{(x-x_0)^3}{2x_0^2} \\
  & \approx (x-x_0)+ \frac{1}{2x_0}(x-x_0)^2
\end{aligned}
$$

のような形で近似できる。$H_0$のもとでは$\hat{p_i}-p_i(\hat{\theta})$ は0に確率収束するので、



$x=\hat{p_i},x_0=p_i(\hat{\theta})$ としてこの近似式を用いると


$$
\begin{aligned}
  -2 \log \Lambda(\mathbf{X}) &= 2n\sum_{i=1}^m \hat{p_i} \log \left(\frac{\hat{p_i}}{p_i(\hat{\theta})}\right) \\
  &\approx 2n\sum_{i=1}^m \left\{(\hat{p_i}-p_i(\hat{\theta}))+ \frac{1}{2p_i(\hat{\theta})}(\hat{p_i}-p_i(\hat{\theta}))^2 \right\}\\
  &= 2n\sum_{i=1}^m (\hat{p_i}-p_i(\hat{\theta}))+ n\sum_{i=1}^m \frac{(\hat{p_i}-p_i(\hat{\theta}))^2}{p_i(\hat{\theta})} \\
  &= n\sum_{i=1}^m \frac{(\hat{p_i}-p_i(\hat{\theta}))^2}{p_i(\hat{\theta})}
\end{aligned}
$$


となり、カイ2乗適合度検定が現れる。あらためて$O_i=X_i, E_i=np_i(\hat{\theta})$とおくと、$H_0$のもとで次のような関係が成り立つことになる。




$$
\begin{aligned}
  -2 \log \Lambda(\mathbf{X}) &= 2\sum_{i=1}^m O_i \log \left(\frac{O_i}{E_i}\right)\approx  \sum_{i=1}^m  \frac{(O_i-E_i)^2}{E_i}
\end{aligned}
$$


制約無しの時のパラメーター数は$m-1$,$H_0$のもとでのパラメーター数は$k$であることを注意すると、定理9.3より尤度比検定は$H_0$のもとで$\chi^2_{m-k-1}$に収束することがわかる。

したがってカイ2乗適合度検定は自由度$m-k-1$のカイ二乗分布から棄却限界を求めることができる。

<br />

### 10.1.1、10.1.2に当てはめると...


例えば、10.1.1項の帰無仮説は$k=0$なので自由度は$m-1$となる。

10.1.2項の$r\times c$のクロス表については$m=cr,k=c+r-2$に対応するので、自由度は$m-k-1=cr-(c+r-2)-1=cr-c-r+1=(c-1)(r-1)$となる。

