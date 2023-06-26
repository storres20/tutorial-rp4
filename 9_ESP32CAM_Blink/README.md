<a name="readme-top"></a>

<div align="center">

  <img src="../rp4logo.png" alt="logo" width="140"  height="auto" />
  <br/>

  <h3><b>9_ESP32CAM_Blink</b></h3>

</div>

# Getting Started With ESP32-CAM

### Link del Tutorial y Bibliografía
```
https://lastminuteengineers.com/getting-started-with-esp32-cam/
```

### Imagen del ESP32-CAM
![image](https://github.com/storres20/tutorial-rp4/assets/81504385/d27fff43-2bce-4d86-be26-4dbe4103088e)

## Configuracion del IDE de ARDUINO para agregar librerias de ESP32-CAM

`Nota:` El propósito de esta configuración es agregar las librerias de ESP32-CAM, para ello debemos realizar lo siguiente:
* Abrir el IDE de ARDUINO
* Click en `File` -> click en `Preferences...`

![image](https://github.com/storres20/tutorial-rp4/assets/81504385/0e516f67-e757-4dc5-9a23-25a1efceed83)

* Click en el `ICONO` que señala la `flecha roja`; el cual, pertenece a `Additional boards manager URLs`

![image](https://github.com/storres20/tutorial-rp4/assets/81504385/d7b37904-cd9c-449c-a345-5751ebe12cc5)

* En el recuadro de `Enter additional URLs, one for each row`, copiar el siguiente Link
```
https://espressif.github.io/arduino-esp32/package_esp32_index.json
```

* Click en el boton `OK`

![image](https://github.com/storres20/tutorial-rp4/assets/81504385/72209e67-d1e5-484c-90e1-4b4657251a3f)

* Click en el `ICONO` de `Boards Manager` (ver flecha roja)

![image](https://github.com/storres20/tutorial-rp4/assets/81504385/fedfeaf8-e170-4985-ab6a-9e77653bcd1f)

* En el `filtro de busqueda`, escribir `ESP32` (ver flecha roja)

![image](https://github.com/storres20/tutorial-rp4/assets/81504385/8d3e7584-87a7-49a6-9bf0-29fd96920a27)

* Click en el boton `INSTALL`

![image](https://github.com/storres20/tutorial-rp4/assets/81504385/b619a361-959e-4aed-b2c2-665983d824d6)

* Esperar unos segundos mientras termina la instalacion de las librerias

![image](https://github.com/storres20/tutorial-rp4/assets/81504385/6459df52-0363-4312-8ee8-6e130343c937)

* Una vez finalizado la instalacion, podemos continuar con los pasos para el Codigo del Parpadeo del Led-Flash del ESP32-CAM

## Código del Parpadeo del Led-Flash del ESP32-CAM para el IDE de ARDUINO

`Nota:`
* Este código debe ser ejecutado en el IDE de ARDUINO
* `Paso 1:` Crear un nuevo sketch (Ctrl + N)
  * En el IDE de ARDUINO, click en la pestaña `File`
  * Luego click en `New Sketch`

![image](https://github.com/storres20/tutorial-rp4/assets/81504385/3b2252e3-cb43-4db1-9d67-c6c6e9a5fe5e)

* `Paso 2:` Seleccionar el Board: `AI Thinker ESP32-CAM`
  * En el IDE de ARDUINO, click en la pestaña `Tools`
  * Luego click en `Board`
  * Click en `Tools` -> click en `Board` -> click en `esp32` -> click en `AI Thinker ESP32-CAM`

![image](https://github.com/storres20/tutorial-rp4/assets/81504385/a0d8645a-43fa-43d3-8460-2c542088e7e4)

* `Paso 3:` Usar el siguiente codigo en el IDE de ARDUINO

```
int flashPin = 4;

void setup() {
    pinMode(flashPin, OUTPUT);
}

void loop() {
    digitalWrite(flashPin, HIGH);
    delay(1000);
    digitalWrite(flashPin, LOW);
    delay(1000);
}
```

### Imagen del Código en el IDE de ARDUINO

![esp32cam-flash](https://github.com/storres20/tutorial-rp4/assets/81504385/b5403178-3347-4438-995b-27d2789c9b28)

`Nota:`
* El `flashPin = 4` hace referencia al GPIO4 del ESP32-CAM
* Prueba de ello se va a mostrar parte del archivo esquemático del ESP32-CAM
* Link del archivo esquemático: 

```
https://docs.ai-thinker.com/_media/esp32/docs/esp32_cam_sch.pdf
```

* La señal de salida del `GPIO4` o también llamado `HS2_DATA1` del `ESP32-CAM` permite la activación o desactivación del transistor `Q1 S8050`; lo cual, permite el encendido y/o apagado del `LED_FLASH`

![image](https://github.com/storres20/tutorial-rp4/assets/81504385/51164032-98e9-4ece-9086-c006c6e7d051)

![image](https://github.com/storres20/tutorial-rp4/assets/81504385/77bb6338-1a6b-4cda-884f-70ec7a58ecc8)

## Conversor USB a TTL

* El ESP32-CAM no cuenta con un puerto USB; por ello, la necesidad del conversor USB a TTL para lograr la comunicación entre el ESP32-CAM y la PC
* Producto de esta comunicación, se lograría la programación del ESP32-CAM con el algoritmo deseado (parpadeo de led, cámara web, etc.) por medio del IDE de ARDUINO hacia el conversor USB-TTL y el ESP32-CAM

![image](https://github.com/storres20/tutorial-rp4/assets/81504385/614bf6c1-39bd-4f4a-b79a-992b13b128cd)

### Imagen del conversor de USB a TTL utilizado para el presente proyecto
![image](https://github.com/storres20/tutorial-rp4/assets/81504385/c857c7e9-1bf6-4ffa-bd97-2f1d0626eed5)

Link de la documentación del conversor:

```
http://magicduino.com/Images/ItemsMedia/File/7279.pdf
```

### Jumper para 3.3v y/o 5v en conversor de USB a TTL
![image](https://github.com/storres20/tutorial-rp4/assets/81504385/d974bf54-0aae-4345-ba84-ddb5f161f5f5)

* El conversor USB-TTL presenta pines de salida de 5v y 3.3v
* El uso de un pin de 5v o un pin 3.3v va a depender de la naturaleza del proyecto
* En este caso va a depender, del voltaje con el cual el conversor USB-TTL va a alimentar al ESP32-CAM
* `Nota:` El ESP32-CAM puede ser alimentado con 5v o 3.3v
* Para el proyecto del Parpadeo del Led-Flash, se va a utilizar el pin de salida de 3.3v del conversor USB-TTL y el ESP32-CAM será alimentado con 3.3v
* Asimismo, no se utilizará el JUMPER de color amarillo en los pines VCC y 3V3; sin embargo, se utilizará un cable adicional para alimentar al pin VCC con los 3.3v provenientes del pin 3V3

### Conexion entre ESP32-CAM y conversor USB-TTL

![image](https://github.com/storres20/tutorial-rp4/assets/81504385/92dde4a9-c286-4066-8ecc-b91a734ac7f0)

* Conectar el conversor USB-TTL a la PC
* 




https://github.com/storres20/tutorial-rp4/assets/81504385/fe57b2d5-9e63-4c3e-bdce-dbe3ccb6124f




