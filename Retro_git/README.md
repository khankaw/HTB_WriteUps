# Retro Write Up

**No distribuir mientras la máquina esté activa**

**Créditos al creador de la máquina: r0BIT**

Retro es una máquina Windows que presenta las siguientes configuraciones y vulnerabilidadesw:

### Acceso Inicial:

1. Autenticación anónima en SMB
2. Lectura de archivos sensibles
3. Contraseñas débiles para usuarios del dominio AD

### Escalada de Privilegios:

1. Plantilla de Active Directory Certificate Services vulnerable a ESC1

## ESC1

Es una vulnerabilidad presente en ADCS que permite que cualquier usuario del dominio haga una petición válida para obtener el certificado de otro usuario y por lo tanto
autenticarse como tal.  


