## Notas sobre la resolución de la máquina

### Enumeración web

#### ¿Qué es el X-Backend-Server Header?

x-backend-server se usa para regresar el nombre del back-end server que puede estar detrás de un load-balancer.

Este header potencialmente incluye ip's internas o hostnames que pueden ser usados por un atacante para acceder a dichos hosts directamente.

#### Sobre RocketChat

Es una plataforma de código abierto que permite compartir archivos, mensajería y realizar video conferencias en empresas para equipos particulares.

### Escalada de Privilegios

Polkit es un componente de autorización de privilegios para sistemas operativos tipo Unix, como Linux.

Su función principal es permitir que procesos sin privilegios se comuniquen con procesos privilegiados, proporcionando un control granular y centralizado 
sobre acciones administrativas sin necesidad de otorgar acceso completo de root.  
A diferencia de sudo, que suele conceder permisos a todo un proceso, Polkit evalúa políticas específicas para cada acción, distinguiendo entre usuarios, 
grupos y el estado de la sesión.

#### ¿Qué es el D-Bus?

D-Bus (Desktop Bus) es un sistema de comunicación entre procesos (IPC) y una llamada a procedimiento remoto (RPC) , para aplicaciones de software con el fin de 
comunicarse entre sí

Puede correrse en el contexto del sistema entero o en sesiones particulares de usuario.

El dbus-daemon actúa como intermediario entre procesos.

En el caso de la vulnerabilidad vista, dbus-daemon retorna un error si el proceso que buscaba permisos desaparece, sin embargo polkit autoriza dicho 
proceso como si hubiera sido solicitado por root o por otro proceso con altos privilegios. 

El PoC mencionado aprovecha esta vulnerabilidad insertando un usuario en el grupo sudo. 
