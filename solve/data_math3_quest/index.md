---
title: "「データ解析のための数理統計入門」第3章 演習問題 解答"
format: html
code-fold: true
date: last-modified
toc: true
lang: ja
categories:
  - 統計
  - データ解析のための数理統計入門
status: "作成中"
---

# １問目

## 問題概要

$X,Y$が確率変数で、1~4を２回やるときの和と差に対応。

### 小問1
$f(4,0), f(5,3)$ を求める。

### 小問2
$f_X(6),f_Y(2)$ を求める。

### 小問3
$f_{Y|X}(2|4),f_{X|Y}(5|1)$

## 回答

### 小問1


$$
f(4,0)=P(X=4,Y=0) = \frac{1}{16}
$$

$$
f(5,3)=P(X=5,Y=3) = \frac{2}{16} = \frac{1}{8}
$$

### 小問2

$$
f_X(6)= f(6,0)+f(6,1)+f(6,2)+f(6,3)= \frac{1}{16} + 0 + \frac{2}{16} + 0 =\frac{3}{16}
$$

$$
f_Y(2)= f(2,2)+f(3,2)+f(4,2)+f(5,2)+f(6,2)+f(7,2)+f(8,2)= 0+ 0+ \frac{2}{16}+0+\frac{2}{16}+0+0=\frac{1}{4}
$$


### 小問3

$$
f_{Y|X}(2|4)=\frac{f(4,2)}{f_X(4)}=\frac{f(4,2)}{f(4,0)+f(4,1)+f(4,2)+f(4,3)} =\frac{2/16}{1/16+2/16}=\frac{2}{3}
$$

$$
f_{X|Y}(5|1) = \frac{f(5,1)}{f_Y(1)}= \frac{f(5,1)}{f(2,1)+f(3,1)+f(4,1)+f(5,1)+f(6,1)+f(7,1)+f(8,1)} = \frac{2/16}{2/16+2/16+2/16}= \frac{1}{3}
$$

# 2問目

## 問題概要

多項分布について。

### 小問1

多項分布の周辺分布は二項分布か、周辺分布の和の分布はどうなるか。



### 小問2

$X_1$ を与えた時の、$X_2$の条件付き確率。



### 小問3

$X_1+X_2$ を与えた時の$X_2$ の条件付き確率。



## 回答

### 小問1

多項分布は多次元の確率変数で、$1$から$m$ の番号が書かれた多面体を$n$ 回投げる時に、それぞれの面が出る確率を$p_1,p_2,\dots,p_m=1$ とし、$X_1+X_2+ \dots + X_m=n$ である分布。

$X_i$ の周辺分布は$i$　番目が出るか出ないかであり、$Bin(n,p_i)$となるし、$X_i+X_j$ の周辺分布は$i$番目もしくは$j$　番目が出るか出ないかなので$Bin(n,p_i+p_j)$ である。

サイコロで考えてみるとわかりやすいかも。

### 小問2

求めたいのは$\frac{P(X_1=x_1,X_2=x_2)}{P(X_1=x_1)}$ である。それぞれ、

$$
P(X=x_1)= \frac{n!}{x_1!(n-x_1)!} p_1^{x_1}(1-p_1)^{n-x_1}
$$


$$
P(X_1=x_1,X_2=x_2)= \frac{n!}{x_1!x_2!(n-x_1-x_2)!}p_1^{x_1} p_2^{x_2}(1-p_1-p_2)^{n-x_2}
$$

よって

$$
\begin{aligned}
\frac{P(X_1=x_1,X_2=x_2)}{P(X_1=x_1)}
=\frac{\frac{n!}{x_1!x_2!(n-x_1-x_2)!}p_1^{x_1} p_2^{x_2}(1-p_1-p_2)^{n-x_2}}{\frac{n!}{x_1!(n-x_1)!} p_1^{x_1}(1-p_1)^{n-x_1}} \\
= \frac{(n-x_1)!}{x_2!(n-x_1-x_2)!} (\frac{p_2}{1-p_1})^{x_2} (\frac{1-p_1-p_2}{1-p_1})^{n-x_1-x_2}
\end{aligned}
$$


これによって条件付き確率は二項分布$Bin(n-x_1,\frac{p_2}{1-p_1})$ に従う。

直感的にも、例えばサイコロを１０回投げるとして1の目が２回出たことを知っていたら、2の目が出る確率は試行回数が8回で2~6の1/5の確率で出る二項分布というのはしっくりきます。

### 小問3

求めたいのは$\frac{P(X_2=x_2)}{P(X_1+X_2=z)}=\frac{P(X_2=x_2)}{P(X_1+X_2=x_1+x_2)}$ である。

(変数$x_2$が与えられれば$x_1$は自ずと決まるので、$x_1$を使う。)

それぞれ

$$
P(X_1+X_2=x_1+x_2)=\frac{n!}{(x_1+x_2)!(n-x_1-x_2)!}(p_1+p_2)^{x_1+x_2}(1-p_1-p_2)^{n-x_1-x_2}
$$

$$
P(X_2=x_2,X_1+X_2=x_1+x_2)=P(X_1=x_1,X_2=x_2)= \frac{n!}{x_1!x_2!(n-x_1-x_2)!}p_1^{x_1} p_2^{x_2}(1-p_1-p_2)^{n-x_2}
$$


$$
\begin{aligned}
\frac{P(X_2=x_2)}{P(X_1+X_2=x_1+x_2)}=\frac{\frac{n!}{x_1!x_2!(n-x_1-x_2)!}p_1^{x_1} p_2^{x_2}(1-p_1-p_2)^{n-x_1-x_2}}{\frac{n!}{(x_1+x_2)!(n-x_1-x_2)!}(p_1+p_2)^{x_1+x_2}(1-p_1-p_2)^{n-x_1-x_2}} \\
=\frac{(x_1+x_2)!}{x_1!x_2!} (\frac{p_2}{p_1+p_2})^{x_2}(\frac{p_1}{p_1+p_2})^{x_1}
\end{aligned}
$$

よって条件付き分布は二項分布$Bin(z,\frac{p_2}{p_1+p_2})$ に従う。

これもサイコロで例えると、１の目が出た回数と2の目が出た回数が合計4回だと知っているとき、2の目が出る確率は試行回数4回で1/2の二項分布の確率になりそうですよね。


# 3問目

## 問題概要

$X,Y$ がそれぞれポアソン分布に従う。

### 小問1
$Z=X+Y$ の分布を求めよ。

### 小問2

$X+Y=n$に固定した時、$X$ の条件付き分布を求める。

## 回答


### 小問1


再生性からと言いたいところですが、誘導に乗ってみます。（離散確率の変数変換の方法ってどこかに載ってたかな）

$X=x$ という実現値を取る時、$Y$ は自ずと$n-x$ という実現時をとる。$X$ と$Y$ は独立であり、同時確率は積であらわすことができるため、

$$
P(X+Y=n) = \sum_{x=0}^n P(X=x)P(Y=n-x)
$$


と表せる。これを計算すると


$$
\begin{aligned}
\sum_{x=0}^n P(X=x)P(Y=n-x) &= \sum_{x=0}^n\frac{\lambda_1^x}{x!}e^{-\lambda_1}\frac{\lambda_2^{n-x}}{(n-x)!}e^{-\lambda_2} \\
&=\frac{(\lambda_1+\lambda_2)^n}{n!} e^{-(\lambda_1+\lambda_2)} \sum_{x=0}^n\frac{n!}{x!(n-x)!} \left(\frac{\lambda_1}{\lambda_1+\lambda_2}\right)^x \left(\frac{\lambda_2}{\lambda_1+\lambda_2}\right)^{n-x} \\
&=\frac{(\lambda_1+\lambda_2)^n}{n!} e^{-(\lambda_1+\lambda_2)}
\end{aligned}
$$


$\displaystyle \sum_{x=0}^n\frac{n!}{x!(n-x)!} \left(\frac{\lambda_1}{\lambda_1+\lambda_2}\right)^x \left(\frac{\lambda_2}{\lambda_1+\lambda_2}\right)^{n-x}$ は嬉しいことに、二項分布$\displaystyle Bin(n,\frac{\lambda_1}{\lambda_1+\lambda_2})$ に従う分布の全確率？（用語があっているかわからない）なので1になります。

$X+Y=n$ という確率変数が従う分布は$Po(\lambda_1+\lambda_2)$ になります。

例えば$X \sim Po(2)$,$Y \sim Po(3)$ なら$X+Y \sim Po(5)$ になるみたいなことですね。


### 小問2

求めたいのは$\displaystyle \frac{P(X+Y=n,X=x)}{P(X+Y=n)}$ である。

また$P(X+Y=n,X=x)=P(X=x,Y=n-x)$ とも表せれるので、

$$
\begin{aligned}
  \frac{P(X=x,Y=n-x)}{P(X+Y=n)} &=\frac{\frac{\lambda_1^x}{x!}e^{-\lambda_1}\frac{\lambda_2^{n-x}}{(n-x)!}e^{-\lambda_2}}{\frac{(\lambda_1+\lambda_2)^n}{n!} e^{-(\lambda_1+\lambda_2)}} \\
  &=\frac{n!}{x!(n-x)!} \left(\frac{\lambda_1}{\lambda_1+\lambda_2}\right)^x \left(\frac{\lambda_2}{\lambda_1+\lambda_2}\right)^{n-x}
\end{aligned}
$$

綺麗に二項分布$\displaystyle Bin(n,\frac{\lambda_1}{\lambda_1+\lambda_2})$に従います！

ちなみに統計検定準１級の勉強でも出てきました。

# 4問目

## 問題概要

$f(x,y)=xe^{-x(y+1)} I(x > 0,y>0)$ の周辺確率、条件確率、$P(XY > 1)$ を計算。

## 回答

$$
\begin{aligned}
  f_X(x) 
  &= \int^{\infty}_{0} xe^{-x(y+1)} dy \\
  &= xe^{-x} \int^{\infty}_{0} e^{-xy} dy \\
  &= xe^{-x} \left[-\frac{1}{x}e^{-xy}\right]^{\infty}_{y=0} \\
  &= e^{-x}
\end{aligned}
$$

$$
\begin{aligned}
  f_Y(y) 
  &= \int^{\infty}_{0} xe^{-x(y+1)} dx \\
  &= \frac{1}{(y+1)^2} \int^{\infty}_{0} \frac{1}{\Gamma(2) (y+1)^{-2}} xe^{-x(y+1)} dx \\
  &= \frac{1}{(y+1)^2} 
\end{aligned}
$$

$xe^{-x}$ みたいな形を見つけたら、ガンマ関数の式に持っていくのがよくある計算だと感じてきた。

$xe^{-x(y+1)}$から$\alpha=2,\beta=(y+1)^{-1}$ にしたら都合がよさそうなことから、この変形をしている。

$$
\begin{aligned}
f_{X|Y}(x|y)
&= \frac{f(x,y)}{f_Y(y)} \\
&= \frac{xe^{-x(y+1)} }{(y+1)^{-2} } \\
&= \frac{1}{\Gamma(2)(y+1)^2} x^{2-1} e^{-(y+1)x}
\end{aligned}
$$

３つ目の等式はガンマ分布に落ち着きそうな気配を察して、$\Gamma(2)=1$を入れている。

よって

$$
X|Y=y \sim Ga(2,(y+1)^{-1})
$$

となる。

$$
\begin{aligned}
f_{Y|X}(y|x)
&= \frac{f(x,y)}{f_X(x)} \\
&= \frac{xe^{-x(y+1)} }{e^{-x}} \\
&= xe^{-xy}
\end{aligned}
$$

一瞬見慣れないと思いきや、$y$ の関数で$x$はすでに与えられているパラメーターです。すると指数分布$Ex(x)$に従うことがわかります。

$$
\begin{aligned}
  P(XY>1) &= \int^{\infty}_{0} \int^{\infty}_{\frac{1}{x}} xe^{-x(y+1)} dy dx \\
  &= \int^{\infty}_{0} x e^{-x} \\
  &= \frac{1}{e}
\end{aligned}
$$

$\int^{\infty}_{0} \int^{\infty}_{\frac{1}{x}}$ がしっくりきてない。なんとなくそうな気はするけど、$\int^{\infty}_{\frac{1}{y}} \int^{\infty}_{\frac{1}{x}}$ じゃだめなのかがわからない。

# 7問目

ゼミでやったことがあるので飛ばします。