# Configuración y Despliegue de Tomcat en Ubuntu 24.04 (Máquina Virtual)

## Índice
1. Instalación de Tomcat
2. Archivos clave de configuración
3. Estructura básica de directorios
4. Flujo interno de funcionamiento
5. Despliegue automático de un WAR
6. Flujo interno del despliegue
7. Evidencia de despliegue
8. Bibliografía

---

## 1. Instalación de Tomcat

En Ubuntu 24.04 (máquina virtual), se instaló Tomcat 10 mediante APT:

```bash
sudo apt update
sudo apt install -y tomcat10
sudo systemctl start tomcat10
sudo systemctl enable tomcat10
sudo systemctl status tomcat10
