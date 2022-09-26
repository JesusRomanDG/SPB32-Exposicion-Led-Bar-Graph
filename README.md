
# LED BAR GRAPH (LED DE GRAFICO DE BARRAS)

## Autor: Jesus Roman Dominguez Garcia
#### Presentacion realizara para la materia **SISTEMAS PROGRAMABLES** de la carrera de **INGENIERIA EN SISTEMAS COMPUTACIONALES**.

## Introducción
Con mucha frecuencia, vamos a querer indicar el nivel relativo de algo, bien sea sobre el valor de un potenciómetro, de un sensor de luz,  de un sensor de temperatura, tanque de agua, carga de la batería, fuerza de la señal, o de cualquier otra variable, etc.

Pero para estos casos, regularmente lo que se usa es una serie de LEDS independientes o combinaciones de ellos, por lo que se vuelve mas complicado representar el porcentaje de algo con respecto a su valor maximo.

Utilizar ese sistema funciona, pero es poco práctico y aún menos eficaz como indicador, por eso resulta mas conveniente usar un LED de grafico de barras (LED BAR GRAPH). 

## Sobre el sensor

![](/img/1815-00.jpg)
![](/img/1815-01.jpg)
![](/img/1815-02.jpg)
![](/img/1815-03.jpg)

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

La conexión de este sensor se realiza colocando una resistencia de limitación de 220Ω a cada LED y conectar los positivos a 10 puertas de nuestro microcontrolador.

![](/img/LED-Bar-Graph-Pinout.png)
> Como se observa en la imagen, los ánodos (Positivo) de los diodos estan posicionados en una cara y los cátodos (Negativo) en la otra…

La única dificultad, es que en algunos sensores no se muestra ninguna marca indicando el pin número 1, por lo que si este es el caso, hay que probar a ver cuál es. Para ello conectad el positivo y negativo de un único LED y comprobar que se ilumina, antes de conectar el resto.

![](/img/LED-Bar-Graph-Connection-with-Micro-controller.png)
> En la anterior imagen se muestra un ejemplo de un diagrama de conexion hacia un microcontrolador.

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
> En la siguiente imagen se muestran las conexiones realizadas entre los componentes y la raspberry pi pico.

![](/img/diagrama.png)

## Codigo
```python
# Autor: Dominguez Garcia Jesus Roman
# Usuario Github: JesusRomanDG
# Fecha: 26 de Septiembre de 2022

# importando las librerias a utilizar
import time
import board
import digitalio
from analogio import AnalogIn

# definiendo entrada analoga del potenciometro
analog_in = AnalogIn(board.GP26)

# definiedno entradas digitales de los leds del Led Bar Graph
led1 = digitalio.DigitalInOut(board.GP15)
led2 = digitalio.DigitalInOut(board.GP14)
led3 = digitalio.DigitalInOut(board.GP13)
led4 = digitalio.DigitalInOut(board.GP12)
led5 = digitalio.DigitalInOut(board.GP11)
led6 = digitalio.DigitalInOut(board.GP7)
led7 = digitalio.DigitalInOut(board.GP6)
led8 = digitalio.DigitalInOut(board.GP5)
led9 = digitalio.DigitalInOut(board.GP4)
led10 = digitalio.DigitalInOut(board.GP3)

# metodo para obtener e imprimir el voltaje del potenciometro desde la entrada analogica
def obtener_voltaje(pin):
  return (pin.value / 65536) * 100

# metodo para determinar que leds encender
def determinar_Led(min, pin):
  if(obtener_voltaje(analog_in) > min):   # si el valor del potenciometro es mayor que el minimo necesario para cierto led, entonces se encendera
    pin.direction = digitalio.Direction.OUTPUT
    pin.value = True  # enciende el led conectado al pin dado

  else:     # si no se cumple la entrada necesaria entonces se apaga el led
    pin.direction = digitalio.Direction.OUTPUT
    pin.value = False # apaga el led conectado al pin dado

# ciclo
while True:
  valorPotenciometro = obtener_voltaje(analog_in) # llama al metodo obtener_Voltaje y lo almacena en una variable
  print(valorPotenciometro) # imprime el valor del potenciometro
  time.sleep(0.1) # delay de 0.1 segundos

# llamadas al metodo determinar_Led para encender o apagar los leds correspondientes
  determinar_Led(0, led1)
  determinar_Led(10, led2)
  determinar_Led(20, led3)
  determinar_Led(30, led4)
  determinar_Led(40, led5)
  determinar_Led(50, led6)
  determinar_Led(60, led7)
  determinar_Led(70, led8)
  determinar_Led(80, led9)
  determinar_Led(90, led10)

```

#### Link del codigo y el diagrama: [https://wokwi.com/projects/343854896568599123](https://wokwi.com/projects/343854896568599123)

## Referencias
* [https://www.prometec.net/led-bar/](https://www.prometec.net/led-bar/)
* [https://peppe8o.com/using-a-10-segment-led-bar-with-raspberry-pi-and-python/](https://peppe8o.com/using-a-10-segment-led-bar-with-raspberry-pi-and-python/)
* [https://components101.com/displays/led-bar-graph](https://components101.com/displays/led-bar-graph)
* [https://www.adafruit.com/product/1815](https://www.adafruit.com/product/1815)
* [https://docs.wokwi.com/parts/wokwi-pi-pico](https://docs.wokwi.com/parts/wokwi-pi-pico)
* [https://docs.wokwi.com/guides/circuitpython](https://docs.wokwi.com/guides/circuitpython)
* [https://docs.wokwi.com/parts/wokwi-led-bar-graph](https://docs.wokwi.com/parts/wokwi-led-bar-graph)
* [https://docs.wokwi.com/parts/wokwi-potentiometer](https://docs.wokwi.com/parts/wokwi-potentiometer)
* [https://docs.wokwi.com/guides/diagram-editor](https://docs.wokwi.com/guides/diagram-editor)
* [https://learn.adafruit.com/esenciales-para-circuitpython/entradas-analogicas-circuitpython](https://learn.adafruit.com/esenciales-para-circuitpython/entradas-analogicas-circuitpython)
