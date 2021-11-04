+++
title = "Análisis y procesamiento de señales - Clase 7"
date = 2021-11-04T00:00:00-03:00
draft = false
+++

## Convolución discreta {#convolución-discreta}

Operación matemática entre \\(x[n]\\) (entrada) y su repuestal impulso, resultando en \\(y[n]\\).

Sabemos que toda señal discreta se puede representar como un tren de impulsos desplazados.

\\[x[n] = \sum\_{k=-\infty}^{\infty} x[k]\delta[n-k]\\]

También sabemos que la respuesta de un sistema a un impulso unitario es:

\\[x[n]=\delta[n]\\]

\\[h[n]=T<\delta[n]>\\]

Si el operador `T` es LTI

\\[h[n-k]=T<\delta[n-k]>\\]

La respuesta del sistema \\(y[n]\\) a una entrada \\(x[n]\\)

\\[y[n]= T<x[n]>\\]
\\[y[n]=T \left\langle \sum\_{k=-\infty}^{\infty}x[k]\delta[n-k] \right\rangle\\]

Como el operador `T` sólo opera en `n`, podemos sacar la sumatoria de \\(n[k]\\).

\\[y[n]= \sum\_{k=-\infty}^{\infty} x[k] T \left\langle \delta[n-k] \right\rangle\\]

\\[y[n] = \sum\_{k=-\infty}^{\infty} x[k] h[n-k]\\]

La expresión anterior se conoce como `producto de convolución` entre una entrada \\(x[n]\\) y una respuesta impulsa \\(h[n]\\)


## Propiedades de la convolución {#propiedades-de-la-convolución}

-   Linealidad
-   Conmutatividad
-   Corrimiento
-   Distribuitiva
-   Asociativa
-   Convolución con un impulso:
    Si se realiza la convolución con un impulso voy a obtener replicas escaladas y/o desplazadas.