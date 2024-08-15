---
title: 🌐 WordPress
author: mgrl39
date: 2024-06-07
category: Jekyll
layout: post
---

### Instalación y Configuración de WordPress en Lighttpd

#### 1. Instalación de Lighttpd

Primero, instala Lighttpd, un servidor web ligero y eficiente:

```bash
sudo apt install lighttpd -y
```

- **Explicación**:
  - **`sudo`**: Ejecuta el comando con permisos de superusuario.
  - **`apt install`**: Instala el paquete.
  - **`lighttpd`**: El nombre del servidor web que se instalará.
  - **`-y`**: Responde automáticamente "sí" a las preguntas durante la instalación.

![Imagen 197](https://raw.githubusercontent.com/mgrl39/Born2BeRoot/main/steps/b2br_img_197.png)

#### 2. Configuración del Cortafuegos

Permite el tráfico HTTP en el puerto 80:

```bash
sudo ufw allow 80 && sudo ufw status
```

- **Explicación**:
  - **`ufw`**: Herramienta para configurar el cortafuegos.
  - **`allow 80`**: Permite el tráfico en el puerto 80.
  - **`&&`**: Ejecuta el siguiente comando solo si el anterior tiene éxito.
  - **`ufw status`**: Muestra el estado actual del cortafuegos.

![Imagen 198](https://raw.githubusercontent.com/mgrl39/Born2BeRoot/main/steps/b2br_img_198.png)

#### 3. Instalación de Herramientas Adicionales

Instala `wget` y `zip` para descargar y descomprimir archivos:

```bash
sudo apt install wget zip -y
```

- **Explicación**:
  - **`wget`**: Herramienta para descargar archivos desde la web.
  - **`zip`**: Herramienta para manejar archivos ZIP.

![Imagen 200](https://raw.githubusercontent.com/mgrl39/Born2BeRoot/main/steps/b2br_img_200.png)

#### 4. Descarga y Descompresión de WordPress

Descarga WordPress en español y descomprímelo:

```bash
cd /var/www && sudo wget https://es.wordpress.org/latest-es_ES.zip
sudo unzip latest-es_ES.zip
```

- **Explicación**:
  - **`cd /var/www`**: Cambia al directorio donde se almacenan los archivos web.
  - **`wget`**: Descarga el archivo ZIP de WordPress.
  - **`unzip`**: Descomprime el archivo ZIP.

![Imagen 202](https://raw.githubusercontent.com/mgrl39/Born2BeRoot/main/steps/b2br_img_202.png)
![Imagen 203](https://raw.githubusercontent.com/mgrl39/Born2BeRoot/main/steps/b2br_img_203.png)

#### 5. Configuración de Directorios y Permisos

Renombra el directorio antiguo de `html`, mueve WordPress y ajusta permisos:

```bash
sudo mv html/ html_old && sudo mv wordpress/ html
sudo chmod -R 755 html
```

- **Explicación**:
  - **`mv html/ html_old`**: Renombra el directorio `html` para hacer una copia de seguridad.
  - **`mv wordpress/ html`**: Mueve los archivos de WordPress al directorio `html`.
  - **`chmod -R 755 html`**: Ajusta los permisos para asegurar que los archivos sean accesibles.

![Imagen 205](https://raw.githubusercontent.com/mgrl39/Born2BeRoot/main/steps/b2br_img_205.png)

#### 6. Instalación y Configuración de MariaDB

Instala MariaDB y asegura la instalación:

```bash
sudo apt install mariadb-server -y
sudo mysql_secure_installation
```

Durante la configuración, responde lo siguiente:

```
Switch to unix_socket authentication [Y/n] N
Change the root password? [Y/n] N
Remove anonymous users? [Y/n] Y
Disallow root login remotely? [Y/n] Y
Remove test database and access to it? [Y/n] Y
Reload privilege tables now? [Y/n] Y
```

- **Explicación**:
  - **`mariadb-server`**: Instala MariaDB, un sistema de gestión de bases de datos.
  - **`mysql_secure_installation`**: Ejecuta un script para asegurar la instalación de MariaDB.

![Imagen 208](https://raw.githubusercontent.com/mgrl39/Born2BeRoot/main/steps/b2br_img_208.png)
![Imagen 210](https://raw.githubusercontent.com/mgrl39/Born2BeRoot/main/steps/b2br_img_210.png)
![Imagen 211](https://raw.githubusercontent.com/mgrl39/Born2BeRoot/main/steps/b2br_img_211.png)

#### 7. Creación de la Base de Datos para WordPress

Accede a MariaDB y configura la base de datos:

```bash
mariadb
```

```sql
CREATE DATABASE wp_database;
SHOW DATABASES;
CREATE USER 'meghribe'@'localhost' IDENTIFIED BY '12345';
GRANT ALL PRIVILEGES ON wp_database.* TO 'meghribe'@'localhost';
FLUSH PRIVILEGES;
exit
```

- **Explicación**:
  - **`CREATE DATABASE wp_database;`**: Crea una nueva base de datos para WordPress.
  - **`CREATE USER 'meghribe'@'localhost' IDENTIFIED BY '12345';`**: Crea un nuevo usuario con privilegios para la base de datos.
  - **`GRANT ALL PRIVILEGES`**: Otorga todos los privilegios sobre la base de datos al nuevo usuario.

![Imagen 216](https://raw.githubusercontent.com/mgrl39/Born2BeRoot/main/steps/b2br_img_216.png)

#### 8. Instalación de PHP

Instala PHP y los módulos necesarios:

```bash
sudo apt install php-cgi php-mysql -y
```

- **Explicación**:
  - **`php-cgi`**: Permite a Lighttpd procesar scripts PHP.
  - **`php-mysql`**: Permite a PHP interactuar con MariaDB.

![Imagen 218](https://raw.githubusercontent.com/mgrl39/Born2BeRoot/main/steps/b2br_img_218.png)

#### 9. Configuración Final de Lighttpd para PHP

Habilita FastCGI y recarga Lighttpd:

```bash
sudo lighty-enable-mod fastcgi
sudo lighty-enable-mod fastcgi-php
sudo service lighttpd force-reload
```

- **Explicación**:
  - **`lighty-enable-mod fastcgi` y `fastcgi-php`**: Habilitan el soporte para FastCGI, necesario para PHP.
  - **`service lighttpd force-reload`**: Recarga la configuración de Lighttpd.

![Imagen 225](https://raw.githubusercontent.com/mgrl39/Born2BeRoot/main/steps/b2br_img_225.png)

#### 10. Verificación de la Dirección IP

Obtén la dirección IP del servidor:

```bash
ip -c a
```

- **Explicación**:
  - **`ip -c a`**: Muestra la configuración de red y la dirección IP del servidor.

![Imagen 226](https://raw.githubusercontent.com/mgrl39/Born2BeRoot/main/steps/b2br_img_226.png)

#### 11. Finalización de la Instalación de WordPress

1. **Accede a WordPress**: Abre un navegador y navega a `http://IP`, donde `IP` es la dirección IP de tu servidor.
2. **Configuración de WordPress**: Sigue el asistente de configuración de WordPress para crear un usuario administrador y configurar el sitio.

![Imagen 227](https://raw.githubusercontent.com/mgrl39/Born2BeRoot/main/steps/b2br_img_227.png)
![Imagen 230](https://raw.githubusercontent.com/mgrl39/Born2BeRoot/main/steps/b2br_img_230.png)
![Imagen 232](https://raw.githubusercontent.com/mgrl39/Born2BeRoot/main/steps/b2br_img_232.png)
![Imagen 233](https://raw.githubusercontent.com/mgrl39/Born2BeRoot/main/steps/b2br_img_233.png)

- **Finalización**: Una vez completada la configuración, podrás iniciar sesión en tu nuevo sitio de WordPress con las credenciales que creaste durante el proceso de configuración.

```bash
http://IP/wp-admin/
```

![Imagen 2352](https://raw.githubusercontent.com/mgrl39/Born2BeRoot/main/steps/b2br_img_2352.png)
![Imagen 236](https://raw.githubusercontent.com/mgrl39/Born2BeRoot/main/steps/b2br_img_236.png)
