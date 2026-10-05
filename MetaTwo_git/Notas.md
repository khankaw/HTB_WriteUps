# Notas sobre la resolución de la máquina:

### Identificación de vulnerabilidades:

* #### XML External Entity

Es una vulnerabilidad que ocurre cuando una aplicación procesa archivos XML de forma insegura, permitiendo que un atacante pueda manipular la petición para leer 
archivos del sistema.
Las entidades son parecidas a las variables dentro de un código de programación, sin embargo las entidades externas pueden contener recursos externos como links u archivos.
Si se tiene habilitado el procesamiento de entidades externas en el parser XML se puede dar lugar a leer archivos de sistema o visitar enlaces maliciosos.
La CVE-2021-29447 es una "blind XXE" ya que el valor no se extrae de forma directa ni se muestra en el navegador, si no que mediante la solicitud de un archivo DTD,
se logra exfiltrar la información hacia el servidor atacante.

* #### ¿Qué es un archivo DTD?

Un archivo DTD es un documento que define, a través de reglas, la estructura y sintaxis
de un lenguaje de marcado.

* #### ¿Qué es un archivo WAV?

WAV (Waveform Audio File Format) es un formato de archivo de audio digital desarrollado por Microsoft e IBM en 1991 para almacenar sonido en PCs

### Sobre CVE-2022-0739

* #### ¿Qué es wpnonce?

Es un mecanismo de seguridad de WordPress diseñado para prevenir ataques CSRF. Es un token único y temporal que se usa en Word Press para verificar una petición.
Se usa para validar si una acción viene de quien dice venir. Este token es generado por el propio Word Press. 
Este valor se usa para verificar la autenticidad de la petición que se está realizando.

### Escalada de Privilegios

* #### ¿Qué es passpie?

Passpie es un gestor de contraseñas de línea de comandos multiplataforma diseñado para administrar credenciales desde la terminal en Linux, macOS y Windows. 
Las contraseñas se cifran mediante GnuPG y se almacenan en archivos de texto YAML

* #### ¿Qué son las claves PGP?

Las claves PGP son pares de claves criptográficas (pública y privada) utilizadas por el sistema Pretty Good Privacy para garantizar la confidencialidad, 
autenticación e integridad de los datos en correos electrónicos y archivos.

* #### ¿Qué es GnuPG?

GnuPG (GNU Privacy Guard), comúnmente conocido como GPG, es una herramienta de software libre desarrollada por el Proyecto GNU que implementa el estándar OpenPGP (RFC 4880).  
Funciona como un reemplazo libre de PGP (Pretty Good Privacy) y permite realizar cifrado y firma digital de datos y comunicaciones electrónicas.







