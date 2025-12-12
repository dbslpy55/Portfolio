# Despliegue simple de una aplicación web

## Índice
1. Instalación de Tomcat
2. Despliegue automático de un WAR
3. Flujo interno del despliegue

---

## 1. Instalación de Tomcat

En Ubuntu 24.04 (máquina virtual), se instaló Tomcat 10 mediante APT:

```
sudo apt update
sudo apt install -y tomcat10
sudo systemctl start tomcat10
sudo systemctl enable tomcat10
sudo systemctl status tomcat10
```

![Instalación de Tomcat en Ubuntu](img/instalacion.png)

---

## 2. Despliegue automático de un WAR

Se coloca el archivo sample.war en la carpeta de aplicaciones web:
```
sudo cp /tmp/sample.war /var/lib/tomcat10/webapps/
```
Gracias a esto, Tomcat detecta automáticamente el WAR y comienza el proceso de despliegue sin necesidad de reiniciar el servidor.

---

## 3. Flujo interno del despliegue

Cuando Tomcat detecta un WAR nuevo en `webapps/`, realiza los siguientes pasos:

- **Detección del WAR**: Catalina identifica el archivo sample.war.
- **Creación del Contexto**: Se registra un nuevo contexto `/sample` que será la URL de acceso.
- **Descompresión del WAR**: Tomcat extrae todo el contenido en `/var/lib/tomcat10/webapps/sample/`.
- **Lectura del descriptor web.xml**: Se configuran servlets, filtros, listeners y mapeos de URL.
- **Compilación de JSP (Jasper)**: Las JSP se convierten en servlets Java y se guardan en `/var/cache/tomcat10/work/`.
- **Inicialización de servlets y listeners**: Se cargan servlets con `<load-on-startup>` y se activan listeners de ciclo de vida.
- **Aplicación lista para recibir peticiones**: El conector Coyote habilita la aplicación en `http://localhost:8080/sample`.

## 4. Funcionamiento de la aplicación

![Hello World](img/Hello_world.png)
