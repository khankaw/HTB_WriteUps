# Expressway

**No distribuir mientras la máquina esté activa**

**Créditos al creador de la máquina: dakkmaddy**

Expressway es una máquina Linux que presenta las siguientes configuraciones y vulnerabilidades:  

### Acceso Inicial

1. Servidor TFTP con archivos sensibles
2. Contraseña débil crackeable con hashcat en configuración de VPN

### Escalada de Privilegios

1. CVE-2025-32462 -> Error de autorización de sudo 1.9.17, lo que permite esclar privilegios   

### CVE-2025-32462

Es un error de autorización que permite ejecutar comandos como otro usuario que tenga permisos definidos en sudoers. Con sudo -h (host) -l se pueden listar los permisos, 
sin embargo si se hace sudo -h (host) (comando) el comando se ejecutará con los privilegios del host.

