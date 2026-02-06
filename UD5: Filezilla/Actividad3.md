# Actividad 3: Creación de usuarios y grupos en el servidor FTP
Objetivo

Crear usuarios y grupos en el sistema para controlar el acceso al servidor FTP, asignando permisos, directorios raíz y límites de conexión, y comprender la diferencia entre permisos de usuario y permisos de grupo.

## 1. Creación de grupos

Se crea un grupo con permisos limitados para los usuarios FTP.
```
sudo groupadd ftp_limitado
```

Este grupo se utilizará para aplicar permisos comunes a varios usuarios.

## 2. Creación de usuarios FTP

Se crean dos usuarios asociados al grupo `ftp_limitado`.

### Usuario 1
```
sudo useradd -m -g ftp_limitado -s /usr/sbin/nologin ftpuser1
sudo passwd ftpuser1
```
### Usuario 2
```
sudo useradd -m -g ftp_limitado -s /usr/sbin/nologin ftpuser2
sudo passwd ftpuser2
```

El uso de `/usr/sbin/nologin` evita que los usuarios puedan iniciar sesión por SSH.

## 3. Definición del directorio raíz

Se define un directorio raíz común para los usuarios FTP:
```
sudo mkdir -p /srv/ftp/limitado
```

Asignación de propietario y grupo:
```
sudo chown root:ftp_limitado /srv/ftp/limitado
sudo chmod 750 /srv/ftp/limitado
```

Esto permite:

- Lectura y escritura para el grupo
- Acceso restringido a otros usuarios

## 4. Asociación de usuarios al directorio raíz (chroot)

En el archivo de configuración de vsftpd:
```
sudo nano /etc/vsftpd.conf
```

Se añaden o verifican las siguientes líneas:
```
local_enable=YES
write_enable=YES
chroot_local_user=YES
allow_writeable_chroot=YES
```

Cada usuario queda encerrado en su directorio, evitando el acceso al resto del sistema.

## 5. Configuración de permisos
Permisos aplicados
```
ls -ld /srv/ftp/limitado
```
![]()

## 6. Límites de conexión

En `/etc/vsftpd.conf` se configuran límites básicos:
```
max_clients=10
max_per_ip=2
```

Esto limita:

- Número máximo de clientes simultáneos
- Número máximo de conexiones por IP

Tras los cambios, se reinicia el `vsftpd` y no debe de haber más problemas.

## 7. Diferencias entre permisos de usuario y permisos de grupo

### Permisos de usuario

- Se aplican a un usuario concreto
- Tienen prioridad sobre los permisos de grupo
- Permiten un control individual y específico

### Permisos de grupo

- Se aplican a todos los usuarios que pertenecen al grupo
- Facilitan la administración cuando hay varios usuarios
- Garantizan permisos homogéneos sin configuración individual
