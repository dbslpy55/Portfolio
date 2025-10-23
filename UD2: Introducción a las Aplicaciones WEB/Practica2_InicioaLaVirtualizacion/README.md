# Informe Técnico: Iniciación a la Virtualización

## 1. ¿Qué es la virtualización?

La **virtualización** es una tecnología que permite ejecutar varios sistemas operativos o entornos de software independientes sobre una misma máquina física.  
Esto se logra mediante un software llamado **hipervisor**, que gestiona los recursos y coordina el funcionamiento de las **máquinas virtuales (VMs)**.

**Conceptos clave:**
- **Hipervisor:** Software que administra las máquinas virtuales (ej. VirtualBox, VMware, Hyper-V).
- **Imagen ISO:** Archivo que contiene una copia exacta de un sistema operativo o software de instalación.
- **Recursos virtualizados:** CPU, memoria RAM, almacenamiento y red.

## 2. Instalación de Ubuntu en VirtualBox

### Pasos realizados

1. Se descargó la ISO de **Ubuntu 24.04 LTS** desde la página oficial:  
   [https://ubuntu.com/download/desktop](https://ubuntu.com/download/desktop)
2. En VirtualBox, se creó una nueva máquina virtual con la siguiente configuración:

   | Parámetro             | Valor recomendado       |
   |------------------------|-------------------------|
   | Nombre                | Ubuntu-DAW2DAW          |
   | Memoria RAM           | 4096 MB                 |
   | Disco duro virtual    | 50 GB (VDI, dinámico)   |
   | Tipo de red           | NAT                     |
   | Sistema operativo     | Ubuntu (64-bit)         |

3. Se inició la instalación de Ubuntu siguiendo el asistente gráfico.
4. Tras la instalación, se añadieron las **Guest Additions** para mejorar el rendimiento y la integración del sistema.
5. Se verificó el correcto funcionamiento de la máquina y se realizó una captura del escritorio.

## 3. Instalación de Docker en Ubuntu

### Teoría básica

**Docker** es una plataforma que permite ejecutar aplicaciones dentro de **contenedores**, los cuales son entornos ligeros y portátiles que comparten el kernel del sistema operativo, a diferencia de las máquinas virtuales.

**Ventajas principales:**
- Portabilidad
- Aislamiento
- Escalabilidad
- Rapidez de despliegue
