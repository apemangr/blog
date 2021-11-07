+++
title = "Análisis y procesamiento de señales - Clase 4"
date = 2021-10-25T00:00:00-03:00
tags = ["Análisis y procesamiento de señales", "Academic"]
draft = false
+++

## Sistemas discretos {#sistemas-discretos}

Es un dispositivo o algoritmo que opera sobre una señal discreta, que es la "entrada o excitación", de acuerdo a una regla bien definida, para producir una señal discreta en el tiempo, que es la "salida" o respuesta del sistema.

{{< figure src="/ox-hugo/2021-10-26_13-50-46_screenshot.png" >}}

Siempre debe existir una relación única entre la secuencia de entrada y salida la que se pruede representar como \\(y(n)=T[x(n)]\\), donde \\(T\\) es la transformación que realiza el sistema.

Los sistemas se pueden clasificar en base a las restricciones que afectan a la transformación \\(T\\). Esa clasificación es importante ya que determina las limitaciones de un sistema como las operaciones matemáticas que pueden ser usadas.


## Linealidad {#linealidad}

Para que un sistema sea lineal debe cumplir con las propiedades de `aditividad` y `homogeneidad`.

\\[
T\left[a \cdot x\_{1}(n)+b \cdot x\_{2}(n)\right]=a \cdot T\left[x\_{1}(n)\right]+b \cdot T\left[x\_{2}(n)\right] \quad a, b: \text { constantes }
\\]

Para más información ver [este video.](https://www.youtube.com/watch?v=wOQDGvCLOs8&t=208s)


## Invariancia {#invariancia}

Un sistema es `invariante` si la transformación que se le aplica no varía con el tiempo. Es decir que si la entrada se desplaza en el tiempo la salida lo hace en el mismo intervalo, sin alterar su forma matemática.

\\[
y\left(n-n\_{0}\right)=T\left[x\left(n-n\_{0}\right)\right] \quad n\_{0}: \text { constante entera }
\\]