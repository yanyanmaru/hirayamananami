---
title: "11月12日　7.4不偏推定の問題点"
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


### 不偏推定の問題点

以上で述べてきた、一様最小分散不偏推定量(UMVU)の理論は、標本平均のように直感的にもっともらしい推定量を理論的に裏付けるための有効な理論である。

もしUMVUが存在すればUMVUを用いることは説得性のあることと思われる。

しかしながら、一様最小分散不偏推定量が存在しなかったり不合理な推定量となる例がある。

これらの例は必ずしも特殊な例とは言えず、不偏推定量の理論に疑問を投げかけるものとなっている。

不偏推定量の理論は点推定論の中でも伝統的に大きな位置を占めてきたが、このような事情から不偏推定という考え方を重視しない学者も多い。

不偏推定の問題点として、母数の変換に対して不変ではないということがあげられる。

つまり$\hat{\theta}$が$\theta$の不偏推定量であったとしても、$\gamma(\hat{\theta})$は$\gamma(\theta)$の不偏推定量ではないのである。この例として、母分散・母標準偏差の推定を考えてみよう。

---

### 不偏推定の問題点を示す例


$\displaystyle s^2=\sum^{n}_{i=1}\frac{(X_i - \bar{X})^2}{n-1}$ は$\sigma^2$の不偏推定量であるが、$s=\sqrt{s^2}$は$\sigma$の不偏推定量にはならない。

<br/>

実際ジェンセンの不等式より、$E[s] < \sigma$となることが容易に示される。

<br/>

---

### 補足：ジェンセンの不等式

::: {#thm-line}

<br/>

$f(x)$を１変数の凸関数とする。このとき

$$
f(E[X]) \leq E[f(X)]
$$


が成り立つ。ただし$E[X]$は存在するものとする。

:::



証明

$\mu = E[X]$ とする。$(\mu, f(\mu))$ における$f(x)$の接線を$y=a+bx$とする。$f(x)$は凸関数であるから

$$
f(x) \geq a  + bx , \quad \forall x 
$$

が成り立つ。ここで両辺の期待値をとれば$E[f(X)] \geq  a+b\mu=f(\mu)=f(E[X])$である。

もしfが厳密な凸関数で、$P(X \neq \mu) > 0$ ならば強い不等式が成り立つ。



---

### 不偏推定の問題点を示す例

$f(x)=\sqrt{x}$　は厳密に上に凸である。

ジェンセンの不等式より、$(E[s])^2 < E[s^2]$ である。両辺に平方根をとっても大小関係は変わらないため、$\sqrt{(E[s])^2 }< \sqrt{E[s^2]}$　である。これを用いて、





$$
E[s] = E[\sqrt{s^2}] < \sqrt{E[s^2]} = \sqrt{\sigma^2} = \sigma
$$


となる。$E[s] \neq \sigma$ であるため、不偏推定量ではない。

---

### 不偏推定の問題点を示す例

また**正規母集団**からの標本の場合に

$$
\tilde{\sigma} = s \frac{\sqrt{n-1} \Gamma(\frac{n-1}{2})}{\sqrt{2} \Gamma(\frac{n}{2})}
$$

が$\sigma$の不偏推定量であることも示される。

<br/>

不偏推定量であるということは、$E[\tilde{\sigma}] = E[s \frac{\sqrt{n-1} \Gamma(\frac{n-1}{2})}{\sqrt{2} \Gamma(\frac{n}{2})}] = \sigma$ である。つまり、


$$
E[s] = \sigma \frac{\sqrt{2} \Gamma(\frac{n}{2})}{\sqrt{n-1} \Gamma(\frac{n-1}{2})}
$$

であることを示したい。（次のページへ）

---

### 不偏推定の問題点を示す例

$\displaystyle \frac{\sum_{i=1}^n(X_i-\bar{X})^2}{\sigma^2} = \frac{(n-1)s^2}{\sigma^2} \sim \chi^{2}_{n-1}$を用いる。（**正規母集団**のため）

<br/>

$\displaystyle Y=\frac{(n-1)s^2}{\sigma^2}$ とおいて、$Y \sim \chi^{2}_{n-1}$ から、$E[s]= \int^{\infty}_0 \sqrt{\frac{\sigma^2}{n-1}y} f(y) dy$ より期待値を求めれる。

<br/>



$$
E[s] = \int^{\infty}_0 \sqrt{\frac{\sigma^2}{n-1}y} \frac{y^{\frac{n-1}{2} - 1} e^{- \frac{y}{2}}}{\Gamma(\frac{n-1}{2}) 2^{\frac{n-1}{2}}} dy = \sqrt{\frac{\sigma^2}{n-1}} \frac{\Gamma(\frac{n}{2}) 2^{\frac{n}{2}}}{\Gamma(\frac{n-1}{2}) 2^{\frac{n-1}{2}}} =  \sigma \frac{\sqrt{2} \Gamma(\frac{n}{2})}{\sqrt{n-1} \Gamma(\frac{n-1}{2})}
$$

<br/>

補足：自由度$n$のカイ二乗分布に従う時、$Ga(\frac{n}{2},2)$ に従う。


---


### 不偏推定の問題点を示す例


したがって、もし不偏推定の考え方にこだわるのであれば$\sigma^2$の推定には$s^2$ を用いるが、$\sigma$の推定には$\tilde{\sigma}$を用いなければならなくなる。

しかしこれは明らかに不自然な推定方法であろう。

したがってこの場合不偏推定の基準を厳密に適用することは不合理である。


