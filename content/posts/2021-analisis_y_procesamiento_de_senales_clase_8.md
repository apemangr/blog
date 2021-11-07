+++
title = "Análisis y procesamiento de señales - Clase 8"
date = 2021-11-05T00:00:00-03:00
tags = ["Análisis y procesamiento de señales", "Academic"]
draft = false
+++

## Convolución mediante el método "Slidding strip" {#convolución-mediante-el-método-slidding-strip}

Este método analítico básicamente consiste en:

-   1. Voltear la señal más pequeña
-   2. Desplazarla en todo el intervalo de la muestra
-   3. Multiplicar las señales en sus puntos de intersección


## Convolución mediante el método "Suma por columnas" {#convolución-mediante-el-método-suma-por-columnas}

Si tenemos las señales \\(x[n]\\) y \\(h[n]\\) con un soporte compacto y de largo \\(L\_h=M\\), \\(L\_x=N\\) se tiene que

\\[y[n]=\sum\_{l=0}^L h[l] x[n-l] = h[0] x[-l]+ \ldots + h[L] x[n-L]\\]

\\[x[n]=0, \quad \forall n < 0\\]
\\[y[0]=h[0]x[0]\\]
\\[y[1]=h[0]x[1]+h[1]x[0]\\]
\\[y[2]=h[0]x[2]+h[1]x[1]+h[2]x[0]\\]
\\[y[k]=h[0]x[N-1]+h[1]h[N-2]+\ldots+h[M-1]x[0]\\]
\\[y[k+1] = 0  + h[1]x[N-1]+ \ldots + h[M-1]x[1]\\]
\\[y[P]= h[M-1]x[N-1]\\]

`Ejemplo`

Se tienen dos señales \\(h[n]=[1,1,1,1]\\) y \\(x[n]=[2,3,5]\\), donde cabe destacar que los indices de cada señal comienzan en 0.

\\[y[0]=h[0]x[0]=2\\]
\\[y[1]=h[0]x[1]+h[1]x[0]=5\\]
\\[y[2]=h[0]x[2]+h[1]x[1]+h[2]x[0]=10\\]
\\[y[3]=0 +h[1]x[2]+h[2]x[1]+h[3]x[0]=10\\]
\\[y[4]=0+0+h[2]x[2]+h[3]x[1]=8\\]
\\[y[5]=0+0+0+h[3]x[2]=5\\]

No sirve seguir tomando valores puesto que ya no se estaría cumpliendo con la causalidad.