---
title: Servicio Adicional - LiteSpeed
author: mgrl39
date: 2024-06-08
category: Jekyll
layout: post
---

```bash
sudo su
```
![Imagen 238](https://raw.githubusercontent.com/mgrl39/Born2BeRoot/main/steps/b2br_img_238.png)
```bash
sudo apt install curl -y
```
![Imagen 237](https://raw.githubusercontent.com/mgrl39/Born2BeRoot/main/steps/b2br_img_237.png)
```bash
wget -O - https://repo.litespeed.sh | sudo bash
```
![Imagen 240](https://raw.githubusercontent.com/mgrl39/Born2BeRoot/main/steps/b2br_img_240.png)
```bash
sudo apt update
```
![Imagen 242](https://raw.githubusercontent.com/mgrl39/Born2BeRoot/main/steps/b2br_img_242.png)
```bash
sudo apt install openlitespeed -y
```
![Imagen 244](https://raw.githubusercontent.com/mgrl39/Born2BeRoot/main/steps/b2br_img_244.png)
```bash
sudo /usr/local/lsws/admin/misc/admpass.sh
```
Le puse de user `meghribe` y password `42Password-`. _Os recomiendo poner vuestro user_.
![Imagen 245](https://raw.githubusercontent.com/mgrl39/Born2BeRoot/main/steps/b2br_img_245.png)
```bash
sudo ufw allow 8088/tcp
sudo ufw allow 7080/tcp
``` 
![Imagen 246](https://raw.githubusercontent.com/mgrl39/Born2BeRoot/main/steps/b2br_img_246.png)
Abrimos el navegador y escribimos nuestra IP, si no recordamos cual era la direccion IP podemos utilizar `ip -c a` en la maquina virtual para ver la direccion (saldra en morado/lila/rosa).
![Imagen 247](https://raw.githubusercontent.com/mgrl39/Born2BeRoot/main/steps/b2br_img_247.png)
Es posible que aparezca este Warning, para poder entrar a la paginna tendremos que aceptar este certificado, es decir, darle a advanced y **Accept the Risk and Continue**. 
![Imagen 248](https://raw.githubusercontent.com/mgrl39/Born2BeRoot/main/steps/b2br_img_248.png)
Finalmente, ya estamos en el login. Ponemos nuestras credencicales.
![Imagen 249](https://raw.githubusercontent.com/mgrl39/Born2BeRoot/main/steps/b2br_img_249.png)
Los mios eran: `meghribe` y `42Password-`, seguidamente le damos al boton de Login.
![Imagen 250](https://raw.githubusercontent.com/mgrl39/Born2BeRoot/main/steps/b2br_img_250.png)
Si los credenciales eran correctos, entramos a este panel, enhorabuena, ya tienes el proyecto acabado!
Ahora capaz te queda estudiarte las cosas :)
![Imagen 251](https://raw.githubusercontent.com/mgrl39/Born2BeRoot/main/steps/b2br_img_251.png)
