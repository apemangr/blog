+++
title = "Análisis y procesamiento de señales - Clase 9"
date = 2021-11-06T00:00:00-03:00
tags = ["Análisis y procesamiento de señales", "Academic"]
draft = false
+++

## Transformada discreta en el tiempo de Fourier (DTFT) {#transformada-discreta-en-el-tiempo-de-fourier--dtft}

Esta transformada nos genera apartir de una secuencia \\(x[n]\\) genera una representación en el dominio de la frecuencia.

\\[x[n] \longrightarrow X[\omega]\\]

\\[X(\omega) = \sum\_{n=-\infty}^{\infty}x[n]e^{-j \omega n}\\]

Recordando la identidad de Euler

\\[e^{-j \omega} = \cos(\omega) +j \sin(\omega)\\]

Ahora si utilizamos la identidad de Euler en la DTFT queda como

\\[X(\omega) = \sum\_{n= -\infty}^{\infty} x[n] \cos(\omega n) - j \sum\_{n= -\infty}^{\infty} x[n]\sin(\omega n)\\]

Como podemos observar la DTFT se divide en una parte `real`

\\[\mathbb{R}[X(\omega)] = \sum\_{n=-\infty}^{\infty}x[n] \cos(\omega n)\\]

y de una parte `imaginaria`

\\[\mathbb{I}[X(\omega)] = \sum\_{n=-\infty}^{\infty} x[n] \sin(\omega n)\\]

Podemos observar que

\\[\omega n \longrightarrow[rad] \quad \textrm{Ángulo}\\]

\\[n \longrightarrow \textrm{Índice de muestras}\\]

\\[\omega \longrightarrow \left[ \frac{rad}{m} \right] \quad \textrm{Radianes por muestra}\\]

`Ejemplo`

Tenemos la señal \\(x[n]=\cos[2 \pi fn]\\) con \\(f=0.1[c/m]\\), donde \\(x[n]\\) contiene \\(10[m/c]\\).

Supongamos que se desea calcular la parte real de la DTFT en la frecuencia \\(\omega=0.1 \pi [rad/m]\\).

Como \\(\omega=2 \pi f\\), la frecuencia de la onda con seno generada por la DTFT es igual a \\(0.05 [c/m]\\). En otras palabras, la secuencia contiene \\(20[m/c]\\)

```octave
n = 1:20;
f = 0.1;
x = cos(2*pi*f*n);
w = 0.1*pi;

realP = cos(w*n);
prod = x.*realP;

figure()
subplot 311
stem(n,x)
grid on
title('x[n] 0.1[c/m]')
subplot 312
stem(n,realP)
title('cos[wn] 0.05[c/m]')
grid on
subplot 313
stem(n,prod)
title('Producto')
grid on
```

Donde se obtiene como resultado

{{< figure src="/ox-hugo/2021-11-07_00-18-44_screenshot.png" >}}

Basicamente lo que hace la función es obtener la señal y multiplicarla por su parte real punto por punto

`Resumiendo`, las partes real e imaginaria de \\(X(\omega)\\) son dos números que indican la similitud de la secuencia \\(x[n]\\) con secuencias coseno y seno de frencuencia \\(\omega\\) generadas por la DTFT.


## Transformada discreta inversa en el tiempo de Fourier (IDTFT) {#transformada-discreta-inversa-en-el-tiempo-de-fourier--idtft}

Se puede representar como

\\[x[n] = \frac{1}{2 \pi} \int\limits\_{-\pi}^{\pi}X(\omega)e^{j\omega n} d\omega\\]

Lo que se busca con esta transformada es poder reconstruir la secuencia orginial a partir de la secuencia en el dominio de la frecuencia.


## Propiedadse de la DTFT {#propiedadse-de-la-dtft}

-   Linealidad
-   Desplazamiento en frencuencia
-   Desplazamiento en el tiempo
-   Simetría
-   Convolución
    \\[y[n] = x[n]\*h[n] \longrightarrow Y(\omega)=X(\omega)\cdot H(\omega)\\]
    \\[z[n ] = x[n]\cdot y[n] \longrightarrow Z(\omega) = \frac{1}{2 \pi} X(\omega)\*Y(\omega)\\]

    Osea, que la convolución en un dominio es la multiplicación en el otro.