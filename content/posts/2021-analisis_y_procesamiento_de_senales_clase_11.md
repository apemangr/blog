+++
title = "Análisis y procesamiento de señales - Clase 11"
date = 2021-11-10T00:00:00-03:00
tags = ["Análisis y procesamiento de señales", "Academic"]
draft = false
+++

## Respuesta en frecuencia de filtros digitales {#respuesta-en-frecuencia-de-filtros-digitales}

Los sistemas digitales invariantes (SLI) en tiempo discreto actúan como `filtros digitales`.

Los filtros `FIR` (Finite Impulse Response) no tienen realimentación. Para el `diseño` de estos filtros lo que se hace es: Encontrar los coeficientes de su respuesta impulso \\(h(n)\\) a partir de la respuesta de frecuencia deseada.

Los filtros `IIR` (Infinite Impulse Response) tienen realimentación. Para el `diseño` lo que se hace es: Encontrar los coeficientes de su ecuación en diferencia a partir de la respuesta de frecuencia deseada.

`Tip de diseño`: Verificar la respuesta de frecuencia obtenida para determinar el cumplimiento de las especificaciones originales.


## Respuesta de frecuencia en función de h[n] {#respuesta-de-frecuencia-en-función-de-h-n}

Si ingresamos una sinusoide en un SLI, su salida en estado estacionario también es una sinusoide de igual frecuencia.

\\[\textrm{Sinusoide} \longrightarrow SLI \longrightarrow \textrm{Estado estacionario}\\]

Por ejemplo si tenemos la siguiente señal

\\[y[n] = \sum\_{k=-\infty}^{\infty} h[k] x[n-k]\\]

En donde, su entrada \\(x[n]\\) es

\\[x[n]=e^{j\omega n}\\]

Entonces nuestra señal queda como

\\[y[n] = \sum\_{k=-\infty}^{\infty} h[k] e^{j\omega (n-k)}\\]
\\[y[n]= \sum\_{k=-\infty}^{\infty} h[k] e^{j\omega n} e^{-j\omega k}\\]
\\[y[n]= e^{j\omega n} \sum\_{k=-\infty}^{\infty} h[k]e^{j \omega k}\\]

Quedando la entrada afuera de la sumatoria, y siendo la sumatoria la `"Respuesta de frecuencia del sistema con respuesta impulso"` que también se puede denotar como \\(H(\omega)\\).

Por la tanto \\(H(\omega)\\) se puede expresar como

\\[H(\omega)= \sum\_{k=-\infty}^{\infty} h[k]e^{-j \omega k}\\]

`Ejemplo`

Si se quiere determinar la magnitud y el ángulo para de \\(H(\omega)\\) para \\(h[n] = 0.9^{n} u[n]\\)

\\[H(\omega) = \textrm{DTFT}\left\\{ h[n] \right\\} = \sum\_{n=-\infty}^{\infty}h[n]e^{-j \omega n}\\]
\\[H(\omega)= \sum\_{n=0}^{\infty} 0.9^n e^{-j\omega n} = \sum\_{n=0}^{\infty} \left( 0.9e^{-j\omega} \right)^{n}\\]
\\[H(\omega) = \frac{1}{1-0.9e^{-j\omega}}\\]

Lo pasamos a coordenas trigonométricas

\\[H(\omega) = \frac{1}{(1-0.9\cos(\omega))+j(0.9\sin(\omega))}\\]

Ahora para calcular su magnitud

\\[|H(\omega)| = \sqrt{\frac{1}{(1-0.9\cos(\omega))^{2}+(0.9\sin(\omega))^{2}}\\]
\\[|H(\omega)|=\frac{1}{1.81-1.8 \cos(\omega)}\\]

Ahora para el ángulo procedemos de la siguiente manera

\\[\angle H(\omega)= -\tan^{-1}\left[ \frac{0.9\sin(\omega)}{1-0.9\cos(\omega)} \right]\\]

Podemos representar esta señal de la siguiente forma en MATLAB

```octave
n = 0:40;
h = 0.9.^n;

stem(n,h)
title("h[n]")
```

{{< figure src="/ox-hugo/2021-11-10_23-08-32_screenshot.png" >}}

Y para obtener su ángulo y magnitud

```octave
w = [0 : 0.001 : 1] * pi;

% Mag y Ang Teóricos
MT = 1 ./ sqrt(1.81 - 1.8*cos(w));
AT = - (180/pi) * atan((0.9 * sin(w)) ./ (1 - (0.9 * cos(w))));

% Mag y Ang Numéricos
n = 0 : 20;
h = 0.9 .^ n;
H = dtft(h, n, w);
MN = abs(H);
AN = (180/pi) * angle(H);

subplot 121;
plot(w/pi, MT, 'b', w/pi, MN, 'r');
title('Mag Azul: teórica Rojo: numérica')
xlabel('w / Pi [rad/m]');
grid;

subplot 122;
plot(w/pi, AT, 'b', w/pi, AN, 'r');
title('Ang[°] Azul: teórico Rojo: numérico')
xlabel('w / Pi [rad/m]');
```

{{< figure src="/ox-hugo/2021-11-10_23-09-20_screenshot.png" >}}

`Ejemplo`

Calcular la respuesta impulso de un filtro digital pasabajos ideal con \\(\omega\_{c}\\)

\\[H(\omega)= \left\\{ 1 \quad |\omega| \le \omega\_{c}, \quad 0 \quad \omega\_{c} \lt |\omega| < \pi \right\\}\\]

\\[h[n] = \textrm{IDTFT}[H(\omega)] = \frac{1}{2\pi} = \frac{1}{2\pi}\int\limits\_{-\pi}^{\pi}H(\omega)e^{-j\omega n} d\omega\\]
\\[h[n]=\frac{1}{2\pi}\int\limits\_{-\omega\_{c}}^{\omega^{c}}e^{-j \omega n} d\omega\\]
\\[h[n] = \frac{e^{j\omega\_{c}n} - e^{-j\omega\_{c}n}}{j2\pi n}\\]
\\[h[n]= \frac{\sin(\omega\_{c}n)}{\pi n}\\]