+++
title = "Análisis y procesamiento de señales - Clase 10"
date = 2021-11-07T00:00:00-03:00
tags = ["Análisis y procesamiento de señales", "Academic"]
draft = false
+++

Si calculamos la DTFT de \\(\delta[n]\\) obtenemos

\\[X(\omega) = \sum\_{n=-\infty}^{\infty} \delta[n]e^{-j \omega n} = 1\\]

Por lo tanto, podemos decir que la DTFT de un impulso unitario es independiente de la frecuencia y que no tiene componentes en la parte imaginaria (senos).

`Ejemplo`

Calcular la DTFT de

\\[x[n]= \delta[n+1] + 2\delta[n] + 3 \delta[n-1] + 4 \delta[n-2] + 5\delta[n-3]\\]

\\[X(\omega) = \sum\_{n=-\infty}^{\infty} x[n] e^{-j \omega n}\\]

\\[X(\omega) = e^{j\omega} + 2 + 3e^{-j\omega} + 4 e^{-j 2 \omega} + 5 e^{-j3\omega}\\]

La magnitud de una señal se puede obtener como

\\[\textrm{Mag} = |X(\omega)| = \sqrt{\Re^2+\Im^{2}}\\]

Mientras que se ángulo o fase se obtiene como

\\[\textrm{Ang} = \angle X(\omega) = \textrm{atan2}(\Im,\Re)\\]

En MATLAB se haría de la siguiente manera

```octave
w = 0 : (pi/200) : pi;
X = exp(j*w) + 2 + 3*exp(-j*w) + 4*exp(-j*2*w) + 5*exp(-j*3*w);
figure()
subplot 221; plot(w/pi, abs(X)); grid % grafica magnitud
xlabel('w / Pi [rad/m]'); title('Magnitud')

subplot 222; plot(w/pi, angle(X)/pi); grid % grafica ángulo
xlabel('w / Pi [rad/m]'); title('Angulo / Pi [rad]')

subplot 223; plot(w/pi, abs(X)); grid % grafica magnitud
xlabel('w / Pi [rad/m]'); title('Magnitud')

subplot 224; plot(w/pi, unwrap(angle(X))/pi); grid % grafica ángulo con UNWRAP
xlabel('w / Pi [rad/m]'); title('Angulo / Pi [rad]')
```

Quedando como resultado

{{< figure src="/ox-hugo/2021-11-07_15-12-40_screenshot.png" >}}

`Ejemplo`

Si tenemos la siguiente señal
\\[x[n] = 0.5^n u[n]\\]

Recordemos que \\(u[n]\\) es

\\[
u[n]=\begin{cases}0 \quad n<0\\\1 \quad n\geq 1\end{case}
\\]

Por lo tanto, su DTFT quedaría como

\\[X(\omega) = \sum\_{n=0}^{\infty} (0.5e^{-j\omega})^{n}\\]

La sumatoria converge a

\\[X(\omega)=\frac{e^{j\omega}}{e^{j\omega}-0.5}\\]

Para obtener la magnitud en MATLAB sería de la siguiente manera

```octave
w = [-5 : 0.01 : 5] * pi;
X = exp(j*w) ./ (exp(j*w) - 0.5);
figure()
plot(w/pi, abs(X)); grid
xlabel('w / Pi [rad/m]');
title('Magnitud de X(w)');
```

`Ejemplo`

Calcular la IDTFT de

\\[X(\omega) = \delta(\omega+0.2)+ \delta(\omega-0.2)\\]

Aplicando la IDTFT quedaría como

\\[x[n] = \textrm{IDTFT} \left[ X(\omega) \right] = \frac{1}{2 \pi} \int\limits\_{-\pi}^{\pi}X(\omega)e^{j\omega n}d\omega\\]

Ahora reemplazando

\\[x[n]= \frac{1}{2 \pi} \int\limits\_{-\pi}^{\pi}\delta(\omega+0.2)e^{j\omega n}d\omega + \frac{1}{2\pi}\int\limits\_{-\pi}^{\pi}\delta(\omega-0.2)e^{j\omega n}d\omega\\]

\\[x[n] = \frac{1}{2\pi}e^{-j 0.2 n} + \frac{1}{2\pi}e^{j 0.2 n} = \frac{e^{j0.2n}+e^{-j0.2n}}{2\pi}\\]

Ahora si aplicamos la identidad de Euler

\\[\cos(\alpha) = \frac{e^{j\alpha}+e^{-j\alpha}}{2}\\]

Por lo que, la señal quedaría como

\\[x[n]=\frac{1}{\pi}\cos[0.2n]\\]