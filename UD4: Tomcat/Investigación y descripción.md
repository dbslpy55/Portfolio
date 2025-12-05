# Índice
1. Catalina  
2. Coyote  
3. Jasper  
4. Manager y Host Manager  
5. Estructura básica de directorios  
6. Flujo interno de funcionamiento  
7. Bibliografía  

# Resumen de componentes de Tomcat

## 1. Catalina: 

Es el contenedor de servlets de Tomcat y constituye el núcleo del servidor. Gestiona servlets, JSP compiladas y sesiones. Su configuración principal se encuentra en `conf/server.xml`.

## 2. Coyote: 

Es el conector que recibe peticiones HTTP/1.1 y AJP desde el exterior y las entrega internamente a Catalina. También se configura en `conf/server.xml`.

## 3. Jasper:

Es el motor de compilación JSP; convierte páginas JSP en servlets Java. Sus resultados se almacenan en el directorio `work/` y utiliza librerías del directorio `lib/`.

## 4. Manager y Host Manager: 

Son aplicaciones administrativas para desplegar, gestionar y monitorizar aplicaciones web. Se ubican en `webapps/manager` y `webapps/host-manager`.

## 5. Estructura básica de directorios:

La estructura básica incluye: `bin/` (scripts de inicio/parada), `conf/` (configuración), `webapps/` (aplicaciones), `lib/` (librerías del servidor) y `logs/` (registros generados).

## 6. Flujo interno de funcionamiento: 

El flujo interno comienza cuando **Coyote** recibe una petición y la traduce para **Catalina**, que determina el *Host* y el *Context* adecuados, ejecuta servlets o JSP (compiladas por **Jasper**) y devuelve la respuesta al cliente.

# Bibliografía
- [Apache Tomcat - Wikipedia](https://en.wikipedia.org/wiki/Apache_Tomcat#:~:text=a%20JSP%20engine)
- [Tomcat Manager y su configuración - Arquitectura Java](https://www.arquitecturajava.com/tomcat-manager-y-su-configuracion/)
