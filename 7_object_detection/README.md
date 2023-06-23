<a name="readme-top"></a>

<div align="center">

  <img src="../rp4logo.png" alt="logo" width="140"  height="auto" />
  <br/>

  <h3><b>7_Object_Detection</b></h3>

</div>

`PASO 1:` Abrir la terminal del Raspberry Pi

![image](https://github.com/storres20/tutorial-rp4/assets/81504385/88b35f77-de6d-4fe6-b21e-ca47af352053)

`PASO 2:` Clonar repositorio de `Edje Electronics`

![image](https://github.com/storres20/tutorial-rp4/assets/81504385/1d8d67e7-1b1a-4bed-a2c7-82282e4ef561)

En la terminal, introducir el siguiente comando y presionamos la `tecla ENTER`:

```
git clone https://github.com/EdjeElectronics/TensorFlow-Lite-Object-Detection-on-Android-and-Raspberry-Pi.git
```

![image](https://github.com/storres20/tutorial-rp4/assets/81504385/0ab602b2-9ba9-4c40-9e9f-30d5ed2ad95b)

`PASO 3:` Mover la carpeta clonada hacia la carpeta `tflite`

En la terminal, introducir el siguiente comando y presionamos la `tecla ENTER`:

```
mv TensorFlow-Lite-Object-Detection-on-Android-and-Raspberry-Pi/ tflite
```

![image](https://github.com/storres20/tutorial-rp4/assets/81504385/e3d43464-27c8-4634-a95d-6d0073aa1340)

`PASO 4:` Ingresar a la carpeta `tflite` e ingresar el siguiente comando

```
cd tflite
sudo pip3 install virtualenv
```

![image](https://github.com/storres20/tutorial-rp4/assets/81504385/e4848287-084e-4066-b2ae-1f672aa39d45)

 El comando `sudo pip3 install virtualenv` permite crear entornos virtuales con python

`PASO 5:` Crear el entorno virtual `tflite-env`

```
python3 -m venv tflite-env
```

![image](https://github.com/storres20/tutorial-rp4/assets/81504385/977cc2d0-284b-4386-9c9b-d50e38b39630)

`PASO 6:` Ingresamos al entorno virtual `tflite-env`

Para ello se ejecuta el siguiente commando:

```
source tflite-env/bin/activate
```

![image](https://github.com/storres20/tutorial-rp4/assets/81504385/0df61007-b0ed-4c74-ac89-eaa552a149e3)

`PASO 7:` Instalamos TensorFlow Lite y Open CV

Para ello se ejecuta el siguiente commando:

```
bash get_pi_requirements.sh
```

![image](https://github.com/storres20/tutorial-rp4/assets/81504385/eca69e8f-7582-4310-a1cc-bfd9f92d2ada)

![image](https://github.com/storres20/tutorial-rp4/assets/81504385/47e2e488-5969-4761-a444-ca5853a5ef70)

![image](https://github.com/storres20/tutorial-rp4/assets/81504385/6c4e303a-7469-4c4e-8d8d-8121057c8e29)

`PASO 8:` Descargamos el Modelo Entrenado para deteccion de objetos

Para ello usamos el siguiente link:

```
storage.googleapis.com/download.tensorflow.org/models/tflite/coco_ssd_mobilenet_v1_1.0_quant_2018_06_29.zip
```

Dicho link, descargará el archivo `coco_ssd_mobilenet_v1_1.0_quant_2018_06_29.zip`, el cual contiene el Modelo Entrenado y las etiquetas de los objetos a identificar

`PASO 9:` Descomprimir el archivo descargado `coco_ssd_mobilenet_v1_1.0_quant_2018_06_29.zip`

Los archivos descomprimidos son:

1) detect.tflite
2) labelmap.txt

Estos archivos deberan ser movidos hacia la carpeta `tflite/sample`

![image](https://github.com/storres20/tutorial-rp4/assets/81504385/ac03c9bd-8ced-4055-bc98-9d6cf9b68441)

`PASO 10:` Crear la carpeta `critters` dentro de la carpeta `tflite`

![image](https://github.com/storres20/tutorial-rp4/assets/81504385/a7be4b75-df4e-4fda-bebb-747799c6ff92)


