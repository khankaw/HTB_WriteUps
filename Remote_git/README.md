# Remote Write Up

**No distribuir mientras la máquina esté activa**

**Créditos al creador de la máquina: mrb3n8132**


Remote es una máquina Windows que presenta las siguientes vulnerabilidades y configuraciones:

### Acceso Inicial

1. Acceso a NFS share que contiene archivos de configuración sensibles para Umbraco 7.12.4
2. CVE-2019-25137 -> Authenticated Remote Code Execution en Umbraco 7.12.4

### Escalada de Privilegios

1. CVE-2019-18988 -> Descifrado de contraseñas en Team Viewer 7
2. Reutilización de contraseñas

## Sobre CVE-2019-25137

Se expone el endpoint /umbraco/developer/Xslt/xsltVisualize.aspx mientras se esté autenticado. Este endpoint abre la posibilidad a visualizar código XSLT, en el cual, mediante
la función msxsl:script se puede incluir un script que será ejecutado por el servidor. 

## Sobre CVE-2019-18988

Es una vulnerabilidad menor que permite descifrar las contraseñas almacenadas en el registro por Team Viewer 7. Esto debido a que las claves para las contraseñas
son fijas

## Referencias

https://www.exploit-db.com/exploits/46153  

https://github.com/Ickarah/CVE-2019-25137-Version-Research  

https://whynotsecurity.com/blog/teamviewer/  

https://nvd.nist.gov/vuln/detail/cve-2019-18988  
