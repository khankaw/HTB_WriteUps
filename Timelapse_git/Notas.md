## Notas sobre la resolución de la máquina

### Enumeración de servicios

#### ¿Qué es un archivo pfx?

Un archivo .pfx (Personal Information Exchange), basado en el estándar PKCS#12, es un formato binario que agrupa en un solo contenedor cifrado un certificado 
digital junto con su clave privada y, a menudo, la cadena de certificados intermedios.

Estos .pfx archivos incluyen certificados digitales utilizados para procesos de autenticación necesarias para determinar si un usuario o un dispositivo puede 
acceder a ciertos archivos, el propio sistema o de la red en el que el equipo está conectado como entre las personas con privilegios de administrador. 

type-> alias de Get-Content

$env:APPDATA -> Variable de entorno que apunta la carpeta de aplicaciones del usuario   
usualmente C:\Users\<usuario>\AppData\Roaming

\Microsoft\Windows\PowerShell\PSReadLine\ConsoleHost_history.txt -> Ruta donde reside el archivo de historial de comandos guardado por el modulo PSReadLine. 
Este archivo no se borra por antigüedad o tamaño por lo que puede llegar a ser muy grande.


### Escalada de Privilegios

#### ¿Qué es Local Administrator Password Solution?

(Error dentro del Write Up)
Local Administrator Password Solution es una herramienta de seguridad de Microsoft diseñada para gestionar automáticamente las contraseñas de las cuentas de 
administrador local en equipos unidos a un dominio. Su función principal es eliminar la práctica insegura 
de usar la misma contraseña para la cuenta de administrador local en todos los dispositivos de una red, lo que mitiga
riesgos críticos como los ataques de movimiento lateral y Pass-The-Hash

#### ¿Qué es ms-Mcs-AdmPwd?

Es un atributo de AD en donde se guarda la contraseña en texto plano del administrador local

