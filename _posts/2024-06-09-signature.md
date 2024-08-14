---
title: ✍️ Signature
author: mgrl39
date: 2024-06-09
category: Jekyll
layout: post
---
Llega el punto de generar el Signature, el signature es .... para poder realizar eso utlizaremos el comando `sha1sum` (en Linux) y pondremos el nombre de nuestro .vdi.
Lo que haremos es, primeramente apagar la maquina virtual, dandole a la x.
<div style="text-align: center;">
    <img src="https://raw.githubusercontent.com/mgrl39/Born2BeRoot/main/steps/b2br_img_252.png" alt="Imagen 252"/>
</div>

Aqui nos salen diferentes opciones, vamos a apagarla del todo no guardar su estado ni nada.
![Imagen 253](https://raw.githubusercontent.com/mgrl39/Born2BeRoot/main/steps/b2br_img_253.png)


El siguiente paso será ubicarnos en la ruta donde tengamos el .vdi de nuestra máquina virtual.
Yo lo tenia en `~/sgoinfre/born2beroot/Born2BeRoot` entonces entro a la carpeta usando el comando `cd` y genero el signature con `sha1sum Born2BeRoot.vdi`.
Podemos pasar la signature a un archivo con `sha1sum Born2BeRoot.vdi > signature.txt`
Pero bueno, si para crear la carpeta en sgoinfre utilizaste el comando de creacion de carpeta y le pusiste a la maquina Born2BeRoot puedes utilizar el siguiente comando:
```bash
cd ~/sgoinfre/born2beroot/Born2BeRoot && pwd && sha1sum *.vdi > signature.txt && ls && cat signature.txt
```
![Imagen 254](https://raw.githubusercontent.com/mgrl39/Born2BeRoot/main/steps/b2br_img_254.png)
