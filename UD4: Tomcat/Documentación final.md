# Documentación Final — Apache Tomcat

## Índice
1. Arquitectura básica de Tomcat
2. Configuración del servidor
3. Integración con servidor web
4. Seguridad aplicada
5. Pruebas de funcionamiento y rendimiento
6. Recomendaciones de administración
7. Despliegue de Tomcat en contenedores
8. Conclusión
9. Bibliografía

---

## 1. Arquitectura básica de Tomcat

Apache Tomcat es un servidor de aplicaciones Java que implementa las especificaciones **Jakarta Servlet** y **Jakarta JSP**. Su arquitectura se basa en componentes internos bien definidos:

- **Catalina**: núcleo del servidor y contenedor de servlets.
- **Coyote**: gestiona las conexiones HTTP/HTTPS y actúa como conector.
- **Jasper**: motor encargado de compilar y ejecutar páginas JSP.
- **Manager / Host Manager**: aplicaciones web para administración.

La estructura lógica se organiza en:
- *Service* → *Engine* → *Host* → *Context*.

---

## 2. Configuración del servidor

La configuración principal de Tomcat se realiza mediante archivos XML ubicados en `/etc/tomcat10/`:

- **server.xml**: define conectores, puertos, hilos y SSL.
- **web.xml**: configuración global de aplicaciones web.
- **context.xml**: recursos compartidos (JNDI, pools, sesiones).
- **tomcat-users.xml**: usuarios y roles de administración.

Los directorios más relevantes son:
- `/var/lib/tomcat10/webapps` (aplicaciones)
- `/usr/share/tomcat10/lib` (librerías)
- `/var/log/tomcat10` (logs)

---

## 3. Integración con servidor web

Tomcat puede integrarse con **Apache HTTP Server** mediante **reverse proxy**. Se utiliza el módulo `mod_proxy` para redirigir peticiones desde Apache a Tomcat:

```
ProxyPass /app http://localhost:8080/app
ProxyPassReverse /app http://localhost:8080/app
```

### Ventajas de esta integración:

- Mejor rendimiento en contenido estático.
- Centralización de HTTPS.
- Balanceo de carga.
- Mayor seguridad.

## 4. Seguridad aplicada
Las principales medidas de seguridad implementadas son:

### Autenticación y roles
Configurados en `tomcat-users.xml`:

- `manager-gui`
- `admin-gui`

### Restricción de acceso
El acceso a Manager y Host Manager se limita por IP (`localhost`).

### HTTPS
Se configuró un conector SSL con keystore:

- Puerto 8443
- Certificado autofirmado

### Mejoras que se le pueden aplicar

- No usar contraseñas débiles.
- No exponer el Manager en producción.
- Usar un firewall y reverse proxy en caso de errores fatales.

## 5. Pruebas de funcionamiento y rendimiento
Se realizaron pruebas de carga usando ApacheBench y curl paralelo. Un ejemplo de prueba que se ha hecho en clases:

```
ab -n 1000 -c 10 http://localhost:8080/
```

Se ajustaron nuevos parámetros en server.xml:

- **maxThreads**
- **minSpareThreads**
- **acceptCount**
- **connectionTimeout**

### Resultados
Tras los ajustes se obtuvo:

- Mayor número de peticiones por segundo.
- Menor tiempo de respuesta.
- Sin errores de conexión.

## 6. Recomendaciones de administración

- Supervisar logs regularmente.
- No modificar **server.xml** sin reiniciar Tomcat.
- Separar entornos (desarrollo / producción).
- Usar backups antes de cambios críticos.
- Limitar permisos de usuarios administrativos.
- Monitorizar uso de CPU y memoria.

## 7. Despliegue de Tomcat en contenedores
Se utilizó la imagen oficial de Tomcat en Docker:

```
docker pull tomcat:latest
docker run -d -p 8081:8080 tomcat:latest
```

Las aplicaciones se despliegan en:

```
/usr/local/tomcat/webapps
```

### Diferencias frente a Tomcat nativo

| Aspecto       | Tomcat nativo | Tomcat en Docker |
| ------------- | ------------- | ---------------- |
| Instalación   | Sistema       | Imagen           |
| Aislamiento   | Bajo          | Alto             |
| Persistencia  | Permanente    | Volátil          |
| Portabilidad  | Limitada      | Alta             |
| Escalabilidad | Manual        | Automática       |

## 8. Conclusión

Apache Tomcat es una plataforma robusta y flexible para aplicaciones Java. Su correcta configuración, seguridad, integración y uso de contenedores con Apache permiten adaptarlo a entornos profesionales, garantizando rendimiento y seguridad.

## 9. Bibliografía

[Apache Software Foundation. Apache Tomcat Documentation.](https://tomcat.apache.org/)

[Apache Software Foundation. Apache HTTP Server Documentation.](https://httpd.apache.org/docs/)

[Docker Inc. Docker Documentation.](https://docs.docker.com/)

[Ubuntu Documentation. Tomcat on Ubuntu.](https://help.ubuntu.com/)

[Baeldung. Tomcat Configuration Guide.](https://www.baeldung.com/)
