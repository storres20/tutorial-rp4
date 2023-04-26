<a name="readme-top"></a>

<div align="center">

  <img src="../rp4logo.png" alt="logo" width="140"  height="auto" />
  <br/>

  <h3><b>4_Led_blink</b></h3>

</div>

`Nota:` Este README contiene el codigo para el Led_blink (parpadeo del Led) y además un video demostrativo

`Paso 1:` Conocer e identificar la distribucion de Pines de Salida (PINOUT) del Raspberry Pi

En la siguiente pagina web https://pinout.xyz/ usted encontrará principalmente 02 tipos de distribuciones de Pines de Salida; los cuales son, BOARD y BCM.

La distribucion de `pines BOARD` indica a la numeracion que se le asigna a cada Pin de Salida `(por ejemplo: 1,2,3,4,5,...)`

La distribucion de `pines BCM` indica al término GPIO asignado a cada Pin de Salida `(por ejemplo: GPIO2, GPIO3, GPIO4,...)`

Sin embargo, para el `presente proyecto`, se utilizará la `distribucion de PINES en BCM`

Ver la siguiente imagen para mayor detalle

![Screenshot from 2023-04-09 01-05-03](https://user-images.githubusercontent.com/81504385/230757358-6c6da901-e4ce-418e-a6e0-ecdab4b0dfb9.png)

`Paso 2:` Crear una nueva carpeta `(por ejemplo: Led_blink)`

![2023-04-23-230050_1920x1080_scrot](https://user-images.githubusercontent.com/81504385/233897530-cca96a5d-b989-447d-8bdf-271db8799f35.png)

`Paso 3:` Crear archivo con extension .py `(por ejemplo: blink.py)`

![2023-04-23-230139_1920x1080_scrot](https://user-images.githubusercontent.com/81504385/233897646-19b81cb0-d83e-44ea-bbef-460bdae6fcfd.png)

`Paso 4:` Dar doble click al archivo creado y se abrirá el IDE DE GEANY

![2023-04-23-230221_1920x1080_scrot](https://user-images.githubusercontent.com/81504385/233897750-80c86add-c806-4f43-b8b0-c28f693e6e67.png)

`Paso 5:` Copiar el siguiente codigo del Led_blink (parpadeo del Led)

```python
import RPi.GPIO as GPIO
from time import sleep
 
GPIO.setwarnings(False)
GPIO.setmode(GPIO.BCM)
GPIO.setup(7, GPIO.OUT, initial=GPIO.LOW)
GPIO.setup(12, GPIO.OUT, initial=GPIO.HIGH)

try: 
	while True:
		GPIO.output(7, GPIO.HIGH)
		GPIO.output(12, GPIO.LOW)
		print("LED on @ GPIO 7")
		print("LED off @ GPIO 12")
		sleep(1)
		GPIO.output(7, GPIO.LOW)
		GPIO.output(12, GPIO.HIGH)
		print("LED off @ GPIO 7")
		print("LED on @ GPIO 12")
		sleep(1)

except KeyboardInterrupt:
    GPIO.cleanup()

```

`Paso 6:` Codigo del Led_blink en GEANY

![Screenshot from 2023-04-26 01-39-34](https://user-images.githubusercontent.com/81504385/234490732-8efab752-ecc0-4f98-8f04-50aaac1af473.png)

`Paso 7:` Explicacion del codigo

```python
import RPi.GPIO as GPIO # permite controlar todos los Pines de Salida del Raspberry Pi
from time import sleep # permite agregar un retardo en "segundos"
 
GPIO.setwarnings(False) # desactiva todas las falsas alertas
GPIO.setmode(GPIO.BCM) # nos permite utilizar los numeros GPIO (distribucion de pines en BCM)
GPIO.setup(7, GPIO.OUT, initial=GPIO.LOW) # el pin GPIO 7 se inicializa en LOW ("0" logico)
GPIO.setup(12, GPIO.OUT, initial=GPIO.HIGH) # el pin GPIO 12 se inicializa en HIGH ("1" logico)

try: 
	while True: # bucle infinito
		GPIO.output(7, GPIO.HIGH) # se asigna al pin GPIO 7 en HIGH ("1" logico)
		GPIO.output(12, GPIO.LOW) # se asigna al pin GPIO 12 en LOW ("0" logico)
		print("LED on @ GPIO 7") # imprime en la terminal el valor contenido dentro del metodo print(...)
		print("LED off @ GPIO 12") # imprime en la terminal el valor contenido dentro del metodo print(...)
		sleep(1) # agrega un retardo de 1 segundo
		GPIO.output(7, GPIO.LOW) # se asigna al pin GPIO 7 en LOW ("0" logico)
		GPIO.output(12, GPIO.HIGH) # se asigna al pin GPIO 12 en HIGH ("1" logico)
		print("LED off @ GPIO 7") # imprime en la terminal el valor contenido dentro del metodo print(...)
		print("LED on @ GPIO 12") # imprime en la terminal el valor contenido dentro del metodo print(...)
		sleep(1) # agrega un retardo de 1 segundo

# para detener el bucle infinito de la terminal, se presiona los comando Ctrl + C
# En ese momento se activa esta linea de codigo
except KeyboardInterrupt: 
    GPIO.cleanup() # esto resetea todos los estados y modos de los pines GPIO

```

`Paso 8:` En el IDE de GEANY, dar click en el icono de `Avion de Papel` para ejecutar el codigo

![Screenshot from 2023-04-23 23-44-40](https://user-images.githubusercontent.com/81504385/233902070-eaf855dc-ee21-4ad7-82dd-09d7472f0d47.png)

`Paso 9:` Codigo en ejecucion en la terminal

![2023-04-09-003833_984x630_scrot](https://user-images.githubusercontent.com/81504385/233902916-c9831019-ac54-4dfa-99c2-d59f09ba6b1b.png)

`Paso 10:` Para detener la ejecucion, presionar `Ctrl + C`

`Paso 11:` Componentes electronicos

* 02 Leds - el color puede ser cualquiera

* 02 resistencias de 1k ohms (marron-negro-negro)

* Juegos de cables macho-hembra

* 01 protoboard

* 01 raspberry pi

`imagen referencial`

![Screenshot from 2023-04-24 00-24-10](https://user-images.githubusercontent.com/81504385/233906867-81ad1fdf-4c41-4f0b-9264-b25030f9d7ba.png)

`Paso 12:` Conexiones y cableado

Conectar un cable macho-hembra desde algun `pin 5v Power del Raspberry Pi` hacia la linea general Positiva del `Protoboard`

Conectar un cable macho-hembra desde algun `pin GROUND del Raspberry Pi` hacia la linea general Negativa del `Protoboard`

Conectar un cable macho-hembra desde el `pin GPIO 7 del Raspberry Pi` hacia el `Protoboard`

Conectar un cable macho-hembra desde el `pin GPIO 12 del Raspberry Pi` hacia el `Protoboard`

`1er Led`

Conectar en serie el `pin GPIO 7`, el Led, la resistencia de 1k ohm y GROUND `(similar a la imagen referencial)`

`2do Led`

Conectar en serie el `pin GPIO 12`, el Led, la resistencia de 1k ohm y GROUND `(similar a la imagen referencial)`


## Video demostrativo

https://user-images.githubusercontent.com/81504385/230756887-a69dd50a-6f86-4fc7-bc26-a0756c310394.mp4

## Bibliografia

- https://roboticsbackend.com/raspberry-pi-control-led-python-3/

- https://www.maketecheasier.com/make-blinking-leds-with-raspberry-pi/

- https://pinout.xyz/
