# Knife Write Up

**No distribuir mientras la máquina esté activa**

**Créditos al creador de la máquina: MrKN16H7**

Knife es una máquina Linux que presenta las siguientes vulnerabilidades y configuraciones.

### Acceso Inicial

1. PHP 8.1.0-dev – User-Agentt Remote Code Execution -> Es una vulnerabilidad presente en PHP 8.1.0 en donde la función zend_eval_string ejecuta un código
   que se envíe en un header HTTP con el nombre User-Agentt y después indicando la cadena zerodium. 

### Escalada de privilegios

1. El comando /usr/bin/knife está disponible para ser ejecutado como sudo, lo cual lleva a escalar privielgios puesto que la utilidad permite ejecutar comandos de sistema,
   incluyendo spawnear una shell.
