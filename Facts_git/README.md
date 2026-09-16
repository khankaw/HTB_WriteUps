# Facts

**No distribuir mientras la máquina esté activa**

**Créditos al creador de la máquina: LazyTitan33**

Facts es una máquina Linux que presenta las siguientes vulnerabilidades y configuraciones:

### Acceso Inicial

1. CVE-2025-2304 -> Escalada de privilegios local en CMS Camaleon 2.9.0
2. Lectura en texto claro de contraseñas para MinIO
3. Uso de una contraseña débil para proteger una llave ED25519 para ssh

### Escalada de privilegios

1. Privilegios sudo sobre Factor, una utilidad que permite ejecutar arbitrariamente archivos escritos en Ruby

## CVE-2025-2304

Es una vulnerabilidad que permite abusar de una petición de cambio de contraseña enviada como un usuario autenticado dentro de Camaleon CMS 2.9.0. Debido a la
implementación incorrecta de la función de cambio de contraseña, se puede modificar la petición y cambiar el rol del usuario de Client a Administrator.

## Referencias

https://github.com/Alien0ne/CVE-2025-2304  

https://github.com/d3vn0mi/cve-2025-2304-poc  

https://gtfobins.org/gtfobins/facter/#inherit 

