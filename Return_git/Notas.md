# Notas sobre la resolución de la máquina

### Acceso Inicial

#### ¿Qué es IIS?

Internet Information Services es el servidor oficial de Microsoft desarrollado para Windows. Además
de soportar HTTP, también soporta FTP, FTPS, SMTP y NNTP.

### Escalada de Privilegios

#### ¿Qué es el grrupo Server Operators?

Es un grupo de seguridad integrado en Windows Server para permitir la administración delegada de 
controladores de dominio (DC) sin otorgar derechos completos de Domain Admins. 

El exploit se basa en que con este grupo el usuario tiene el poder de modificar servicios del sistema
incluyendo modificar el binPath, que es el path que guarda el ejecutable para cierto proceso. 

A través de un proceso que ya está corriendo se abusa del privilegio mencionado y se coloca el 
ejecutable nc.exe para ejecutar una Reverse Shell


