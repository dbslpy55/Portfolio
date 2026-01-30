## 1. Esquema general de la arquitectura FTP

┌───────────────┐ Canal de Control (21) ┌────────────────┐
│ Cliente FTP │ ─────────────────────────────────► │ Servidor FTP │
│ (FileZilla) │ │ (FileZilla Srv)│
└───────────────┘ └────────────────┘
│
│ Canal de Datos (temporal)
▼
Transferencia de archivos


---

## 2. Esquema detallado del canal de control

┌───────────────┐ Puerto 21 (Control) ┌────────────────┐
│ Cliente FTP │ ───────────────────────────────► │ Servidor FTP │
└───────────────┘


### Comandos típicos:
- USER
- PASS
- LIST
- RETR
- STOR

Este canal permanece **abierto durante toda la sesión**.

---

## 3. Esquema de transferencia de datos

┌───────────────┐ Canal de Datos ┌────────────────┐
│ Cliente FTP │ ◄───────────────────────────────► │ Servidor FTP │
└───────────────┘


- Solo se abre cuando hay transferencia.
- Se cierra al finalizar la operación.

---

## 4. Modo ACTIVO (Active FTP)

### Flujo paso a paso

1. El cliente abre el canal de control (21).
2. El cliente informa un puerto aleatorio (>1024).
3. El servidor inicia la conexión de datos desde su puerto 20.

┌───────────────┐ ┌────────────────┐
│ Cliente FTP │ │ Servidor FTP │
│ Puerto >1024 │ │ Puerto 21 / 20 │
└───────┬───────┘ └───────┬────────┘
│ Control (21) │
│──────────────────────────────────────────────►│
│ │
│◄──────────────────────────────────────────────│
│ Datos (desde puerto 20 del servidor) │


❌ Problemas:
- El servidor inicia conexiones al cliente.
- Dificultades con NAT y firewalls.

---

## 5. Modo PASIVO (Passive FTP) ✅

### Flujo paso a paso

1. El cliente abre el canal de control (21).
2. El servidor asigna un puerto pasivo.
3. El cliente inicia la conexión de datos hacia ese puerto.

┌───────────────┐ ┌────────────────┐
│ Cliente FTP │ │ Servidor FTP │
│ Puerto >1024 │ │ Puerto 21 / Px │
└───────┬───────┘ └───────┬────────┘
│ Control (21) │
│──────────────────────────────────────────────►│
│ │
│──────────────────────────────────────────────►│
│ Datos (puerto pasivo del servidor) │


✔ Ventajas:
- El cliente inicia todas las conexiones.
- Compatible con NAT y máquinas virtuales.
- Modo recomendado.

---

## 6. Comparación visual resumida

ACTIVE MODE
Cliente ◄──── Datos ──── Servidor
Cliente ───── Control ─► Servidor

PASSIVE MODE
Cliente ───── Control ─► Servidor
Cliente ───── Datos ───► Servidor


---

## 7. Puertos implicados

CONTROL
Cliente ───► Servidor : 21

DATOS (Activo)
Servidor:20 ───► Cliente:>1024

DATOS (Pasivo)
Cliente:>1024 ───► Servidor:50000-51000


---

## 8. Conclusión técnica

El uso de esquemas claros permite comprender el funcionamiento interno del protocolo FTP. El modo pasivo es el más adecuado en entornos virtualizados y con firewall, como máquinas virtuales Ubuntu con FileZilla Server.
