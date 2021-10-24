+++
title = "Teoría de circuitos 1 - Ayudantía 5"
draft = false
+++

## Capacitores {#capacitores}

Los capacitores cuando el circuito se está cargando actúan como "circuito abierto", y una vez que se retira la fuente de voltage este toman su lugar y comienzan a descargarse. La ecuación diferencial que describe la variación de corriente es la siguiente:

\\[i(t)=\frac{dq(t)}{dt}=C\frac{dv(t)}{dt}\\]

La `capacitancia` es la unidad de medida de los capacitores, y esta descrita por la siguiente fórmula:

\\[C=\frac{q}{v}[F]\\]


## Inductores {#inductores}

Al igual que los capacitores el comportamiento de estos elementos varían dependiendo del momento de tiempo en el que los analicemos, mientras se estan cargando actúan como "circuito cerrado", y cuando ya estan cargandos y se descargan tienen un comportamiento similar al de una fuente de corriente.

La `inductancia` es la unidad de medida, y tiene la siguiente fórmula:

\\[L=\frac{N^2 \mu A }{l}[H]\\]

Mediante la ley de Faraday podemos asumir que la variación del flujo magnético puede inducir un voltage, en el caso del inductor su fórmula es:

\\[v(t)=\frac{d\Phi(t)}{dt}=L\frac{di(t)}{dt}\\]


## Como sumar componentes {#como-sumar-componentes}


### Capacitores {#capacitores}


#### Serie {#serie}

Se suman como si fuesen resistencias en paralelo.


#### Paralelo {#paralelo}

Se suman como si fuesen resistencias en serie.


### Inductores {#inductores}


#### Serie {#serie}

Se suman igual que las resistencias.


#### Paralelo {#paralelo}

Se suman igual que las resistencias.


## Energía almacenada {#energía-almacenada}


### Capacitor {#capacitor}

\\[E\_{C}=\frac{1}{2}C(V\_{final}^2-V\_{inicial}^2)\\]


### Inductor {#inductor}

\\[E\_{L}=\frac{1}{2}L(I\_{final}^2-I\_{inicial}^2)\\]