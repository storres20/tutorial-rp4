<a name="readme-top"></a>

<div align="center">

  <img src="../rp4logo.png" alt="logo" width="140"  height="auto" />
  <br/>

  <h3><b>5_LCD</b></h3>

</div>

`Nota:` Este README contiene el codigo para el Led_blink (parpadeo del Led) y además un video demostrativo

`Paso 1:` Conocer e identificar la distribucion de Pines de Salida (PINOUT) del Raspberry Pi

En la siguiente pagina web https://pinout.xyz/ usted encontrará principalmente 02 tipos de distribuciones de Pines de Salida; los cuales son, BOARD y BCM.

La distribucion de `pines BOARD` indica a la numeracion que se le asigna a cada Pin de Salida `(por ejemplo: 1,2,3,4,5,...)`

La distribucion de `pines BCM` indica al término GPIO asignado a cada Pin de Salida `(por ejemplo: GPIO2, GPIO3, GPIO4,...)`

Sin embargo, para el `presente proyecto`, se utilizará la `distribucion de PINES en BCM`

Ver la siguiente imagen para mayor detalle

![Screenshot from 2023-04-09 01-05-03](https://user-images.githubusercontent.com/81504385/230757358-6c6da901-e4ce-418e-a6e0-ecdab4b0dfb9.png)

`Paso 2:` Crear una nueva carpeta `(por ejemplo: proyectoLCD)`

![2023-04-26-014131_1920x1080_scrot](https://user-images.githubusercontent.com/81504385/234491151-0252fea5-9221-4f23-896c-d9ae5c13d68a.png)

`Paso 3:` Abrir dicha nueva carpeta en la Terminal

![Screenshot from 2023-04-26 01-44-40](https://user-images.githubusercontent.com/81504385/234491594-d834d90e-2099-4821-82eb-611818b1f0b7.png)

`Paso 4:` Clonar repositorio del proyecto LCD

- Autor: [@the-raspberry-pi-guy](https://github.com/the-raspberry-pi-guy)

Ingresar el siguiente comando en la Terminal

```
git clone https://github.com/the-raspberry-pi-guy/lcd.git
```

Al termino de la ejecucion del presente comando, se creará la carpeta `lcd` con los archivos demos para el LCD

![Screenshot from 2023-04-26 01-48-57](https://user-images.githubusercontent.com/81504385/234492528-fb0188aa-1a1c-4247-bbbf-46c8f4708aa0.png)

`Paso 5:` Ingresar a la carpeta `lcd`

Ingresar el siguiente comando en la terminal

```
cd lcd
```

Para visualizar el contenido de la carpeta `lcd`, ingresar el siguiente comando

```
ls
```

![Screenshot from 2023-04-26 01-59-23](https://user-images.githubusercontent.com/81504385/234495090-1a39be0b-0883-481c-9959-88f8d5e925ac.png)

`Paso 6:` Ejecutamos el script de instalacion

```
sudo ./install.sh
```

![Screenshot from 2023-04-26 01-51-27](https://user-images.githubusercontent.com/81504385/234493393-e178873d-d100-49c2-8808-2ec535ad751d.png)

`Paso 7:` Ejecutamos las DEMOS `(por ejemplo: demo_lcd.py)`

`imagen del total de DEMOS en la carpeta lcd`

![Screenshot from 2023-04-26 01-59-23](https://user-images.githubusercontent.com/81504385/234495090-1a39be0b-0883-481c-9959-88f8d5e925ac.png)

Para ejecutar el archivo `demo_lcd.py` ingresamos el siguiente comando en la terminal

```
python demo_lcd.py
```

![Screenshot from 2023-04-26 02-16-21](https://user-images.githubusercontent.com/81504385/234499011-03a7b158-ca7d-4090-96a2-e3821f261609.png)

A continuacion en la pantalla LCD podra visualizar lo siguiente:

![demo_simple_strings](https://user-images.githubusercontent.com/81504385/234498573-2cdc044f-7dd2-4cd1-bad7-7cf1b0613b2e.jpg)

- Author: [@Tomtom0201](https://github.com/Tomtom0201)

`Paso 8:` Ejecutamos las DEMOS `(por ejemplo: demo_clock_and_IP.py)`

`imagen del total de DEMOS en la carpeta lcd`

![Screenshot from 2023-04-26 01-59-23](https://user-images.githubusercontent.com/81504385/234495090-1a39be0b-0883-481c-9959-88f8d5e925ac.png)

Para ejecutar el archivo `demo_clock_and_IP.py` ingresamos el siguiente comando en la terminal

```
python demo_clock_and_IP.py
```

![Screenshot from 2023-04-26 02-27-35](https://user-images.githubusercontent.com/81504385/234501572-0061ed3d-3174-4535-972a-030dcabf815d.png)

A continuacion en la pantalla LCD podra visualizar lo siguiente:

![demo_ip](https://user-images.githubusercontent.com/81504385/234501713-edd2a740-42e2-4e9c-91ea-4a8b8c181538.jpg)

`Nota:` Para mayores detalles y DEMOS, visitar el siguiente repositorio

```
https://github.com/the-raspberry-pi-guy/lcd
```

`Paso 9:` Componentes electronicos
