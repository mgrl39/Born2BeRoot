---
title: 🚀 Servicio Adicional - LiteSpeed
author: mgrl39
date: 2024-06-08
category: Jekyll
layout: post
---

### 1. **Cambiar a Usuario Root**
```bash
sudo su
```
- **Explicación**: `sudo su` te eleva a un usuario root, permitiéndote ejecutar comandos con privilegios completos.
![Imagen 238](https://raw.githubusercontent.com/mgrl39/Born2BeRoot/main/steps/b2br_img_238.png)

### 2. **Instalar `curl`**
```bash
sudo apt install curl -y
```
- **Explicación**: `curl` es necesario para descargar y ejecutar el script de instalación de LiteSpeed.
![Imagen 237](https://raw.githubusercontent.com/mgrl39/Born2BeRoot/main/steps/b2br_img_237.png)

### 3. **Descargar e Instalar el Repositorio de LiteSpeed**
```bash
wget -O - https://repo.litespeed.sh | sudo bash
```
- **Explicación**: Este comando agrega el repositorio oficial de LiteSpeed a tu lista de fuentes de software.
![Imagen 240](https://raw.githubusercontent.com/mgrl39/Born2BeRoot/main/steps/b2br_img_240.png)

### 4. **Actualizar el Sistema para Incluir el Nuevo Repositorio**
```bash
sudo apt update
```
- **Explicación**: `apt update` asegura que el sistema tenga acceso a las últimas versiones de los paquetes.
![Imagen 242](https://raw.githubusercontent.com/mgrl39/Born2BeRoot/main/steps/b2br_img_242.png)

### 5. **Instalar OpenLiteSpeed**
```bash
sudo apt install openlitespeed -y
```
- **Explicación**: OpenLiteSpeed es un servidor web altamente optimizado para aplicaciones PHP como WordPress.
![Imagen 244](https://raw.githubusercontent.com/mgrl39/Born2BeRoot/main/steps/b2br_img_244.png)

### 6. **Configurar la Contraseña de Administración de OpenLiteSpeed**
```bash
sudo /usr/local/lsws/admin/misc/admpass.sh
```
Le puse de user `meghribe` y password `42Password-`. _Os recomiendo utilizar vuestro user_.
- **Explicación**: Este script te permite establecer el nombre de usuario y la contraseña para el panel de administración de OpenLiteSpeed.
![Imagen 245](https://raw.githubusercontent.com/mgrl39/Born2BeRoot/main/steps/b2br_img_245.png)

### 7. **Configurar el Firewall para Permitir Acceso a los Puertos Necesarios**
```bash
sudo ufw allow 8088/tcp
sudo ufw allow 7080/tcp
``` 
- **Explicación**: Estos comandos permiten el tráfico TCP en los puertos 8088 y 7080, necesarios para acceder a OpenLiteSpeed y su panel de administración.
![Imagen 246](https://raw.githubusercontent.com/mgrl39/Born2BeRoot/main/steps/b2br_img_246.png)

### 8. **Acceder al Servidor Web desde un Navegador**
- **Explicación**: Escribe la dirección IP de tu servidor en el navegador. Si no recuerdas la IP, usa `ip -c a` para obtenerla.
- **Explicación**: Verás la dirección IP en color morado/rosa. Usa esta IP para acceder a OpenLiteSpeed.
![Imagen 247](https://raw.githubusercontent.com/mgrl39/Born2BeRoot/main/steps/b2br_img_247.png)

### 9. **Aceptar el Certificado SSL Autogenerado**
- **Explicación**: Es posible que aparezca un warning en el navegador debido a un certificado SSL autogenerado.
- **Solución**: Haz clic en "Advanced" y luego en "Accept the Risk and Continue" para acceder al panel.
![Imagen 248](https://raw.githubusercontent.com/mgrl39/Born2BeRoot/main/steps/b2br_img_248.png)

### 10. **Acceder al Panel de Administración de OpenLiteSpeed**
- **Explicación**: Ingresa las credenciales que configuraste anteriormente (`meghribe` y `42Password-` en este caso).
![Imagen 249](https://raw.githubusercontent.com/mgrl39/Born2BeRoot/main/steps/b2br_img_249.png)
- **Acceso al Panel**: Si los credenciales son correctos, entrarás al panel de administración de OpenLiteSpeed.
![Imagen 250](https://raw.githubusercontent.com/mgrl39/Born2BeRoot/main/steps/b2br_img_250.png)

### 11. **Explorar el Panel de Administración**
- **Explicación**: Una vez dentro, explora unn poco lass opciones para configurar el servidor LiteSpeed.
![Imagen 251](https://raw.githubusercontent.com/mgrl39/Born2BeRoot/main/steps/b2br_img_251.png)

### 12. **Estudio y Verificación Final**
- **Explicación**: Revisa los conceptos para asegurarte de que entiendes cómo funciona todo y cómo administrarlo correctamente.
