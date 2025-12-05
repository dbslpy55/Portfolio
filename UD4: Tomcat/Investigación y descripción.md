# Índice

1.  Componentes de Tomcat
    *   1.1 Catalina
    *   1.2 Coyote
    *   1.3 Jasper
    *   1.4 Manager y Host Manager
    *   1.5 Estructura básica de directorios
    *   1.6 Flujo interno de funcionamiento
2.  Bibliografía

## 1. Componentes de Tomcat

### 1.1 Catalina: 

Catalina es el contenedor de servlets de Tomcat. Catalina implementa las especificaciones de Sun Microsystems para servlets y JavaServer Pages (JSP). En Tomcat, un elemento Realm representa una "base de datos" de nombres de usuario, contraseñas y roles (similar a los grupos de Unix ) asignados a dichos usuarios. Diferentes implementaciones de Realm permiten integrar Catalina en entornos donde dicha información de autenticación ya se crea y mantiene

### 1.2 Coyote: 

Coyote es un componente conector para Tomcat compatible con el protocolo HTTP 1.1 y 2 como servidor web. Esto permite que Catalina, nominalmente un servlet de Java o contenedor JSP, también actúe como un servidor web simple que sirve archivos locales como documentos HTTP. Coyote detecta conexiones entrantes al servidor en un puerto TCP específico y reenvía la solicitud al motor Tomcat para procesarla y enviar una respuesta al cliente solicitante.

### 1.3 Jasper:

Jasper es el motor JSP de Tomcat. Analiza archivos JSP para compilarlos en código Java como servlets (archivos que Catalina puede gestionar). En tiempo de ejecución, Jasper detecta cambios en los archivos JSP y los recompila. A partir de la versión 5, Tomcat utiliza Jasper 2, una implementación de la especificación JSP 2.0 de Sun Microsystems.

### 1.4 Manager y Host Manager: 

Son aplicaciones administrativas para desplegar, gestionar y monitorizar aplicaciones web. Se ubican en `webapps/manager` y `webapps/host-manager`.

### 1.5 Estructura básica de directorios:

- bin: La carpeta bin almacena los ficheros binarios que permiten arrancar o parar Tomcat como son los ficheros startup y shutdown
- conf : Es la carpeta en la cual disponemos de todos los ficheros de configuración , esta es la que contiene el fichero que queremos modificar
- logs: La carpeta que almacena los ficheros de log.
- lib: La carpeta que almacena librerías a nivel de Tomcat y son compartidas por las aplicaciones
- webapps: La carpeta en la cual se despliegan las diferentes aplicaciones web

### 1.6 Flujo interno de funcionamiento: 

El flujo interno comienza cuando **Coyote** recibe una petición y la traduce para **Catalina**, que determina el *Host* y el *Context* adecuados, ejecuta servlets o JSP (compiladas por **Jasper**) y devuelve la respuesta al cliente.

## 2. Bibliografía
- [Apache Tomcat - Wikipedia](https://en.wikipedia.org/wiki/Apache_Tomcat#:~:text=a%20JSP%20engine)
- [Tomcat Manager y su configuración - Arquitectura Java](https://www.arquitecturajava.com/tomcat-manager-y-su-configuracion/)
