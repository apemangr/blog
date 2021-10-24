+++
title = "Teoría de circuitos 1 - Ayudantía 6"
date = 2021-10-17T00:00:00-03:00
draft = false
+++

## Circuitos de primer orden {#circuitos-de-primer-orden}

Características principales:

-   Trabajan con ecuaciones diferenciales de primer order
-   Varían en el tiempo
-   Solo pueden ser de tipo R-C o R-L
-   Se tiende a buscar el valor del capacitor o inductor en el tiempo
-   Se pueden dividir en dos tipos de circuitos
    1.  Circuitos de carga (estado 0), que presenta respuesta homogénea y particular
    2.  Circuitos de descarga (entrada 0), que presentan sólo respuesta homogénea


## Pasos para resolver un circuito de primer orden {#pasos-para-resolver-un-circuito-de-primer-orden}

1.  Analizar el circuito con respecto a t<0 y calcular las condiciones iniciales
2.  Analizar el circuito con respecto a t>0 ya sea mediante LKV o LKC para de esta forma encontrar la ecuación diferencial
3.  Encontrar el valor de los exponentes que acompañan a la señal exponencial
4.  Encontrar la respuesta en el tiempo


## Circuitos de entrada 0 {#circuitos-de-entrada-0}

Son los circuitos que al ser analizados para instantes de tiempo mayores a 0 (t>0) nos queda como un resistor conectado a un inductor o capacitor.

El capacitor o inductor comienza a alimentar el circuito hasta que finalmente se vacía. Este tipo de circuito posee una condición inicial distinta de 0. Sin embargo su ecuación diferencial queda igualada a 0.


## Circuitos de estado 0 {#circuitos-de-estado-0}

Cuando hacemos un análisis en instantes de tiempo mayores a 0 (t>0) el circuito queda como un resistor conectado a un inductor o capacitor y a una fuente independiente de voltaje o corriente. En estos instantes el capacitor o inductor se encuentran cargandose.

Pueden tener una condición inical igual o distinta de 0. Su ecuación diferencial queda igualada a la fuente multiplicada o dividida por algún capacitor (dependiendo si la ecuación queda en base a tensión o corriente)