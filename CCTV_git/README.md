# CCTV Write Up

**No distribuir mientras la  máquina esté activa**

**Créditos al creado de la máquina y los scripts mostrados: holdthefort**

CCTV es una máquina Linux que concatena las siguientes vulnerabilidades: 

## Acceso Inicial

1. CVE-2024-51482 -> SQL Injection (Boolean Based)
2. Fuerza bruta sobre contraseñas débiles

## Movimiento Lateral

1. Lectura de logs
2. Tcpdump con capacidad de hacer sniffing en interfaces de red
3. Captura de contraseñas en texto claro

## Escalada de Privilegios

1. Port Forwarding habilitado en servicios
2. CVE-2025-60787 -> RCE en Motion Eye

## CVE-2024-51482

Es una vulnerabilidad de inyección SQL booleana que está
presente en ZoneMinder, el cual expone el endpoint web/ajax/event.php. Dentro de la
función removetag el parametro tagID es directamente pasado a una secuencia de comandos
SQL sin sanitizar, lo que ocasiona que sea inyectable.

## CVE-2025-60787

Es una vulnerabilidad de RCE dentro del servicio Motion Eye. Se puede inyectar código directamente a través de la GUI web y el input, al no ser
sanitizado, se interpertará como código. La vulnerabilidad consiste en que la confguración del servicio se está recargando constantemente
y lo que se escriba en los campos image_file_name y movie_filename se escribirá
directamente en /etc/motioneye/camera-*.conf.

## Referncias

1. https://github.com/BridgerAlderson/CVE-2024-51482
2. https://github.com/advisories/GHSA-j945-qm58-4gjx


