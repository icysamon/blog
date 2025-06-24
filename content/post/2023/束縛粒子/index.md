+++
date = '2023-11-15T12:58:00+09:00'
draft = false
title = '束縛粒子'
categories = [ "半導体" ]
description = '量子井戸とは、電子の移動方向が束縛された状態のこと。'
+++

## 量子井戸(quantum well)

電子の移動方向が束縛された状態のこと。

![](https://image.icysamon.jp/%E9%87%8F%E5%AD%90%E4%BA%95%E6%88%B8.webp)

## 境界条件

\(x=0\) の点で　\(φ(0)=0\)
\(x=L\) の点で　\(φ(L)=0\)

$$\varphi (x)=\Big(\frac{2}{L}\Big)^{\frac{1}{2}}\sin\Big(\frac{n\pi}{L}x\Big)$$

$$P_r=|\varphi (x)|^2=\Big(\frac{2}{L}\Big)\sin^2\Big(\frac{n\pi}{L}x\Big)$$

$$E_n=\frac{\pi^2\hslash^2}{2mL^2}\cdotp n^2$$

## 3次元の場合

$$\varphi (x,y,z)=\Big(\frac{2}{L}\Big)^\frac{3}{2}\cdotp\sin \Big(\frac{n_x\pi}{L}x\Big)\cdotp\sin \Big(\frac{n_y\pi}{L}y\Big)\cdotp\sin \Big(\frac{n_z\pi}{L}z\Big)$$

$$E_{n_x,n_y,n_z}=\frac{\hslash ^2}{2m}\Big(\frac{\pi}{L}\Big)^2(n_x^2+n_y^2+n_z^2)$$

最大のエネルギー値 E を**フェルミエネルギー**という。