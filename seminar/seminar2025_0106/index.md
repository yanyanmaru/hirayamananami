---
title: "1月7日　12.4前半"
code-fold: true
format:
  html:
    grid:
      margin-width: 350px         # <1>
reference-location: margin        # <2>
citation-location: margin         # <2>
date: 2024/01/07
toc: true
lang: ja
categories:
  - データ解析のための数理統計入門
status: "作成中"
---

##  変数選択の方法

説明変数の個数を増やしていくとデータによく当てはまるモデルができるが、利用したデータだけにはよく適合するものの、同じモデルから発生する新たなデータへの予測は良くないという問題が生じる。これは**過学習**もしくは**過剰適合** と呼ばれる。そこでモデルの汎化性能を担保するために予測誤差を小さくするような変数選択の方法などが考えられてきた。ここでは代表的な変数選択手法を紹介する。

### 重相関係数と決定係数

単回帰モデルにおいて、回帰モデルがデータにどの程度当てはまっているかを調べる方法として決定係数を取り上げた。重回帰モデルにおいても、$y_i$を回帰式$y = \hat{\beta}_0 + \hat{\beta}_1 x_{1} + \cdots + \hat{\beta}_{k-1} x_{k-1}$を用いて
$$
\hat{y}_i = \hat{\beta}_0 + \hat{\beta}_1 x_{1i} + \cdots + \hat{\beta}_{k-1} x_{k-1,i}
$$
で予測することになるので、$(y_i, \hat{y}_i), \, i = 1, \dots, n$の相関係数を当てはまりを測る尺度として利用することができる。

重回帰モデルにおいては、相関係数
$$
R = \frac{\sum_{i=1}^n (\hat{y}_i - \bar{y})(y_i - \bar{y})}{\left\{\sum_{i=1}^n (\hat{y}_i - \bar{y})^2 \sum_{i=1}^n (y_i - \bar{y})^2\right\}^{1/2}}\tag{12.14}
$$
を**重相関係数** と呼ぶ。

決定係数（$R$-square）$R^2$は単回帰の場合と同様にして
$$
\begin{aligned}R^2 &=\frac{(\sum_{i=1}^n (\hat{y}_i - \bar{y})(y_i - \bar{y}))^2}{\sum_{i=1}^n (\hat{y}_i - \bar{y})^2 \sum_{i=1}^n (y_i - \bar{y})^2} \\
&= \frac{(\sum_{i=1}^n (\hat{y}_i - \bar{y})^2)^2}{\sum_{i=1}^n (\hat{y}_i - \bar{y})^2 \sum_{i=1}^n (y_i - \bar{y})^2}  \\
&= \frac{\sum_{i=1}^n (\hat{y}_i - \bar{y})^2 }{\sum_{i=1}^n (y_i - \bar{y})^2} \\
&= 1 - \frac{\sum_{i=1}^n (y_i - \hat{y}_i)^2}{\sum_{i=1}^n (y_i - \bar{y})^2} \end{aligned}\tag{12.15}
$$
と表すことができる。

1. $(\sum_{i=1}^n (\hat{y}_i - \bar{y})(y_i - \bar{y}))^2 =(\sum_{i=1}^n (\hat{y}_i - \bar{y})^2)^2$ となる理由

   1. $\sum_{i=1}^n (\hat{y}_i - \bar{y})(y_i - \bar{y})=\sum_{i=1}^n (\hat{y}_i - \bar{y})^2$ となればよい

   2. $$
      \sum_{i=1}^n (\hat{y}_i - \bar{y})(y_i - \bar{y}) \\
      = \sum_{i=1}^n(\hat{y_i}-\bar{y})\left\{(\hat{y_i}-\bar{y})-(\hat{y_i} -y_i) \right\} \\
      =\sum_{i=1}^n (\hat{y}_i - \bar{y})^2 -\sum_{i=1}^n (\hat{y}_i - \bar{y})(\hat{y_i} -y_i)\\
      =\sum_{i=1}^n (\hat{y}_i - \bar{y})^2
      $$

   3. 3つ目の等式が成り立つためには$\sum_{i=1}^n (\hat{y}_i - \bar{y})(\hat{y_i} -y_i)=0$ になると嬉しい

2. $\displaystyle \frac{\sum_{i=1}^n (\hat{y}_i - \bar{y})^2 }{\sum_{i=1}^n (y_i - \bar{y})^2} =1 - \frac{\sum_{i=1}^n (y_i - \hat{y}_i)^2}{\sum_{i=1}^n (y_i - \bar{y})^2}$ となる理由

   1. $$
      \sum_{i=1}^n (y_i - \bar{y})^2  = \sum_{i=1}^n (\hat{y_i} - \bar{y} +y_i-\hat{y_i})^2 \\
      = \sum_{i=1}^n (\hat{y_i} - \bar{y})^2  + \sum_{i=1}^n (y_i - \hat{y_i})^2 + 2\sum_{i=1}^n (\hat{y_i} - \bar{y})(y_i - \hat{y_i}) \\
      = \sum_{i=1}^n (\hat{y_i} - \bar{y})^2  + \sum_{i=1}^n (y_i - \hat{y_i})^2
      $$

   2. $$
      \frac{\sum_{i=1}^n (\hat{y}_i - \bar{y})^2}{\sum_{i=1}^n (\hat{y_i} - \bar{y})^2  + \sum_{i=1}^n (y_i - \hat{y_i})^2} \\
      =\frac{\sum_{i=1}^n (\hat{y}_i - \bar{y})^2+\sum_{i=1}^n (y_i - \hat{y_i})^2-\sum_{i=1}^n (y_i - \hat{y_i})^2}{\sum_{i=1}^n (\hat{y_i} - \bar{y})^2  + \sum_{i=1}^n (y_i - \hat{y_i})^2} \\
      =1 - \frac{\sum_{i=1}^n (y_i - \hat{y}_i)^2}{\sum_{i=1}^n (y_i - \bar{y})^2}
      $$




例えば、表12.1のデータの解析について、次の4つのモデルを考えてみる。
$$
\begin{aligned}M_0  &: y_i = \beta_0 + \beta_1 x_{1i} + \beta_2 x_{2i} + u_i, \\

M_1 & : \log(y_i) = \beta_0 + u_i, \\

M_2  &: \log(y_i) = \beta_0 + \beta_1 \log(x_{1i}) + u_i, \\

M_3  &: \log(y_i) = \beta_0 + \beta_1 \log(x_{1i}) + \beta_2 \log(x_{2i}) + u_i \end{aligned}
$$
各モデルにおける回帰直線は
$$
\begin{aligned}
M_0&:  y = 550.57 - 3.75 x_1 - 0.65 x_2,  \\
M_1&:  \log(y) = 5.71, \\

M_2 &: \log(y) = 8.05 - 0.62 \log(x_1), \\

M_3 &: \log(y) = 8.30 - 0.56 \log(x_1) - 0.12 \log(x_2)\end{aligned}
$$
で与えられる。それぞれの決定係数を求めると、$M_0$: 0.626, $M_1$: 0.681, $M_3$: 0.738となる。決定係数が大きくなるほど重回帰モデルのデータへの適合がよいと考えられるので、4つのモデルの中では対数変換した重回帰モデル(M3)がデータへの当てはまりがよいと思われる。

説明変数の個数を増やしていくと決定係数$R^2$が1に近づいていくことが数値的に確認できる。しかし、$k$が増えるにつれて未知母数である回帰係数の個数が増えることになり、回帰係数の推定量の推定精度が悪くなる。また$\sigma^2$の推定量$\hat{\sigma}^2$の自由度は$n-k$であるが、$k$の増加とともに自由度が減少し、その結果$\hat{\sigma}^2$の推定精度も低くなる。したがって、説明変数の個数を増やすことはモデルの適合度を高くするものの、「モデルの良さ」を考えた場合、必ずしもよいとは限らない。そこで、説明変数$x_{1,i}, \dots, x_{k-1,i}$のうちどの変数を選択するかが重要な問題となる。以下では代表的な変数選択の方法を紹介する。

### 自由度調整済み決定係数

(12.14)の決定係数の中に現れる統計量について、$\sum_{i=1}^n (y_i - \hat{y}_i)^2, \sum_{i=1}^n (y_i - \bar{y})^2$をそれらの自由度$n-k, n-1$で割ったものの
$$
R_k^{*2} = 1 - \frac{\sum_{i=1}^n (y_i - \hat{y}_i)^2 / (n-k)}{\sum_{i=1}^n (y_i - \bar{y})^2 / (n-1)} \tag{12.16}
$$
を自由度調整済み決定係数（adjusted R-square）と呼ぶ。これを書き直すと
$$
R_k^{*2} = 1 - \frac{n-1}{n-k}(1 - R^2)
$$
となる。$R^2= 1 - \frac{\sum_{i=1}^n (y_i - \hat{y}_i)^2}{\sum_{i=1}^n (y_i - \bar{y})^2}$ なので。

この形からわかるように、$k$が大きくなると、$1-R^2$が小さくなるものの分母の$n-k$も小さくなるので、$R_k^{*2}$は必ずしも1に近づかない。分母の$n-k$は母数が多くなることに対するペナルティとして機能しており、自由度調整済み決定係数$R_k^{*2}$を最大にする説明変数の組を選ぶことになる。

表12.1のデータについて(12.15)の回帰モデルの自由度調整済み決定係数を求めると、$M_0$: 0.598, $M_1$: 0.670, $M_3$: 0.718となり、対数変換した重回帰モデル$M_3$が選ばれる。