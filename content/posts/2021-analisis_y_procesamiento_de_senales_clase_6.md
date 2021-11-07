+++
title = "Análisis y procesamiento de señales - Clase 6"
date = 2021-10-28T00:00:00-03:00
tags = ["Análisis y procesamiento de señales", "Academic"]
draft = false
+++

## Operador de corrimiento {#operador-de-corrimiento}

Se representa como \\(\lambda^{-1}\\), lo que hace es representar cuanto se ha corrido una señal a la izquierda.

Ejemplo:

\\[a\_{p}y[n-p]+\cdots+a\_{1}y[n-1]+a\_{0}y[n]=0\\]

Al aplicar el operador queda de la siguiente manera

\\[a\_{p}\lambda^{-p}y[n]+\cdots+a\_{1}\lambda^{-1}y[n]+a\_{0}y[v]=0\\]

Ahora factorizamos el \\(y[n]\\)

\\[[a\_{p}\lambda^{-p}+\cdots+a\_{1}\lambda^{-1}+a\_{0}]y[n]=0\\]

De la ecuación anterior se obtienen "p" soluciones \\(\lambda\_1, \lambda\_2, \cdots, \lambda\_p\\)  que corresponden a los valores propios de la ecuación en diferencia. Dependiendo de los valores propios que obtengamos tendremos dos casos.


### Todos los valores propios distintos {#todos-los-valores-propios-distintos}

-   \\(\lambda\_1 \neq \lambda\_2, \cdots, \lambda\_{p-1} \neq \lambda\_{p}\\) la solución corresponde a:

    \\[y\_n[n]=\sum\_{l=1}^{p}C\_l \lambda\_l^n\\]


### Todos o algunos valores propios son iguales {#todos-o-algunos-valores-propios-son-iguales}

-   \\(\lambda\_1 = \lambda\_2 = \cdots = \lambda\_k \neq \lambda\_p\\) la solución corresponde a:

    \\[y\_n[n]= \sum\_{l=k+1}^{p}C\_l\lambda\_l^n+\sum\_{l=1}^kC\_ln^{(l-1)}\lambda^n\\]


## Ejemplo {#ejemplo}

Tenemos la siguiente señal

\\[y[n-3]-y[n-2]-y[n-1]+y[n]=0\\]

Aplicamos el operador de corrimiento \\(\lambda^-1\\)

\\[[\lambda^{-3}-\lambda^{-2}-\lambda^{-1}+1]y[n]=0\\]

Ahora resolvemos la siguiente ecuación

\\[\lambda^{-3}-\lambda^{-2}-\lambda^{-1}+1 =0\\]

Ecuación que tiene las siguientes soluciones

\\[\lambda\_1=-1, \quad \lambda\_2=1, \quad \lambda\_3=1\\]

De lo que podemos obtener que le grado del polinomio es 3, osea que \\(m\\) es igual a 3.

Por lo tanto, la `solución homogénea` del polinomio queda de la siguiente manera

\\[y\_n[n]= C\_1(1)^n+C\_2n(1)^n+C\_3(-1)^n\\]

Como podemos observar \\(C\_1\\) y \\(C\_2\\) corresponden a los terminos que se repiten, mientras que \\(C\_3\\) corresponde al termino que no.


## Solución particular {#solución-particular}

Se puede obtener de la siguiente maneara

\\[\sum\_{l=0}^{p}a\_{l} y[n-l]=x[n]\\]

Podemos definir \\(x[n]\\) (entrada) como un polinomio en n:

\\[x[n]=P(n)A^n\\]

\\(A\\) constante, \\(P(n)\\) polinomio

Para las ecuaciones en diferencia qudería expresado de la siguiente manera

\\[y\_p[n]=Q[n]A^nn^m\\]

Con \\(Q[n]\\) como un polinomio del mismo grado que \\(P[n]\\)


### Ejemplo {#ejemplo}

Tenemos la siguiente señal

\\[2y[n+2]+3y[n+1]-5y[n]=7n\\]

Podemos observar que \\(7n\\) corresponde a la entrada de la señal.

Aplicamos el operador de corrimiento \\(\lambda^-1\\)

\\[2\lambda^2+3\lambda-5=0\\]

Obetiendo como soluciones \\(\lambda\_1=\frac{5}{2}, \quad \lambda\_2=1\\)

\\[y\_n[n]=C\_1\left(\frac{5}{2}\right)^n+C\_2(1)^n\\]

Ahora expresamos la entrada como un polinomio

\\[P(n) = 7n, \quad A^n = 1\\]

Reemplazando \\(y\_p[n]\\) en la ED.

\\[y\_p[n]= \frac{-11}{4}n+\frac{1}{2}n^2\\]

`Solución`

\\[y[n]=C\_1\left(\frac{5}{2}\right)^n+C\_2(1)^n-\frac{11}{4}n+\frac{1}{2}n^2\\]


## Resolución por recursividad {#resolución-por-recursividad}

En este caso la \\(y[n]\\) se puede obtener muestra a muestra

\\[\sum\_{l=0}^{p}a\_ly[n-l]=\sum\_{l=0}^{m}b\_lx[n-l]\\]

Se expande como

\\[y[n]=\frac{b\_0}{a\_0}x[n]+\frac{b\_1}{a\_0}x[n-1]+\cdots+\frac{b\_m}{a\_0}x[n-m]-\left(\frac{a\_1}{a\_0}y[n-1]+\cdots+\frac{a\_p}{a\_0}y[n-p]\right)\\]

Entonces ahora solo falta iterar para "\\(n\\)" y "\\(p\\)"

```octave
% y[n] = y[n-1] + y[n-2] + x[n]
% y[n] = 0 para n<0
% x[n] = impulso(n)


n = 20;
y = zeros(1,n); % Desde 0

y(1) = 1; % Condición inicial y[0]
y(2) = 1; % Condición inicial y[1]

for p=3:1:n
  if p > 1
    x(p)=0;
  else
    x(p)=1;
  end
  y(p) = y(p-1) + y(p-2) + x(p);
end

stem(y)
```