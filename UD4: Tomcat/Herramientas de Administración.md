# Tomcat — Herramientas de Administración

## 1. Tomcat Manager

### Descripción
Tomcat Manager es una aplicación web administrativa que permite gestionar el ciclo de vida de las aplicaciones desplegadas en el servidor Tomcat.

### Funciones principales
- Despliegue de aplicaciones WAR.
- Arranque y parada de aplicaciones.
- Recarga de aplicaciones sin reiniciar el servidor.
- Eliminación de aplicaciones desplegadas.
- Visualización del estado y sesiones activas.

### Acceso

```http://localhost:8080/manager```

### Requisitos
- Usuario con rol `manager-gui`.
- Acceso restringido por IP (localhost por defecto).

---

## 2. Tomcat Host Manager

### Descripción
Tomcat Host Manager permite administrar hosts virtuales, posibilitando alojar múltiples dominios en una única instancia de Tomcat.

### Funciones principales
- Creación de hosts virtuales.
- Configuración de alias y rutas.
- Gestión del despliegue automático por host.
- Visualización de hosts existentes.

### Acceso

```http://localhost:8080/host-manager```

### Requisitos
- Usuario con rol `admin-gui`.

---

## 3. Diferencias principales

| Herramienta | Uso principal |
|------------|--------------|
| Manager | Gestión de aplicaciones |
| Host Manager | Gestión de dominios / hosts |

---

## 4. Conclusión

Las herramientas Manager y Host Manager permiten administrar Tomcat de forma centralizada. Manager se centra en las aplicaciones web, mientras que Host Manager facilita la creación y gestión de entornos multi-dominio.
