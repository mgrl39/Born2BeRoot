---
title: ✍️ Signature
author: mgrl39
date: 2024-06-09
category: Jekyll
layout: post
---

### 1. **Apagar la Máquina Virtual**

Antes de generar la signature, asegúrate de que la máquina virtual esté completamente apagada. Haz clic en el botón ❌ para cerrar la máquina virtual.

<div style="text-align: center;">
    <img src="https://raw.githubusercontent.com/mgrl39/Born2BeRoot/main/steps/b2br_img_252.png" alt="Imagen 252"/>
</div>

- **Opciones**: Asegúrate de seleccionar la opción para apagar la máquina virtual por completo, sin guardar su estado.

![Imagen 253](https://raw.githubusercontent.com/mgrl39/Born2BeRoot/main/steps/b2br_img_253.png)

---

### 2. **Ubicarse en la Ruta del Archivo `.vdi`**

Navega hasta el directorio que contiene tu archivo `.vdi`. En este caso, se encuentra en `~/sgoinfre/born2beroot/Born2BeRoot`. Utiliza el siguiente comando para cambiar al directorio adecuado:

```bash
cd ~/sgoinfre/born2beroot/Born2BeRoot
```

---

### 3. **Generar la Signature**

Una vez que estés en el directorio correcto, usa `sha1sum` para generar la firma del archivo `.vdi`. Reemplaza `Born2BeRoot.vdi` con el nombre de tu archivo `.vdi` si es diferente.

```bash
sha1sum Born2BeRoot.vdi
```

Para guardar la signature en un archivo de texto, puedes usar:

```bash
sha1sum Born2BeRoot.vdi > signature.txt
```
Entra y solo deja el numero, sera algo asi: `e3325e26ebf96d3a5d1f009328d6bf6b85b0238a`

---

### 4. **Comando Completo**

Si creaste la carpeta en `~/sgoinfre` usando un comando y le diste el nombre `Born2BeRoot`, puedes ejecutar el siguiente comando para realizar todo el proceso de una vez:

```bash
cd ~/sgoinfre/born2beroot/Born2BeRoot && pwd && sha1sum *.vdi | awk '{print $1}' > signature.txt && ls && cat signature.txt
```

**Explicación**:
- Cambia al directorio que contiene el archivo `.vdi`.
- Muestra la ruta actual (`pwd`).
- Genera la signature y la guarda en `signature.txt`.
- Lista los archivos en el directorio (`ls`).
- Muestra el contenido del archivo `signature.txt` (`cat signature.txt`).
- `sha1sum *.vdi` genera el hash y el nombre del archivo.
- `| awk '{print $1}'` toma la salida de `sha1sum` y solo selecciona la primera columna, que es el hash.
- `> signature.txt` redirige esa salida (solo el hash) al archivo `signature.txt`.

![Imagen 254](https://raw.githubusercontent.com/mgrl39/Born2BeRoot/main/steps/b2br_img_254.png)
