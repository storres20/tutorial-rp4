<a name="readme-top"></a>

<div align="center">

  <img src="../rp4logo.png" alt="logo" width="140"  height="auto" />
  <br/>

  <h3><b>8_H_Bridge</b></h3>

</div>

`Nota:` El `H-Bridge` o `Puente H`, es un componente electrónico basado en el `controlador L298N`, usado para controlar la marcha y sentido de giro de motores DC.

![image](https://github.com/storres20/tutorial-rp4/assets/81504385/cefcb90b-250e-44f7-aa8a-472a7135a958)

`PASO 1:` Detalle de los pines y conexiones del `Puente H`

![image](https://github.com/storres20/tutorial-rp4/assets/81504385/08721621-4836-4169-9ace-06a5c8a69535)

* Pines `input1`, `input2`, `input3`, `input4`: Son pines que reciben señal proveniente desde el `Raspberry PI`. El proposito de estas señales es controlar el sentido de giro del motor (horario o antihorario)

* Pines `input1`, `input2`: Controlan el sentido de giro del `Motor A`

* Pines `input3`, `input4`: Controlar el sentido de giro del `Motor B`

* `Motor A`: Aca se pueden apreciar 02 pines de salida. El `Puente H - L298N` suministra un voltaje de salida a estos pines para alimentar al Motor DC. Dicho voltaje es continuo (DC). Su polaridad y su cambio de polaridad, va a depender directamente de los pines `input1` y `input2`. Además, estará limitado a 5V si el `5V Select Jumper` se encuentra habilitado y si no se encuentra habilitado, el voltaje de salida será igual al voltaje ingresado por los pines `7V-35V` y `GND`.

* `Motor B`: Aca se pueden apreciar 02 pines de salida. El `Puente H - L298N` suministra un voltaje de salida a estos pines para alimentar al Motor DC. Dicho voltaje es continuo (DC). Su polaridad y su cambio de polaridad, va a depender directamente de los pines `input3` y `input4`. Además, estará limitado a 5V si el `5V Select Jumper` se encuentra habilitado y si no se encuentra habilitado, el voltaje de salida será igual al voltaje ingresado por los pines `7V-35V` y `GND`.

* `Enable A`: Habilita la recepcion de señales en los pines `input1` e `input2`

* `Enable B`: Habilita la recepcion de señales en los pines `input3` e `input4`

* Pines `7V-35V` y `GND`: Estos pines son para conectar una fuente de poder externa (en el rango de voltaje entre 7V y 35V) el cual alimentará al o los motores DC. El pin `7V-35V` es para la toma positiva y el pin `GND` para la toma negativa

* `5V Select Jumper`: Al estar presente este Jumper, se habilita el Regulador de 5V del componente electronico `Puente H - L298N`; lo cual, permite que el voltaje final suministrado al o los motores DC sea de 5V.

`Por ejemplo`:
Si a los pines `7V-35V` y `GND` se les alimenta con `12V`, al estar habilitado el `5V Select Jumper`, el voltaje final de suministro al o los motores DC será de 5V

`Nota`:
Durante las pruebas de ensayo, con el `5V Select Jumper` habilitado, se ha logrado alimentar los pines `7V-35V` y `GND` con la alimentacion del Raspberry PI (Se utilizó los pines `5V Power` y `Ground` del Raspberry PI). El Raspberry PI tuvo la suficiente potencia para movilizar 02 motores DC en simultaneo

Para mayor detalle, revisar la siguiente documentacion del `Puente H - L298N`:

```
https://components101.com/modules/l293n-motor-driver-module
```

`PASO 2:` Conexiones entre `Puente H - L298N` y el Raspberry PI

### Pines del Raspberry PI

![image](https://github.com/storres20/tutorial-rp4/assets/81504385/eed2f39f-aba7-42af-abcc-ea8d907d2255)

![image](https://github.com/storres20/tutorial-rp4/assets/81504385/eb092a54-cf34-4b7e-81a1-bc7f7a8c4c5b)


`PASO 3:` Se crea el archivo `puenteh.py` para el control de 02 motores DC pero no en simultaneo

`Nota:`

* Los pines `GPIO17` y `GPIO22` del Raspberry PI son conectados a los pines `input1` y `input2` respectivamente del `Puente H - L298N` para el control del `Motor A`
* Los pines `GPIO23` y `GPIO24` del Raspberry PI son conectados a los pines `input3` y `input4` respectivamente del `Puente H - L298N` para el control del `Motor B`
* Los pines `5V Power` y `GROUND` del Raspberry PI son conectados a los pines `7V-35V` y `GND` respectivamente del `Puente H - L298N` para la alimentacion de los Motores DC

### puenteh.py

```
import RPi.GPIO as gpio
import time
def init():
gpio.setmode(gpio.BCM)
gpio.setup(17, gpio.OUT, initial=gpio.LOW)
gpio.setup(22, gpio.OUT, initial=gpio.LOW)
gpio.setup(23, gpio.OUT, initial=gpio.LOW)
gpio.setup(24, gpio.OUT, initial=gpio.LOW)

def motora_forward(sec):
init()
gpio.output(17, False)
gpio.output(22, True)
time.sleep(sec)
gpio.cleanup()

def motora_reverse(sec):
init()
gpio.output(17, True)
gpio.output(22, False)
time.sleep(sec)
gpio.cleanup()

def motorb_forward(sec):
init()
gpio.output(23, False)
gpio.output(24, True)
time.sleep(sec)
gpio.cleanup()

def motorb_reverse(sec):
init()
gpio.output(23, True)
gpio.output(24, False)
time.sleep(sec)
gpio.cleanup()

seconds = 1

print("motora_forward")
motora_forward(seconds)
time.sleep(seconds)

print("motora_reverse")
motora_reverse(seconds)
time.sleep(seconds)

print("motorb_forward")
motorb_forward(seconds)
time.sleep(seconds)

print("motorb_reverse")
motorb_reverse(seconds)
time.sleep(seconds)
```

`PASO 4:` Se crea el archivo `puenteh2.py` para el control de 02 motores DC en simultaneo

`Nota:`

* Los pines `GPIO17` y `GPIO22` del Raspberry PI son conectados a los pines `input1` y `input2` respectivamente del `Puente H - L298N` para el control del `Motor A`
* Los pines `GPIO23` y `GPIO24` del Raspberry PI son conectados a los pines `input3` y `input4` respectivamente del `Puente H - L298N` para el control del `Motor B`
* Los pines `5V Power` y `GROUND` del Raspberry PI` son conectados a los pines `7V-35V` y `GND` respectivamente del `Puente H - L298N` para la alimentacion de los Motores DC

### puenteh2.py

```
import RPi.GPIO as gpio
import time
def init():
gpio.setmode(gpio.BCM)
gpio.setup(17, gpio.OUT, initial=gpio.LOW)
gpio.setup(22, gpio.OUT, initial=gpio.LOW)
gpio.setup(23, gpio.OUT, initial=gpio.LOW)
gpio.setup(24, gpio.OUT, initial=gpio.LOW)

def motorab_forward(sec):
init()
gpio.output(17, False)
gpio.output(22, True)
gpio.output(23, False)
gpio.output(24, True)
time.sleep(sec)
gpio.cleanup()

def motorab_reverse(sec):
init()
gpio.output(17, True)
gpio.output(22, False)
gpio.output(23, True)
gpio.output(24, False)
time.sleep(sec)
gpio.cleanup()

seconds = 1

print("motorab_forward")
motorab_forward(seconds)
time.sleep(seconds)

print("motorab_reverse")
motorab_reverse(seconds)
time.sleep(seconds)

print("motorab_forward")
motorab_forward(seconds)
time.sleep(seconds)

print("motorab_reverse")
motorab_reverse(seconds)
time.sleep(seconds)
```
