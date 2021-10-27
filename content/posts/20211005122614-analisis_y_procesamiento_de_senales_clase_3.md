+++
title = "Análisis y procesamiento de señales - Clase 3"
date = 2021-10-26T00:00:00-03:00
draft = false
+++

## Secuencias fundamentales {#secuencias-fundamentales}

A continuación se muestra como representar el escalón e impulso unitario en Matlab.


### Impulso unitario {#impulso-unitario}

```octave
function[x, n] = impulso(n0, n1, n2)
% Genera x(n) = impulso(n - n0) para n1 <= n <= n2
n = [n1 : n2]; % genera vector n desde n1 a n2
x = [(n - n0) == 0]; % si la resta es = 0, genera un 1
x = single(x); % convierte valor lógico a numérico
```


### Escalón unitario {#escalón-unitario}

```octave
function[x, n] = escalon(n0, n1, n2,A)
% Genera x(n) = escalon(n - n0) para n1 <= n <= n2
n = [n1 : n2]; % genera vector n desde n1 a n2
x = [(n - n0) >= 0]; % si la resta es >= 0, genera un 1
x = A*single(x); % convierte valor lógico a numérico
```


### Secuencias aleatorias {#secuencias-aleatorias}

Estas secuencias se utlizan para representar ruido, y se modelan mediante variables aleatorias de "teoría de probabilidad". Para este tipo de secuencias, el valor RMS es más representativo que la amplitud. El valor RMS se puede calcular a partir de la distribución de probabilidad de la variable aleatoria que da origen a la secuencia.

El valor RMS de una secuenencia \\(r[n]\\) de \\(N\\) muestras es: \\(r\_{RMS}=\sqrt{\frac{1}{N}\sum\_{i=1}^{N}r^2(i)}\\)

La desviación estándar experimental de una variable aleatoria X es:

\\[\sigma\_{x}=\sqrt{\frac{1}{N-1} \sum\_{i=1}^{N}\left(x\_{i}-\overline{\bar{x}}\right)^{2}}\\]

Por otro lado, la desviación estándar teórica de una variable aleatoria continua en la amplitud está dada por:

\\[\sigma\_{r}=\sqrt{\int\_{-\infty}^{\infty} D( r)[r-E( r)]^{2} d r}, \quad E( r)=\int\_{-\infty}^{\infty} D( r) r d r\\]

Siendo \\(D( r)\\) la distribución de probabilidad de la variable, y \\(E( r)\\) su valor esperado, una predicción del promedio experimental.

Por lo tanto, se puede predecir el valor RMS de una secuencia de ruido si se conoce la distribución de probabilidad que da origen a la secuencia.

`Distribución plana`: La variable aleatoria "r" puede tomar cualquier valor comprendido entre -A y A con igual probabilidad.

{{< figure src="/ox-hugo/2021-10-05_13-21-26_screenshot.png" >}}

El valor RMS de una secuencia aleatoria con una distribución plana y amplitud A está dado por:

\\[r\_{R M S}=\frac{A}{\sqrt{3}} \approx 0.577 \mathrm{~A}\\]

La función `rand` en Matlab genera una secuencia aleatoria de `n` valores en un vector de fila, con distribución plana entrte 0 y 1. El "1" en la función `rand` especifíca el número de filas, no el límite de la distribución.


### Ejemplo: {#ejemplo}

```octave
clc
x=2*rand(1,100)-1;

fprintf('Mínimo=\t %1.5f\n', min(x))
fprintf('Máximo=\t %1.5f\n', max(x))
fprintf('RMS=\t %1.5f\n', std(x))
fprintf('Media=\t %1.5f\n', mean(x))

n=1:100;
subplot 211;
plot(n,x);
subplot 212;
hist(x,100);
```