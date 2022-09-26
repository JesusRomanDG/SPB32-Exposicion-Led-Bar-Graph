
# LED BAR GRAPH (LED DE GRAFICO DE BARRAS)

## Autor: Jesus Roman Dominguez Garcia
#### Presentacion realizara para la materia **SISTEMAS PROGRAMABLES** de la carrera de **INGENIERIA EN SISTEMAS COMPUTACIONALES**.

## Introducción
Con mucha frecuencia, vamos a querer indicar el nivel relativo de algo, bien sea sobre el valor de un potenciómetro, de un sensor de luz,  de un sensor de temperatura, tanque de agua, carga de la batería, fuerza de la señal, o de cualquier otra variable, etc.

Pero para estos casos, regularmente lo que se usa es una serie de LEDS independientes o combinaciones de ellos, por lo que se vuelve mas complicado representar el porcentaje de algo con respecto a su valor maximo.

Utilizar ese sistema funciona, pero es poco práctico y aún menos eficaz como indicador, por eso resulta mas conveniente usar un LED de grafico de barras (LED BAR GRAPH). 

## Sobre el sensor

Este sensor es una serie de LEDs encapsulados en un único chip, listo para utilizarse en los ejemplos mencionados antes. Ademas, este sensor es muy utilizado en diversos equipos, por lo que es muy posible que identifiques alguno en un dispositivo electronico.

Estos sensores son pequeños, baratos y muy eficaces a la hora de mostrar este tipo de señales en porcentaje que se mencionaron antes, y además están diseñados para poder parpadear, y además están disponibles en varios colores.

La conexión es de lo más sencilla, porque al final son simplemente 10 LEDs encapsulados en barritas paralelas, pero se manejan exactamente igual que un LED normal.

#### Aplicaciones
* Controles industriales
* Instrumentación
* Equipo de oficina
* Periféricos de computadora
* Productos de consumo
* Visualización de mensajes en movimiento
* Pantalla digital
* Tableros de puntuación

#### Caracteristicas
* 10 LEDs con control individual
* Alto brillo
* Alta intensidad
* Precio económico
* Tablero de pruebas o tablero Perf amigable
* Cumple con RoHS
* Amplio ángulo de visión

## Esquema
Como se observa en la imagen, los ánodos (Positivo) de los diodos estan posicionados en una cara y los cátodos (Negativo) en la otra…

La conexión de este sensor se realiza colocando una resistencia de limitación de 220Ω a cada LED y conectar los positivos a 10 puertas de nuestro microcontrolador.

La única dificultad, es que en algunos sensores no se muestra ninguna marca indicando el pin número 1, por lo que si este es el caso, hay que probar a ver cuál es. Para ello conectad el positivo y negativo de un único LED y comprobar que se ilumina, antes de conectar el resto.

## Especificaciones
En la tabla a continuacion se muestran algunas de las especificaciones del sensor.

| Especificaciones              | Valor                                       |
|-------------------------------|---------------------------------------------|
| Pines Ánodos                  | Del 1 al 10                                 |
| Pines Cátodos                 | Del 11 al 20                                |
| Corriente de funcionamiento   | 20mA                                        |
| Voltaje directo               | 2.0V a 2.2V (máximo=                        |
| Intensidad luminosa           | 60mcd                                       |
| Longitud de onda              | 630nm                                       |
| Temperatura de funcionamiento | -25℃ a 85℃                                  |
| Temperatura de almacenamiento | -30℃ a 85℃                                  |
| Temperatura de soldadura      | 260℃ durante 5 segundos                     |
| Colores disponibles           | Rojo, Verde, Azul, Amarillo, Naranja, Ámbar |

## Diagrama

## Codigo

## Referencias
`[1]-`[https://www.prometec.net/led-bar/](https://www.prometec.net/led-bar/)
`[2]-`[https://peppe8o.com/using-a-10-segment-led-bar-with-raspberry-pi-and-python/](https://peppe8o.com/using-a-10-segment-led-bar-with-raspberry-pi-and-python/)
`[3]-`[https://components101.com/displays/led-bar-graph](https://components101.com/displays/led-bar-graph)

