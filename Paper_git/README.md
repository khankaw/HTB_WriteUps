# Paper Write Up

**No distribuir mientras la máquina esté activa**

**Créditos al creador de la máquina: secnigma**

Paper es una máquina Linux que concatena las siguientes vulnerabilidades:

### Acceso inicial

1. Headers no estándar en peticiones web para descubrir nombres de dominio
2. CVE-2019-17671 -> Lectura de posts privados, revelación de información sensible
3. Bot mal configurado -> Lectura de contraseñas en texto claro

### Escalada de privilegios

1.  CVE 2021-3560 -> Forzar creación de usuarios con privilegios elevados usando Polkit.

## CVE-2019-17671

Es una vulnerabilidad en la que WordPress falla en su lógica para procesar solicitudes de lectura de posts. Si el primer post es público entonces envía todos los demás. 
Si el primer post es privado entonces simplemente no se puede leer. Modificando sencillamente el URL de la petición se pueden leer posts privados que puedan contener
información sensible.

## CVE 2021-3560

Es una vulnerabilidad de Bypass de Autenticación generada por una condición de carrera entre crear un proceso y matarlo rápidamente. Está 
presente en Polkit 0.115. Permite hacer un bypass de autenticación para ejecutar comandos con privilegios de administrador. Esto debido a un error
lógico dentro de Polkit. 
Si se envía una petición usando dbus-send y esta misma petición se mata rápidamente, se rompe el ciclo lógico de verificación y Polkit asume que la petición viene de root,
por lo que ejecuta la petición. Esta petición puede ser crear un usuario dentro del grupo sudo para poder solicitar una shell como root.

## Referencias

https://wpscan.com/vulnerability/3413b879-785f-4c9f-aa8a-5a4a1d5e0ba2/  
https://github.blog/security/vulnerability-research/privilege-escalation-polkit-root-on-linux-with-bug/   
https://www.hackingarticles.in/linux-privilege-escalation-polkit-cve-2021-3560/  
https://github.com/secnigma/CVE-2021-3560-Polkit-Privilege-Esclation  
