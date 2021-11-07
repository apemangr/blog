+++
title = "Análisis y procesamiento de señales - Clase 5"
date = 2021-10-26T00:00:00-03:00
tags = ["Análisis y procesamiento de señales", "Academic"]
draft = false
+++

## Respuesta impulso {#respuesta-impulso}

Es la respuesta estado cero del sistema a un impulso en tiempo discreto de amplitud 1 aplicado en \\(n=0\\).

La respuesta impulso tiene gran importancia, ya que puede ser utilizada para predecir la respuesta estado cero del sistema a cualquier entrada mediante la operación de `convolución`, si conocer la transformación \\(T\\) que realiza el sistema.


## Estabilidad {#estabilidad}

Un sistema es estable si cualquier entrada acotada produce una salida acotada.

Una secuencia es acotada si cumple con la condición \\(|x(n)| \leq M \quad \forall n\\)
Donde M es una constante positiva finita.

Para mas información ver [este video.](https://www.youtube.com/watch?v=ngJ2QWvMPbI)

La estabilidad no depende de la entrada aplicada. Es suficiente que una entrada acotada produzca una salida no acotada para que el sistema sea `inestable`. En un SLI se puede especificar la condición de estabilidad a partir de su `respuesta impulso` de la siguiente forma \\(h(n)=a^n u(n)\\).

{{< figure src="/ox-hugo/2021-10-26_16-36-07_screenshot.png" >}}

La suma de las magnitudes de los coeficientes de la respuesta impulso es una serie geométrica que converge \\(|a| < 1\\). En tal caso el sistema es estable.

Por ejemplo si a tiene un valor de 0.5 la sumatoria quedaría de la siguiente manera.

\\[
\sum\_{k=0}^{\infty}\left|0.5^{k}\right|=1+\frac{1}{2}+\frac{1}{4}+\frac{1}{8}+\ldots=2
\\]

{{< figure src="/ox-hugo/2021-10-26_16-47-30_screenshot.png" >}}


## Causalidad {#causalidad}

Un sistema es cuasal si su salida solo depende del valor actual o de valores pasados, nunca de valores futuros.

Para mas información ver [este video.](https://www.youtube.com/watch?v=mqwUtn5cip8&t=394s)


## Ecuaciones de diferencia {#ecuaciones-de-diferencia}

Describen la relación entrada - salida de un SLI en tiempo discreto, asi como las ecuaciones diferenciales describen la misma relación en sistemas en tiempo continuo. Por ejemplo:

\\[
Vo(n)=0.1 \cdot V\_{l}(n)+0.9 \cdot \operatorname{Vo}(n-1)
\\]

La forma general de una ED es \\(\sum\_{k=0}^{N} a\_{k} y(n-k)=\sum\_{m=0}^{M} b\_{m} x(n-m)\\)

Ejemplo: Le ED de un SLI es: \\(y(n)=4 x(n)+3 x(n-1)+2 x(n-2)-0.5 y(n-1)\\)
Calcular la salida para \\(0 \leq n \leq 6\\) con \\(y(-1)=0\\) si \\(x(n)=\delta(n)+\delta(n-1)+\delta(n-2)\\)

MATLAB incluye la función `filter` para resolver las ED. Las instrucciones para el ejercicio anterior serian:

```octave

x = [1 1 1 0 0 0 0]; % Entrada
a = [1 0.5];         % Coeficientes de y(n)
b = [4 3 2];         % Coeficientes de x(n)
y = filter(b, a, x)  % Salida
```

Se puede agregar una condición inicial. Por ejemplo, si \\(y(-1)=2\\), el código sería:

```octave

x = [1 1 1 0 0 0 0];   % Entrada
a = [1 0.5];           % Coeficientes de y(n)
b = [4 3 2];           % Coeficientes de x(n)
y = [2];               % Condición inicial y(-1)
z = filtic(b, a, y);   % Calcula las condiciones iniciales para "filter"
y = filter(b, a, x, z) % Salida
```