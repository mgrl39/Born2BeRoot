### **Temas Clave Cubiertos**

1. **Propósito de las Máquinas Virtuales**
   - Proporcionan un entorno de ejecución independiente del hardware y del sistema operativo, facilitando la portabilidad de programas.

2. **Diferencias entre Apt y Aptitude**
   - `apt`: Administrador de paquetes de nivel inferior.
   - `aptitude`: Administrador de paquetes de alto nivel con más características.

3. **Qué es APPArmor**
   - Módulo de seguridad del kernel Linux que restringe las capacidades de un programa.

4. **Qué es LVM**
   - Gestor de volúmenes lógicos que permite un manejo más flexible del espacio en dispositivos de almacenamiento.

5. **Comprobaciones y Configuraciones Específicas**
   - **Interfaz Gráfica**: Verificar que no se está usando (`ls /usr/bin/*session`).
   - **Servicio UFW**: Comprobar estado (`sudo ufw status`).
   - **Servicio SSH**: Comprobar estado (`sudo service ssh status`).
   - **Sistema Operativo**: Verificar con `uname -v` o `uname --kernel-version`.
   - **Grupos de Usuario**: Comprobar membresía (`getent group sudo`, `getent group user42`).
   - **Creación de Usuario y Grupo**: Crear usuario y grupo, añadir usuario al grupo.
   - **Hostname**: Comprobar y modificar hostname.
   - **Particiones**: Verificar particiones (`lsblk`).
   - **Sudo**: Comprobar instalación (`dpkg -s sudo`), añadir usuario al grupo sudo.
   - **Reglas UFW**: Lista, añadir, y borrar reglas.
   - **Servicio SSH**: Verificar puerto y funcionamiento, y uso de SSH con el nuevo usuario.
   - **Crontab**: Modificar tiempo de ejecución y controlar el servicio cron.

6. **Configuraciones Avanzadas**
   - **Historial de Sudo**: Comprobar existencia y contenido del directorio `/var/log/sudo/`.
   - **Revisión Final**: Verificar configuración global y funcionalidad con un tester propio.

### **Comandos y Procedimientos Detallados**

- **Para comprobar el estado de servicios**:
  - `sudo ufw status`
  - `sudo service ssh status`
  - `dpkg -s sudo`

- **Para crear y gestionar usuarios y grupos**:
  - `sudo adduser name_user`
  - `sudo addgroup evaluating`
  - `sudo adduser name_user evaluating`
  - `sudo adduser name_user sudo`

- **Para modificar el hostname**:
  - Editar `/etc/hostname` y `/etc/hosts`
  - Reiniciar la máquina

- **Para gestionar reglas de UFW**:
  - `sudo ufw allow 8080`
  - `sudo ufw delete num_rule`
  - `sudo ufw status numbered`

- **Para modificar crontab**:
  - `sudo crontab -u root -e`

- **Para comprobar y ajustar el servicio SSH**:
  - `sudo service ssh status`
  - `ssh newuser@localhost -p 4242`
