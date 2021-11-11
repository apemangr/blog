+++
title = "Propagación de ondas electromagnéticas - Clase 4"
date = 2021-11-08T00:00:00-03:00
tags = ["Propagación de ondas electromagnéticas", "Academic"]
draft = false
+++

## Materiales dieléctricos {#materiales-dieléctricos}

Cargas positivas y negativas se desplazan cuando se aplica un campo eléctrico.

{{< figure src="/ox-hugo/2021-11-08_17-24-53_screenshot.png" >}}

-   Para un dieléctrico con N molécluas por unidad de volumen:

    \\[\vec{P}= N\vec{p}, \quad \textrm{Polarización eléctrica}\\]

-   Si la polarización es uniforme, las `cargas ligadas` aparecen sólo en la superficie del material

-   Si la polarización varía en el dieléctrico: acumulación de cargas en el material

-   Densidad de carga volumétrica \\(\rho\_b= -\vec{\nabla} \cdot \vec{P} \quad , \quad \textrm{Densidad de cargas ligadas}\\)


## ¿Qué relación tiene esto con las ecuaciones de Maxwell? {#qué-relación-tiene-esto-con-las-ecuaciones-de-maxwell}

Como podemos recordar Maxwell-Gauss es

\\[\vec{\nabla} \cdot \vec{E} = \frac{\rho}{\epsilon\_{o}}\\]

En donde "\\(\rho\\)" representa la `densidad de carga total`, ahora vemos que esta densidad esta compuesta de "cargas libres" y "cargas ligadas"

\\[\rho=\rho\_f + \rho\_{b}\\]

\\[\rho\_{f}= \textrm{Cargas libres}\\]
\\[\rho\_{b} = \textrm{Cargas ligadas}\\]

Ahora si reemplazamos en la ecuación de Maxwell-Gauss

\\[\vec{\nabla} \cdot \vec{E} = \frac{\rho\_f+\rho\_b}{\epsilon\_0}\\]

Ahora si reemplazamos la polarización de las cargas ligadas que vimos anteriormente

\\[\vec{\nabla} \cdot \epsilon\_0 \vec{E} = \rho\_f - \vec{\nabla}\cdot \vec{P}\\]
\\[\vec{\nabla} \cdot \epsilon\_0 \vec{E} + \vec{\nabla} \cdot \vec{P} = \rho\_{f}\\]
\\[\vec{\nabla} \cdot {(\epsilon\_{0} \vec{E}+\vec{P})} = \rho\_{f}\\]
\\[\vec{\nabla} \cdot \vec{D}  = \rho\_{f}\\]


## ¿Qué significa el vector D? {#qué-significa-el-vector-d}

-   Espacio libre: Proporcional al campo eléctrico, con la mismo dirección \\(\vec{D} = \epsilon\_{0}\vec{E}\\)
-   Materiales polarizables: El campo de desplazamiento puede variar. Puede tener rotacional si la polarización tiene.

-   No se trata de una magnitud medible directamente: Es un campo auxiliar que facilita la formulación del problema eléctrico en presencia de medios polarizables.


## Para campos eléctricos tenemos la polarización {#para-campos-eléctricos-tenemos-la-polarización}

-   Momento dipolo magnético por unidad de volumen en materiales magnéticos

-   `Corriente ligadas` actúan como fuente adicional de campos magnéticos

    \\[\vec{J}\_b= \vec{\nabla} \times \vec{P}\_{m}\\]

    \\[\vec{J} \quad \textrm{Corrientes ligadas}\\]
    \\[\vec{P}\_{m} \quad \textrm{Magnetización del material}\\]

-   Otra contribución a la densidad de corriente: razón de cambio de la polarización
    -   Movimiento de cargas implica corriente

        \\[\vec{J}\_{p} = \frac{\partial \vec{P}}{\partial t}\\]

        \\[\vec{J} = \vec{J}\_{f} + \vec{J}\_b+ \vec{J}\_{p}\\]

        \\[\vec{J}\_{f} \quad
            \textrm{Corrientes libres}\\]
        \\[\vec{J}\_{b} \quad \textrm{Corrientes ligadas}\\]
        \\[\vec{J}\_{p} \quad \textrm{Corrientes de polarización}\\]

Por ende, ahora definimos la ecuación de Maxwell-Ampere con estas tres corrientes

\\[\vec{\nabla} \times \vec{B}=\mu\_{0}\left(\vec{J}+\epsilon\_{0} \frac{\partial \vec{E}}{\partial t}\right)\\]
\\[\vec{\nabla} \times \vec{B}=\mu\_{0}\left(\vec{J}\_{f}+\vec{J}\_{b}+\vec{J}\_{p}+\epsilon\_{0} \frac{\partial \vec{E}}{\partial t}\right)\\]
\\[\vec{\nabla} \times \vec{B}=\mu\_{0}\left(\vec{J}\_{f}+\vec{\nabla} \times \overrightarrow{P\_{m}}+\frac{\partial \vec{P}}{\partial t}+\epsilon\_{0} \frac{\partial \vec{E}}{\partial t}\right)\\]
\\[\vec{\nabla} \times\left(\frac{\vec{B}}{\mu\_{0}}-\overrightarrow{P\_{m}}\right)=\vec{J}\_{f}+\frac{\partial\left(\vec{P}+\epsilon\_{0} \vec{E}\right)}{\partial t}\\]
\\[\vec{\nabla} \times \vec{H}=\vec{J}\_{f}+\frac{\partial\left(\vec{P}+\epsilon\_{0} \vec{E}\right)}{\partial t}\\]

-   Intensidad de campo magnético \\(\vec{H}\\): En espacio libre es proporcional al vector de inducción magnética
    -   En cuerpos magnetizados cambia


## Medio conductor {#medio-conductor}

-   Material caracterizado por presencia de cargas libresb

-   La aplicación de un campo eléctrico estático pone en movimiento las cargas libres (de masa \\(m\\) y carga \\(q\\))

{{< figure src="/ox-hugo/2021-11-08_18-26-29_screenshot.png" >}}

Donde tenemos que

\\[\vec{v}=\frac{\tau q}{m} \vec{E}\\]
\\[\vec{J} = \rho \vec{v} = N q \vec{v}\\]
\\[\vec{J} = \sigma \vec{E}\\]
\\[\sigma = N \frac{\tau q^2}{m}, \quad \textrm{Conductividad del material}\\]

\\[N \quad \textrm{Número de partículas por unidad de volumen}\\]

-   La ley de Ohm microscópica: Más importante es la tensión aplicada, el campo en el conductor es más importante, y las cargas libres se desplazan rápidamente.
    -   La densidad de corriente aumenta con el campo eléctrico

\\[\vec{J} = \sigma \vec{E}\\]

-   Para un material conductor homogéneo, isótropo y no dispersivo

    \\[\vec{J}\_{c}(\vec{r},t)=\sigma \vec{E} (\vec{r}, t)\\]


## Ecuaciones de Maxwell en un conductor (régimen armónico) {#ecuaciones-de-maxwell-en-un-conductor--régimen-armónico}

\\[\vec{\nabla} \times \vec{E}(\vec{r})=-j \omega \mu\_{0} \vec{H}(\vec{r})\\]
\\[\vec{\nabla} \times \vec{H}(\vec{r})=j \omega \epsilon\_{0} \vec{E}(\vec{r})+\sigma \vec{E}+\vec{J}\_{\text {exci }}(\vec{r})\\]
\\[\vec{\nabla} \cdot \vec{E}(\vec{r})=\frac{\rho\_{\text {exci }}(\vec{r})}{\epsilon\_{0}}\\]
\\[\vec{\nabla} \cdot \vec{H}(\vec{r})=0\\]


## Régimen armónico: campos con dependencia sinusoidal {#régimen-armónico-campos-con-dependencia-sinusoidal}

\\[\vec{E}(\vec{r},t) = \Re \left[ \vec{E}(\vec{r})\cdot e^{j\omega t} \right]\\]


## Ecuaciones de Maxwell en régimen armónico {#ecuaciones-de-maxwell-en-régimen-armónico}

\\[\vec{\nabla} \times \vec{E}(\vec{r}) =-j \omega \vec{B}(\vec{r})\\]
\\[\vec{\nabla} \times \vec{H}(\vec{r}) = j \omega \vec{D}(\vec{r})+\vec{J}(\vec{r}) \\]
\\[\vec{\nabla} \cdot \vec{D}(\vec{r}) =\rho(\vec{r}) \\]
\\[\vec{\nabla} \cdot \vec{B}(\vec{r}) = 0 \\]


## Ecuación de Helmholtz o ecuación de onda {#ecuación-de-helmholtz-o-ecuación-de-onda}

Fuentes al infinito \\(\vec{J}(\vec{r}) = 0\\) y \\(\rho(\vec{r})=0\\) en un medio lineal, isótropo y homogéneo

\\[\nabla^{2} \vec{H}(\vec{r})+\omega^{2} \mu \varepsilon \vec{H}(\vec{r})=0\\]
\\[\nabla^{2} \vec{E}(\vec{r})+\omega^{2} \mu \varepsilon \vec{E}(\vec{r})=0\\]
\\[k = \omega \sqrt{\mu\epsilon}\\]


## Supongamos un medio sin pérdidas {#supongamos-un-medio-sin-pérdidas}

Con \\(\chi\\) y \\(\mu\\) reales

Solución de onda plana básica con campo eléctrico en una sola dirección (ninguna variación en ejes \\(Ox\\) y \\(Oy\\))

\\[\frac{\partial^{2} E\_{x}(z)}{\partial z^{2}}+k^{2} E\_{x}(z)=0\\]

-   Solución régimen armónico
    \\[E\_{x}(z)=E^{+} e^{-j k z}+E^{-} e^{+j k z}\\]

-   Solución temporal

\\[E\_{x}(z, t)=E^{+} \cos (\omega t-k z)+E^{-} \cos (\omega t+k z)\\]