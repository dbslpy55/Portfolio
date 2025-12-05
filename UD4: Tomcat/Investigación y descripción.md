# Índice
1. Catalina  
2. Coyote  
3. Jasper  
4. Manager y Host Manager  
5. Estructura básica de directorios  
6. Flujo interno de funcionamiento  
7. Bibliografía  

# Resumen de componentes de Tomcat

**Catalina** es el contenedor de servlets de Tomcat y constituye el núcleo del servidor. Gestiona servlets, JSP compiladas y sesiones. Su configuración principal se encuentra en `conf/server.xml`.

**Coyote** es el conector que recibe peticiones HTTP/1.1 y AJP desde el exterior y las entrega internamente a Catalina. También se configura en `conf/server.xml`.

**Jasper** es el motor de compilación JSP; convierte páginas JSP en servlets Java. Sus resultados se almacenan en el directorio `work/` y utiliza librerías del directorio `lib/`.

**Manager** y **Host Manager** son aplicaciones administrativas para desplegar, gestionar y monitorizar aplicaciones web. Se ubican en `webapps/manager` y `webapps/host-manager`.

La estructura básica incluye: `bin/` (scripts de inicio/parada), `conf/` (configuración), `webapps/` (aplicaciones), `lib/` (librerías del servidor) y `logs/` (registros generados).

El flujo interno comienza cuando **Coyote** recibe una petición y la traduce para **Catalina**, que determina el *Host* y el *Context* adecuados, ejecuta servlets o JSP (compiladas por **Jasper**) y devuelve la respuesta al cliente.

# Bibliografía
- Apache Tomcat Official Documentation: https://tomcat.apache.org/tomcat-10.1-doc/
- The Apache Software Foundation – Tomcat Components Overview
- O’Reilly Media – *Tomcat: The Definitive Guide*
