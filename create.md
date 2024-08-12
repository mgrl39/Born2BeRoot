**Descargar la ISO de Debian y Preparar el Entorno**

Primero, necesitamos descargar la ISO oficial de Debian desde su página web. Para mantener organizada nuestra máquina virtual y no llenar el espacio en el directorio `home` (que solo tiene 5GB disponibles), crearemos una carpeta en `~/sgoinfre` llamada `born2beroot`. Aquí se almacenará la ISO y se creará la carpeta de nuestra máquina virtual.

Ejecuta el siguiente comando para crear la carpeta y descargar la ISO:

```shell
cd ~/sgoinfre && mkdir -p born2beroot && cd born2beroot && wget https://cdimage.debian.org/debian-cd/current/amd64/iso-cd/debian-12.6.0-amd64-netinst.iso
```
![Imagen 001](steps/b2br_img_001.png)
![Imagen 002](steps/b2br_img_002.png)
![Imagen 003](steps/b2br_img_003.png)
![Imagen 004](steps/b2br_img_004.png)
![Imagen 005](steps/b2br_img_005.png)
![Imagen 006](steps/b2br_img_006.png)
![Imagen 007](steps/b2br_img_007.png)
