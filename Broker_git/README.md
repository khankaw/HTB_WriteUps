# Broker Write Up

**No ditribuir mientras la máqiuna esté activa**

**Créditos al creador de la máquina: TheCyberGeek**

Broker es una máquina Linux que presenta las siguientes configuracioens y vulneerabilidades:

## Acceso Inicial

1. Credenciales por defecto no corregidas en ActiveMQ
2. CVE-2023-46604 -> Unauthenticated Remote Code Execution en ActiveMQ 5.15.15

## Escalada de Privilegios

1. Permisos para ejecutar nginx con privilegios administrativos

## Sobre CVE-2023-46604

Es una vulnerabilidad en la que un atacante puede tener acceso a instanciar clases abritrarias en ActiveMQ,
enviando un mensaje data type 31 (EXCEPTION_RESPONSE). Con esto se consigue poder instanciar la clase ClassPathXmlApplicationContex, la cual
permite la configuración de una aplicación Spring (framework disponible dentro de ActiveMQ)
vía un documento XML, cuya ubicación remota se proporciona como string . El documento
XML contendrá código malicioso para ejecutar un proceso dentro del servidor.

## Referencias 

1. https://es.wikipedia.org/wiki/Apache_ActiveMQ
2. https://www.rapid7.com/blog/post/ra-cve-2023-46604-analysis/
3. https://github.com/SaumyajeetDas/CVE-2023-46604-RCE-Reverse-Shell-Apache-ActiveMQ
4. https://gtfobins.org/gtfobins/nginx/



