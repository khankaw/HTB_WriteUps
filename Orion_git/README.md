# Orion Write Up

**No distribur mientras la máquina esté activa**

**Créditos al creador de la máquina: Pho3o**

Orion es una máquina Linux que concatena las siguientes vulnerabilidades y configuraciones:

### Acceso inicial

1. CVE-2025-32432 -> Remote Code Execution dentro de un endpoint en CraftCMS
2. Archivo .env legible con contraseña en texto claro para MySQL con el usuario root
3. Hash de una contraseña débil dentro de MySQL

### Escalada de privilegios

1. CVE-2026-24061 -> Bypass de autenticación dentro del protocolo Telnet

## CVE-2025-32432

Es una vulneranilidad de Remote Code Execution dentro de Craft CMS que ocurre debido a que el endpoint admin/actions/assets/generatetransform está disponible para recibir 
POST requests sin necesidad ade autenticación. Dentro de la petición POST se puede incluir un payload en forma de JSON que será interpretado por Yii como la configuración
de un objeto, por lo tanto el código será ejecutado.

## CVE-2026-24061

Es una vulnerabilidad de Authentication Bypass dentro del protocolo Telnet. Ocurre debido a que no hay una sanitización del input de usuario a la hora de redefinir
el valor de la variable de entorno USER dentro del comando para negociar la conexión. En esta variable se puede colocar el valor de root y se iniciará la conexión
como root sin solicitd de contraseña.

## Referencias

https://sensepost.com/blog/2025/investigating-an-in-the-wild-campaign-using-rce-in-craftcms/#technical-analysis

https://www.offsec.com/blog/cve-2026-24061/






