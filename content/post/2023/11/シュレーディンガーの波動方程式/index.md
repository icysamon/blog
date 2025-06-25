---
date : 2023-11-14T13:22:00+09:00
draft : false
title : シュレーディンガーの波動方程式
categories :
    - 半導体
description : シュレーディンガーの波動方程式とは、物理学の量子力学における基礎方程式である。
---

## 時間に依存するシュレーディンガー方程式

$$i\hslash\frac{d}{dt}|\Psi(t)\rangle=\hat{H}|\Psi(t)\rangle$$

なぜならば

$$E=\frac{P^2}{2m}+V=H$$

ポテンシャルエネルギー \(V\)

すなわち

**1次元**の場合は

$$j\hslash\frac{\partial\Psi}{\partial t}=-\frac{\hslash^2}{2m}\frac{\partial^2\Psi}{\partial x^2}+V\Psi$$

**3次元**の場合は

$$i\hslash\frac{\partial}{\partial t}\Psi(x,t)=\Biggl[\frac{-\hslash^2}{2m}\nabla^2+V(x,t)\Biggr]\Psi(x,t)$$

### ハミルトニアン H

#### 解析力学（古典力学）

$$H=H(q,p;t)=T+V$$

- 運動エネルギー \(T\)
- ポテンシャルエネルギー \(V\)
- 一般化座標 \(q\)
- 一般化運動量 \(p\)

時間 \(t\)

#### 量子力学

これは古典力学におけるハミルトニアンの技術的な定義ではありませんが、これが最も一般的に取られる形式です。これらを組み合わせると、シュレーディンガー方程式で使用される形式が得られます。

$$
\begin{equation}
\begin{aligned}
\hat{H} =\hat{T}+\hat{V} =\frac{\hat{P}\cdotp\hat{P}}{2m}+V(r,t) =-\frac{\hslash^2}{2m}\nabla^2+V(r,t)
\end{aligned}
\end{equation}
$$

### ディラック定数

$$
\begin{equation}
\begin{aligned}
\hslash\equiv\frac{h}{2\pi} =1.054 571 817…\times 10^{-34}J\cdotp s =6.582119569…\times 10^{-16}eV\cdotp s
\end{aligned}
\end{equation}
$$

#### 物理的意義

$$E=h\nu=\frac{h}{2\pi}\cdotp 2\pi\nu =\hslash\omega$$

$$P=\frac{h}{\lambda}=\frac{h}{2\pi}\frac{2\pi}{\lambda} =\hslash k$$

### ラプラシアン

$$\nabla^2=\frac{\partial^2}{\partial x^2}+\frac{\partial^2}{\partial y^2}+\frac{\partial^2}{\partial z^2}$$

## 時刻を含まないシュレーディンガーの波動方程式

$$-\frac{\hslash^2}{2m}\frac{d^2\varphi (x)}{dx^2}+\lbrace V(x)-E\rbrace\varphi (x)=0$$

- エネルギー固有値 \(E\)
- 固有関数 \(φ(x)\)

$$\Psi(x,t)=\varphi (x)Cexp\Biggl(-j\frac{E}{\hslash}t\Biggr )$$

\(\varphi(x)\)は\(\Psi(x,t)\)の**振幅**を決める

## 確率密度

$$P_r=\Psi^*\cdotp\Psi=|\Psi|^2$$

\(\intop_V\Psi^*\cdotp\Psi dxdydz=1\) を満足する波動関数を、**1に規格化された波動関数**という。