# Data Write Up

**No distribuir mientras la máqina esté activa**

**Créditos al creador de la máquina: xct**

Data es una máquina Linux que presenta las siguientes vulnerabilidades y configuraciones:

## Acceso Inicial

1. CVE-2021-43798 -> Unauthenticated Path Traversal + Arbitrary File Read desde Grafana 8.0.0
2. Uso de contraseña débil

## Escalada de Privilegios

1. Permiso para ejecutar docker exec como sudo sin contraseña

## CVE-2021-43798

Es una vulnerabiilidad que permite a un atacante no autenticado viajar entre directrios y leer archivos arbitraros 
dentro del sistema si está disponible alguna versión de Grafana anterior a 8.3.1. Ésta lectura se puede hacer desde una linea
de comandos con la herramienta curl, por ejemplo:  

```
curl --path-as-is "http://ip:3000/public/plugins/alertlist/../../../../../../../../../../../var/lib/grafana/grafana.db"
```

## Referencias

1. https://github.com/MalekAlthubiany/CVE-2021-43798
