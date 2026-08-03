# MetaTwo Write Up

**No distribuir mientras la máquina esté activa**

**Créditos al creador de la máquina: Nauten**

MetaTwo es una máquina Linux que concatena las siguientes vulnerabilidades:

## Acceso Inicial

1. CVE-2022-0739 -> SQL Injection no autenticada en el endpoint expuesto /wp-admin/admin-ajax.php 
2. Fuerza bruta sobre una contraseña débil 
3. CVE-2021-29447 -> Blind XML External Entity para lectura de archivos de configuración

## Movimiento Lateral

1. Lectura permitida de scripts con información sensible 

## Escalada de Privilegios

1. Lectura permitida de archivos con claves privadas
2. Fuerza bruta sobre una contraseña débil

##  CVE-2022-0739

Es una vulnerabilidad dentro del plugin bookingpress instalado en WordPress que expone el endoint /wp-admin/admin-ajax.php a una inyección SQL con clausulas UNION. 
A través de la inyección se pueden enumerar bases de datos que contengan información sobre los usuarios en WordPress y sus contraseñas.

## CVE-2021-29447

Es una vulnerabilidad que debe cumplir la siguiente condición: WordPress debe estar instalado con PHP. Esto abre la puerta a un Blind XXE
Se sube un archivo .wav con un payload que solicita el documento .dtd al servidor del atacante. Dentro del documento .dtd se específica una lógica para solicitar
la lectura de archivos con información sensible, como por ejemplo /etc/passwd o /wp-config.php. Una vez subido el archivo a la página, se recibe en el servidor del atacante 
el archivo solicitado codificado en base64.

## Referencias

https://wpscan.com/vulnerability/388cd42d-b61a-42a4-8604-99b812db2357/  
https://wpscan.com/vulnerability/cbbe6c17-b24e-4be4-8937-c78472a138b5/  
https://blog.wpsec.com/wordpress-xxe-in-media-library-cve-2021-29447/  


