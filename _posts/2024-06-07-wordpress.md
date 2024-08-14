---
title: 🌐 WordPress
author: mgrl39
date: 2024-06-07
category: Jekyll
layout: post
---
```bash
sudo apt install lighttpd -y
```
   - **Explicación**: 
     - `sudo apt install lighttpd -y` es el comando que instala Lighttpd, un servidor web ligero y eficiente.
     - **`sudo`**: Otorga permisos de superusuario necesarios para la instalación.
     - **`apt install`**: Inicia la instalación del paquete especificado.
     - **`lighttpd`**: Es el nombre del paquete del servidor web que estamos instalando.
     - **`-y`**: Responde automáticamente "sí" a cualquier pregunta que aparezca durante la instalación, agilizando el proceso.
     - **¿Por qué Lighttpd?**: Es ideal para servidores con recursos limitados y es suficientemente potente para manejar aplicaciones web como WordPress.

![Imagen 197](https://raw.githubusercontent.com/mgrl39/Born2BeRoot/main/steps/b2br_img_197.png)


```bash
sudo ufw allow 80 && sudo ufw status
```

   - **Explicación**:
     - **`ufw`**: Es una herramienta que facilita la configuración del cortafuegos (firewall).
     - **`allow 80`**: Permite el tráfico en el puerto 80, que es el puerto utilizado por HTTP, permitiendo que los usuarios accedan a tu servidor web.
     - **`&&`**: Permite ejecutar el siguiente comando solo si el anterior tuvo éxito.
     - **`ufw status`**: Verifica el estado actual del cortafuegos y muestra qué reglas están activas.
     - **¿Por qué este paso?**: Para asegurarse de que el servidor web pueda recibir y responder a solicitudes HTTP desde la red.

![Imagen 198](https://raw.githubusercontent.com/mgrl39/Born2BeRoot/main/steps/b2br_img_198.png)

```bash
sudo apt install wget zip -y
```

   - **Explicación**:
     - **`wget`**: Es una herramienta de línea de comandos utilizada para descargar archivos desde la web.
     - **`zip`**: Es una utilidad para comprimir y descomprimir archivos en formato ZIP.
     - **¿Por qué instalar estas herramientas?**: `wget` se utilizará para descargar WordPress, y `zip` se usará para descomprimir el archivo descargado.

![Imagen 200](https://raw.githubusercontent.com/mgrl39/Born2BeRoot/main/steps/b2br_img_200.png)

```bash
cd /var/www && sudo wget https://es.wordpress.org/latest-es_ES.zip
```

   - **Explicación**:
     - **`cd /var/www`**: Cambia el directorio actual a `/var/www`, que es el directorio estándar donde se almacenan los archivos web en servidores Linux.
     - **`sudo wget https://es.wordpress.org/latest-es_ES.zip`**: Descarga la última versión de WordPress en español desde el sitio oficial.
     - **¿Por qué descargar WordPress?**: Este es el sistema de gestión de contenido (CMS) que se configurará para servir como plataforma web.

![Imagen 202](https://raw.githubusercontent.com/mgrl39/Born2BeRoot/main/steps/b2br_img_202.png)

```bash
sudo unzip latest-es_ES.zip
```

   - **Explicación**:
     - **`unzip`**: Descomprime el archivo ZIP descargado.
     - **`latest-es_ES.zip`**: Es el archivo comprimido de WordPress que contiene todos los archivos necesarios para su instalación.
     - **¿Por qué descomprimirlo?**: Necesitamos los archivos de WordPress disponibles en su forma no comprimida para poder configurarlo y ejecutarlo.

![Imagen 203](https://raw.githubusercontent.com/mgrl39/Born2BeRoot/main/steps/b2br_img_203.png)
![Imagen 204](https://raw.githubusercontent.com/mgrl39/Born2BeRoot/main/steps/b2br_img_204.png)

```bash
sudo mv html/ html_old && sudo mv wordpress/ html && sudo chmod -R 755 html && ls
```

   - **Explicación**:
     - **`mv html/ html_old`**: Renombra el directorio `html` existente (que es el directorio web por defecto) a `html_old` para hacer un respaldo.
     - **`mv wordpress/ html`**: Mueve los archivos de WordPress al directorio `html` para que el servidor web los sirva.
     - **`chmod -R 755 html`**: Cambia los permisos de los archivos en el directorio `html` para que todos los usuarios puedan leer y ejecutar archivos, pero solo el propietario puede escribir.
     - **`ls`**: Lista los archivos y directorios en la ubicación actual, verificando que el cambio se realizó correctamente.
     - **¿Por qué este paso?**: Esto asegura que WordPress esté en la ubicación correcta con los permisos adecuados para funcionar correctamente en el servidor web.
     
![Imagen 205](https://raw.githubusercontent.com/mgrl39/Born2BeRoot/main/steps/b2br_img_205.png)

```bash
sudo apt install mariadb-server -y
```

   - **Explicación**:
     - **`mariadb-server`**: Instala MariaDB, un sistema de gestión de bases de datos derivado de MySQL.
     - **¿Por qué instalar MariaDB?**: WordPress necesita una base de datos para almacenar su contenido y configuraciones. MariaDB es una opción popular y compatible.

![Imagen 208](https://raw.githubusercontent.com/mgrl39/Born2BeRoot/main/steps/b2br_img_208.png)
```bash
sudo mysql_secure_installation
```
```
Switch to unix_socket authentication [Y/n] N
Change the root password? [Y/n] N
Remove anonymous users? [Y/n] Y
Disallow root login remotely? [Y/n] Y
Remove test database and acces to it? [Y/n] Y
Reload privilege tables now? [Y/n] Y
```

   - **Explicación**:
     - Este comando inicia un script interactivo para asegurar la instalación de MariaDB.
     - **`Switch to unix_socket authentication [Y/n] N`**: Responde "N" para no cambiar el método de autenticación.
     - **`Change the root password? [Y/n] N`**: Responde "N" si ya tienes una contraseña segura para el usuario root.
     - **`Remove anonymous users? [Y/n] Y`**: Responde "Y" para eliminar usuarios anónimos, mejorando la seguridad.
     - **`Disallow root login remotely? [Y/n] Y`**: Responde "Y" para evitar que el usuario root se conecte de forma remota.
     - **`Remove test database and access to it? [Y/n] Y`**: Responde "Y" para eliminar la base de datos de prueba, un posible riesgo de seguridad.
     - **`Reload privilege tables now? [Y/n] Y`**: Responde "Y" para aplicar todos los cambios de inmediato.
     - **¿Por qué es importante?**: Esto asegura que la instalación de MariaDB esté protegida contra configuraciones inseguras.
     
![Imagen 210](https://raw.githubusercontent.com/mgrl39/Born2BeRoot/main/steps/b2br_img_210.png)
![Imagen 211](https://raw.githubusercontent.com/mgrl39/Born2BeRoot/main/steps/b2br_img_211.png)
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
     - **`CREATE DATABASE wp_database;`**: Crea una nueva base de datos llamada `wp_database` para WordPress.
     - **`SHOW DATABASES;`**: Muestra todas las bases de datos disponibles para verificar que `wp_database` se ha creado correctamente.
     - **`CREATE USER 'meghribe'@'localhost' IDENTIFIED BY '12345';`**: Crea un nuevo usuario de la base de datos llamado `meghribe` con la contraseña `12345`.
     - **`GRANT ALL PRIVILEGES ON wp_database.* TO 'meghribe'@'localhost';`**: Otorga todos los privilegios sobre la base de datos `wp_database` al usuario `meghribe`.
     - **`FLUSH PRIVILEGES;`**: Recarga los privilegios para que los cambios tengan efecto inmediatamente.
     - **¿Por qué esto es crucial?**: Necesitamos una base de datos y un usuario dedicados para que WordPress pueda almacenar y gestionar su contenido de manera segura.
     
![Imagen 216](https://raw.githubusercontent.com/mgrl39/Born2BeRoot/main/steps/b2br_img_216.png)

```bash
sudo apt install php-cgi php-mysql -y
```

   - **Explicación**:
     - **`php-cgi`**: PHP es el lenguaje de programación que WordPress usa para funcionar, y `php-cgi` permite a Lighttpd procesar scripts PHP.
     - **`php-mysql`**: Este paquete permite a PHP interactuar con la base de datos MariaDB.
     - **¿Por qué estos paquetes?**: Son esenciales para que WordPress pueda procesar su lógica y comunicarse con la base de datos.

![Imagen 218](https://raw.githubusercontent.com/mgrl39/Born2BeRoot/main/steps/b2br_img_218.png)
```bash
cd /var/www/html && ls
```

   - **Explicación**:
     - **`cd /var/www/html`**: Cambia al directorio donde ahora están los archivos de WordPress.
     - **`ls`**: Lista los archivos en el directorio, confirmando que todo está en su lugar.


![Imagen 219](https://raw.githubusercontent.com/mgrl39/Born2BeRoot/main/steps/b2br_img_219.png)
```bash
cp wp-config-sample.php wp-config.php
```

   - **Explicación**:
     - **`cp wp-config-sample.php wp-config.php`**: Copia el archivo de configuración de ejemplo de WordPress, `wp-config-sample.php`, a `wp-config.php`, que es el archivo real que WordPress usará.
     - **¿Por qué copiar este archivo?**: `wp-config.php` es donde se configuran las conexiones a la base de datos y otras configuraciones esenciales para que WordPress funcione.


![Imagen 220](https://raw.githubusercontent.com/mgrl39/Born2BeRoot/main/steps/b2br_img_220.png)
```bash
vim wp-config.php
```

   - **Explicación**:
     - **`vim wp-config.php`**: Abre el archivo de configuración `wp-config.php` en el editor de texto Vim para editarlo.
     - **¿Qué cambiar?**: Aquí se configurarán los detalles de la base de datos, como el nombre de la base de datos (`wp_database`), el usuario (`meghribe`), y la contraseña (`12345`).


![Imagen 221](https://raw.githubusercontent.com/mgrl39/Born2BeRoot/main/steps/b2br_img_221.png)

![Imagen 222](https://raw.githubusercontent.com/mgrl39/Born2BeRoot/main/steps/b2br_img_222.png)
![Imagen 223](https://raw.githubusercontent.com/mgrl39/Born2BeRoot/main/steps/b2br_img_223.png)
```bash
sudo lighty-enable-mod fastcgi
sudo lighty-enable-mod fastcgi-php
service lighttpd force-reload
```
   - **Explicación**:
     - **`lighty-enable-mod fastcgi` y `fastcgi-php`**: Estos comandos habilitan el soporte para FastCGI en Lighttpd, lo cual es necesario para ejecutar scripts PHP.
     - **`service lighttpd force-reload`**: Recarga la configuración de Lighttpd para aplicar los cambios.
     - **¿Por qué habilitar FastCGI?**: Es necesario para que el servidor web pueda procesar y ejecutar los scripts PHP que componen WordPress.


![Imagen 225](https://raw.githubusercontent.com/mgrl39/Born2BeRoot/main/steps/b2br_img_225.png)
```bash
ip -c a
```
   - **Explicación**:
     - **`ip -c a`**: Muestra la configuración de red actual, incluyendo la dirección IP del servidor.
     - **¿Por qué esto es importante?**: Necesitas la dirección IP para acceder a tu instalación de WordPress desde un navegador.

![Imagen 226](https://raw.githubusercontent.com/mgrl39/Born2BeRoot/main/steps/b2br_img_226.png)

**Acceder a WordPress y Finalizar la Configuración**
   - **Acceder**: Abre un navegador y escribe la dirección IP de tu servidor para acceder a la pantalla de configuración de WordPress.
   - **Login WordPress**: Sigue los pasos para completar la configuración de WordPress (crea un usuario administrador, configura el título del sitio, etc.).
![Imagen 227](https://raw.githubusercontent.com/mgrl39/Born2BeRoot/main/steps/b2br_img_227.png)
![Imagen 230](https://raw.githubusercontent.com/mgrl39/Born2BeRoot/main/steps/b2br_img_230.png)
![Imagen 232](https://raw.githubusercontent.com/mgrl39/Born2BeRoot/main/steps/b2br_img_232.png)
  
![Imagen 233](https://raw.githubusercontent.com/mgrl39/Born2BeRoot/main/steps/b2br_img_233.png)

- **Finalización**: Una vez completada la configuración inicial, podrás iniciar sesión en tu nuevo sitio de WordPress utilizando el nombre de usuario y la contraseña que creaste durante la configuración.

```bash
http://IP/wp-admin/
```
![Imagen 2352](https://raw.githubusercontent.com/mgrl39/Born2BeRoot/main/steps/b2br_img_2352.png)

![Imagen 236](https://raw.githubusercontent.com/mgrl39/Born2BeRoot/main/steps/b2br_img_236.png)
