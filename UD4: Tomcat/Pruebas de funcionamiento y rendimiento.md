# Tomcat – Pruebas de funcionamiento y rendimiento

## 1. Objetivo
Evaluar el rendimiento del servidor Tomcat bajo carga y optimizar su configuración mediante ajustes en el archivo `server.xml`.

---

## 2. Herramientas utilizadas
- ApacheBench (ab)
- curl con ejecución paralela
- Máquina virtual Ubuntu 24.04
- Apache Tomcat 10

---

## 3. Pruebas iniciales

### Comando ApacheBench
```bash
ab -n 1000 -c 10 http://localhost:8080/
```
![Prueba del comando](ApacheBend.JPG)
