## Notas sobre la resolución de la máquina:

## Escaneo

* Active Directory requiere de LDAP, Kerberos y MSRPC para funcionar
* Con un bind anónimo se puede enumerar gran parte de la infraestructura AD como si se fuere un usuario
  autenticado

## Escaneo de servicios

* sAMAccountName corresponde al nombre de login del usuario

## Escalada de Privilegios

* SeBackupPrivilege permite leer cualquier archivo del sistema con el propósito de respaldarlo, saltándose
  ACL's y los permisos NTFS estándar.

* SeRestorePrivilege permite sobreescribir cualquier archivo del sistema con el propósito de
  respaldarlo.

* ### ¿Qué es una HIVE?

  Es un grupo lógico de claves, subclaves y valores de registro que tiene un conjunto de archivos auxiliares
  cargados en memoria cuando se inicia el sistema o un usuario inicia sesión.

  Cada vez que un nuevo usuario inicia sesión en el equipo, se crea un subárbol para ese usuario.

* ### ¿Qué es NTDS.dit?

  Se puede considerar el corazón de AD. se guarda en un DC en C:\Windows\NTDS\. Guarda usuarios, grupos
  y hashes de contraseñas.

  Potencialmente puede guardar contraseñas en texto claro si está habilitada la opción Store Password with Reversible
  Encryption.

* ### ¿Qué es un hash NTLM?
 
  LM, NT, NTLMv1 y NTLMv2 son algoritmos de hashing que también puede usar AD. Se usan para guardar contraseñas. 
  NTLMv2 y NTLMv2 son protocolos de autenticación construidos encima de estos hashes. NTLMv1 puede usar hashes NT y LM mientras que NTLMv2 usa exclusivamente NT. 

* ### ¿Qué es el hive SYSTEM?

  Es uno de los archivos más importantes puesto que contiene información sobre la configuración del hardware, los servicios, los controladores y datos de arranque.
  
* ### ¿Qué es la boot key o syskey?

  Es una clave de cifrado que Windows genera y almacena de forma fragmentada dentro de la hive SYSTEM. Su función original es añadir una capa de cifrado
  adicional sobre los hashes almacenados en la hive SAM.

  Se calcula a partir de datos dispersos en cuatro claves dentro de SYSTEM:

  CurrentControlSet\Control\Lsa\JD

  CurrentControlSet\Control\Lsa\Skew1

  CurrentControlSet\Control\Lsa\GBG

  CurrentControlSet\Control\Lsa\Data

  La Class Name de cada una de estas claves se concatena y se permuta con una permutación fija para reconstruir la bootkey de 16 bytes.
  
  Junto con este valor se usa el valor F de SAM para descifrar los hashes.

  En resumen, para descifrar los hashes NTLM se necesita la hive SYSTEM para calcular la bootkey y la hive SAM para obtener los hashes.

* ### NTDS.dit y SYSTEM

  Con SYSTEM también se pueden descifrar hashes dentro de NTDS.dit.

  PEK (Password Encryption Key) es una clave de 16 bytes , generada aleatoriamente cuando se promueve el servidor a Domain Controller y se almacena dentro de NTDS.dit
  cifrada con el bootkey.

  PEK se usa para cifrar hashes, a su vez, PEK se descifra con la bootkey.

  
  
