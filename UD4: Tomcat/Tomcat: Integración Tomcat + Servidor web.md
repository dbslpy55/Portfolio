# Integración Apache2 + Tomcat 10 en Ubuntu 24.04 (Máquina Virtual)

## Índice
1. Integración mediante AJP
2. Verificación de funcionamiento
3. Bibliografía

---

## 1. Integración mediante AJP

Lo primero que se debe hacer es activar el conector de AJP en Tomcat, editando el fichero **"server.xml"** y quitarle los comentarios al siguiente código:
```
<Connector port="8009" protocol="AJP/1.3" redirectPort="8443" />
```
Después de esto solo se debe reiniciar Tomcat para tener todo actualizado. Ahora debemos centrarnos en la configuracion de Apache para poder usar al AJP, para ello es meterse a un archivo de de la carpeta apache2 y crear un archivo llamado **"tomcat-ajp.conf"**.

```
sudo nano /etc/apache2/sites-available/tomcat-ajp.conf
```
Ya dentro de este archivo hay que crear el **virtualhost**:

```
<VirtualHost *:80>
    ServerName localhost
    ProxyPass /sample ajp://localhost:8009/sample
    ProxyPassReverse /sample ajp://localhost:8009/sample
</VirtualHost>
```
Por último, queda activar el sevidor web:

```
sudo a2ensite tomcat-ajp.conf
```
---

## 2. Verificación de funcionamiento

Por último, queda el funcionamiento del servidor web, verificando la app directamente: 

![Funcionamiento](funcionamiento.png)

---
## Bibliografía

- Apache Software Foundation. (2024). *Apache HTTP Server Documentation*.  
  https://httpd.apache.org/docs/

- Apache Software Foundation. (2024). *Apache Tomcat 10.1 Documentation*.  
  https://tomcat.apache.org/tomcat-10.1-doc/

- Ubuntu Documentation. (2024). *Tomcat Installation and Configuration*.  
  https://help.ubuntu.com/

- DigitalOcean. (2023). *How To Install Apache Tomcat on Ubuntu*.  
  https://www.digitalocean.com/community/tags/tomcat

- Red Hat. (2024). *Reverse Proxy and Load Balancing with Apache HTTPD*.  
  https://access.redhat.com/documentation/

- StackOverflow Threads sobre AJP y Reverse Proxy (consultas técnicas específicas).  
  https://stackoverflow.com/

- Baeldung. (2023). *Guide to Apache Tomcat Configuration*.  
  https://www.baeldung.com/

- Oracle Java Docs (JSP/Servlet specification).  
  https://docs.oracle.com/javaee/
