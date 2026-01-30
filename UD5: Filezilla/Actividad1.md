## Flujo de conexión FTP: Modo Activo vs Modo Pasivo

### Conceptos previos importantes

- **Conexión de control**: Siempre se establece por el puerto 21 del servidor FTP. Sirve para enviar comandos (`USER`, `PASS`, `LIST`, `RETR`, `STOR`, etc.).

- **Conexión de datos**: Se abre solo cuando hay transferencia de información (listados o archivos). Aquí es donde cambia el modo activo y pasivo.

### FTP en Modo Activo

En el modo activo, el servidor inicia la conexión de datos hacia el cliente.

![FTP en modo activo](img/FTPActivo.jpg)

### Explicación paso a paso (Modo Activo)

#### 1. Conexión de control

- El cliente abre un puerto aleatorio (Puerto N).
- Se conecta al puerto 21 del servidor.
- Se completa el `SYN → SYN-ACK → ACK`.

#### 2. Comando PORT

- El cliente envía el comando `PORT`.
- Indica al servidor:
  - Su dirección IP
  - El puerto N+1, donde escuchará datos.

#### 3. Solicitud de transferencia

- El cliente envía `LIST`, `RETR` o `STOR`.

#### 4. Conexión de datos

- El servidor inicia la conexión desde su puerto 20
- Se conecta al puerto N+1 del cliente.

#### 5. Transferencia

- Los datos fluyen por la conexión de datos.

---

### FTP en Modo Pasivo

En el modo pasivo, el cliente inicia todas las conexiones, tanto de control como de datos.

![FTP en modo pasivo](img/FTPPasivo.jpg)

### Explicación paso a paso (Modo Pasivo)

#### 1. Conexión de control

- Igual que en modo activo: Cliente → Puerto 21 del servidor.

#### 2. Comando PASV

- El cliente envía `PASV`.
- El servidor responde:
  - Su dirección IP
  - Un puerto aleatorio (Puerto Y) donde escuchará datos.

#### 3. Conexión de datos

- El cliente abre un nuevo puerto (Puerto Z).
- Se conecta al Puerto Y del servidor.

#### 4. Transferencia

- El cliente solicita `LIST`, `RETR` o `STOR`.
- Los datos se transfieren por la conexión pasiva.

### Diferencias entre Modo Activo y Modo Pasivo

| Característica           | Modo Activo             | Modo Pasivo          |
| ------------------------ | ----------------------- | -------------------- |
| Quién inicia datos       | Servidor                | Cliente              |
| Puerto de datos servidor | 20                      | Puerto aleatorio (Y) |
| Puertos abiertos cliente | Debe aceptar conexiones | Solo salientes       |
| Problemas con firewall   | Muy frecuentes          | Muy pocos            |
| Uso recomendado          | No recomendado          | Recomendado          |

