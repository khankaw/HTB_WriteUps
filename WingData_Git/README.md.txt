# Wing Data Write Up

**No distribuir mientras la  máquina esté activa**
**Créditos al creado de la máquina y los scripts mostrados: WackyH4cker**

Wing Data es una máquina Linux que concatena las siguientes vulnerabilidades y configuraciones:

### Acceso Inicial

1. Anonymous Login dentro de servidor FTP
2. CVE-2025-47812 -> Remote Code Execution
3. Archivos de configuración de usuarios con permiso de lectura
4. Contraseña crackeable con Hashcat

### Escalada de Privilegios

1. Permisos sudo para ejecutar un script de Python
2. CVE-2025-4517 -> Escritura arbitraria de archivos fuera del target con la librería tarfile

## CVE-2025-47812

Es una vulnerabilidad de Wing FTP que se aprovecha de que Lua no sanitiza el input dentro del campo username en el endpoint /loginok.html. Dentro de este campo se puede 
Añadir un nullbyte para indicar la finalización de una string y en seguida inyectar código.

## CVE-2025-4517

Es una vulnerabilidad que permite escritura arbitraria de archivos con la librería tarfile fuera del directorio target. Esto debido a que existe un bug en la implementación
de la función, que permite resolver symlinks con secuencias de path traversal si es que los nombres de los archivos a los que apuntan exceden cierta longitud. Dentro del código
indicado para resolver la máquina, se crea un archivo .tar con una serie de directorios anidados con nombres largos y sus respectivos symlinks. Éstos, al final, apuntan a un archivo, también
con un nombre largo y este a su vez, apunta a una secuencia de path traversal hasta llegar a /root/.ssh/authorized_keys, en dónde se escribe la llave pública de la máquina atacante
para obtener acceso como root sin contraseña.