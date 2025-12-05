# Archivos clave de configuración en Tomcat

## 1. `conf/server.xml`
Es el archivo principal de configuración del servidor. Define:
- **Conectores (Coyote)**: puertos, protocolo HTTP/AJP, atributos de conexión.  
- **Service** y **Engine (Catalina)**: nivel global del contenedor de servlets.  
- **Hosts virtuales**: dominios gestionados por el servidor.  
- **Realms**, **valves**, **listeners** y rutas de logs.  
Es el archivo que determina cómo Tomcat arranca y cómo recibe peticiones.

## 2. `conf/web.xml`
Es el **descriptor de despliegue por defecto** para *todas* las aplicaciones.  
Define:
- Configuración por defecto de servlets y filtros.  
- Tipos MIME.  
- Parámetros globales.  
- Páginas de error genéricas.  
Cualquier `WEB-INF/web.xml` de una app puede sobrescribir estos valores.

## 3. `conf/tomcat-users.xml`
Controla usuarios, roles y permisos del servidor.  
Define:
- Usuarios administrativos (por ejemplo, para Manager o Host Manager).  
- Roles asociados: `manager-gui`, `admin-gui`, `manager-script`, etc.  
- Permisos de acceso a aplicaciones internas del servidor.  

## 4. `conf/context.xml`
Archivo que define la configuración **por defecto de todos los contextos (aplicaciones)**:  
- Recursos JNDI (BBDD, pools de conexiones).  
- Variables de entorno y parámetros de contexto.  
- Configuración de sesiones y seguridad.  
Una aplicación puede incluir su propio `META-INF/context.xml` para sobrescribirlo.

---

# Mapa visual de dependencias entre los archivos

