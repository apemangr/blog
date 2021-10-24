+++
title = "CLAGISC: Functions and Data"
date = 2021-10-19T00:00:00-03:00
draft = false
+++

## 1.1 Introducción {#1-dot-1-introducción}

En este capítulo se tratarán temas básicos acerca de el lenguaje, donde se veran algunas funciones básicas. Si se tienen conocimentos previos de programación este capitulo se puede saltar.


## 1.2 Functions on numbers {#1-dot-2-functions-on-numbers}

Las primeras funciones que se verán son las aritméticas, ya que son las más básicas. Tenemos la función de suma que se representa con un "+". Aqui se tiene una representación gráfica.

{{< figure src="/ox-hugo/2021-10-15_23-50-30_screenshot.png" >}}

A continuación una tabla con operaciones básicas

| Función | Descripción                            |
|---------|----------------------------------------|
| +       | Suma dos números                       |
| -       | Resta dos numeros                      |
| \*      | Multiplica dos números                 |
| /⁢       | Divide dos números                     |
| ABS     | Obtiene el valor absoluto de un número |
| SQRT    | Obtiene la raíz cuadrada de un número  |


## 1.3 Three kinds of numbers {#1-dot-3-three-kinds-of-numbers}

Existen tres tipos de números, los enteros, los punto flotante que son los que siempre van a estar acompañados de una parte decimal y los fraccionarios. La función SQRT por ejemplo siempre devuelve un número punto flotante, sin importar si ingresamos un entero.

{{< figure src="/ox-hugo/2021-10-19_22-02-12_screenshot.png" >}}

Los numeros fracionarios se pueden escribir tal cual en Common Lisp, por ejemplo en una calculadora si ingresamos "un medio", la calculadora lo representará como 0.5, mientras que Common Lisp como 1/2. Siempre Common Lisp tratará de simplificar las fracciones para que tengan los menores numeradores y denominadores.

Si hacemos operaciones aritméticas con numeros enteros por lo general se obtendran números expresados en fraciones, mientras que si trabajamos con enteros y punto flotante, obtendremos valores en punto flotante.

{{< figure src="/ox-hugo/2021-10-19_22-06-59_screenshot.png" >}}


## 1.4 Order of inputs is important {#1-dot-4-order-of-inputs-is-important}

Cuando realizamos operaciones aritméticas es importante fijarnos en el orden en que colocamos los números, ya que si por ejemplo quisiecemos dividir 8 entre 2 tendriamos que hacerlo de la siguiente manera:

```common-lisp
(/ 8 2) ; Manera correcta

(/ 2 8) ; Manera incorrecta puesto que estamos dividiende 2 entre 8
```


## 1.5 Symbols {#1-dot-5-symbols}

Los símbolos son otro tipo de datos en Lisp. Generalmente son palabras en inglés como "SQRT" para "Square Root", pueden contentener cualquier combinanción de letras, números y algunos caracteres especiales como los guiones. Es importante notar que aunque los símbolos pueden contener números esto no los hace números. Aqui hay algunas definiciones para ayudar.

-   Enteros:  Secuencia de dígitos de 0 a 9, opcionalmente pueden contener un signo + o -.
-   Símbolos: Secuencia de letras, digitos y caracteres especiales que no sean números.

Por lo tanto, FOUR es un símbolo, 4 es un entero, +4 también es un entero, pero + es un símbolo. Y 7-11 es también un símbolo.


## 1.6 The special symbols T and NIL {#1-dot-6-the-special-symbols-t-and-nil}

Existen dos tipos de símbolos en Lisp que tienen un significado especial. Ellos son:

-   **T**      Verdadero, "SI"
-   **NIL**    Falso, vacío, "NO"

Ciertas funciones que responden a la pregunta "Si o no" devuelven un valor de T o NIL. Este tipo de funciones son llamadas "predicados".


## 1.7 Some simple predicates {#1-dot-7-some-simple-predicates}

Un predicado es una función que busca responder a una pregunta. Un predicado devolverá el símbolo T cuando quiera decir "SÍ" y un símbolo NIL cuando quiera decir "NO". El primer predicado a estudiar es "NUMBERP" que significa "Number predicate" y se pronuncia "number-pee", y lo que hace es verificar si la entrada es un número o no.

{{< figure src="/ox-hugo/2021-10-19_22-31-00_screenshot.png" >}}

Igualmente tenemos el predicado "SYMBOLP" que lo que hace es checkear si la entrada es un símbolo o no, devuelve T si es un símbolo y NIL si no.

{{< figure src="/ox-hugo/2021-10-19_22-32-19_screenshot.png" >}}

También esta "ZEROP" que ve si un número es 0 o no.

{{< figure src="/ox-hugo/2021-10-19_22-33-33_screenshot.png" >}}

"ODDP" verifica si un número es impar y devuelve T si no NIL. "EVENP" hace lo mismo pero con los pares.

{{< figure src="/ox-hugo/2021-10-19_22-36-09_screenshot.png" >}}

Aqui hay dos predicados más: "<" devuelve T si la primera entrada es menor que la segunda y ">" devuelve T si la primera entrada es mayor que la segunda. Estos predicados son algunas de las excepciones de los predicados a llevar P.

{{< figure src="/ox-hugo/2021-10-19_22-38-13_screenshot.png" >}}


## 1.8 The equal predicate {#1-dot-8-the-equal-predicate}

El predicado EQUAL compara dos cosas y si estas son iguales retorna T sino NIL. Existen varios predicados parecidos como EQ, EQL, EQUALP, pero por ahora con EQUAL esta bien.

{{< figure src="/ox-hugo/2021-10-23_20-42-44_screenshot.png" >}}


## 1.9 Putting functions together {#1-dot-9-putting-functions-together}

Hasta el momento solo hemos visto funciones primitivas que vienen por defecto en Common Lisp. Crearemos nuevas funciones a partir de estas funciones primitivas.


### 1.9.1 Defining ADD1 {#1-dot-9-dot-1-defining-add1}

Definamos una función llamada "ADD1" que lo único que hará será sumar 1 a la entrada.

{{< figure src="/ox-hugo/2021-10-23_20-46-39_screenshot.png" >}}


### 1.9.2 Defining ADD2 {#1-dot-9-dot-2-defining-add2}

Ahora supongamos que queremos definir una función que sume dos a la entrada. En Lisp siempre hay varias formas de hacer las cosas, ya que podriamos hacer uso de la función ADD1 dos veces para crear ADD2.

{{< figure src="/ox-hugo/2021-10-23_20-49-57_screenshot.png" >}}


### 1.9.3 Defining TWOP {#1-dot-9-dot-3-defining-twop}

Ahora podemos crear nuestros conocimentos para crear predicados, en este caso uno que verifique si la entrada es igual a 2 y de ser así retorne T, sinó NIL.

{{< figure src="/ox-hugo/2021-10-23_20-51-55_screenshot.png" >}}


### 1.9.4 Defining ONEMOREP {#1-dot-9-dot-4-defining-onemorep}

Vamos a definir un predicado que tenga dos entradas y verifique si la primera entrada es exactamente 1 más grande que la segunda entrada.

{{< figure src="/ox-hugo/2021-10-23_20-55-25_screenshot.png" >}}


## 1.10 The NOT predicate {#1-dot-10-the-not-predicate}

NOT es el predicado opuesto. Transforma un T en un NIL y un NIL en un T. Es interesante ver todos los usos que se le puede dar, por ejemplo si queremos comprobar si un número no es igual a otro podriamos juntar un NOT y un EQUAL.


## 1.11 Negating a predicate {#1-dot-11-negating-a-predicate}

Ahora veremos de forma más gráfica a lo que se mencionó anteriormente. Para ver si un número no es igual a otro primero usamos un EQUAL y luego un NOT para negar la salida de este.

{{< figure src="/ox-hugo/2021-10-23_21-02-01_screenshot.png" >}}


## 1.12 Number of inputs to a function {#1-dot-12-number-of-inputs-to-a-function}

Hay algunas funciones que tienen un número fijo de argumentos como por ejemplo, ODDP o EQUAL. Sin embargo también existen funciones que pueden tomar cualquier número de argumentos. Como es el caso de los funciones de aritmética básica (+ - / \*). En el caso de la multiplicación lo que hace es multiplicar los primeros dos argumentos y el resultado de estos multiplicarlo al tercer argumento.

{{< figure src="/ox-hugo/2021-10-23_21-09-26_screenshot.png" >}}

Cuando utilizamos la función de resta "-" con un solo argumento lo que nos entregará será el inverso aditivo del número que hallamos ingresado, ya que a 0 le restará la entrada. Algo similar ocurre cuando utilizamos la función de división con un solo argumento, en este caso nos entrega el recíproco de la entrada, ya que a 1 lo dividirá entre la entrada.

{{< figure src="/ox-hugo/2021-10-23_21-11-55_screenshot.png" >}}


## 1.13 Errors {#1-dot-13-errors}

A la hora de crear nuestras funciones podemos cometer errores como por ejemplo asignar un tipo de dato incorrecto. En el caso de la función + que sólo acepta números, le podriamos pasar una cadena de texto, otro error es pasarle un número incorrecto de argumentos, como pasarle un argumento a la función EQUAL. Otro error común es cuando dividimos por 0, que por supuesto que también está mal.