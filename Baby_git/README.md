# Baby Write Up

**No distribuir mientras la máquina esté activa**

**Créditos al creador de la máquina: xct**

Baby es una máquina Windows que concatena las siguientes configuraciones:

## Acceso Inicial

1. Bind anónimo a Active Directory lo que permite enumerar el dominio
2. Lectura de contraseñas en texto claro
3. Password Spraying debido a una contraseña coloccada por defecto, más la posibilidad de cambiar la contraseña de un usuario

## Escalda de privilegios 

1. Demasiados privielgios otorgados al usuario: SeBackupPrivilege, SeRestorePrivilege
2. Debido a los permisos se tiene la posibilidad de copiar archivos sensibles para obtener hashes y autenticarse haciendo pass-the-hash.

