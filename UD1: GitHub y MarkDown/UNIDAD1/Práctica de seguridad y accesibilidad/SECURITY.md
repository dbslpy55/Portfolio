# Seguridad del proyecto

## Archivos excluidos del control de versiones

Se han añadido reglas en **Seguridad.gitignore** para evitar subir al repositorio información y archivos innecesarios.  
Motivos principales:

- **Archivos de configuración local y contraseñas**: Contienen datos privados que no deben compartirse públicamente (credenciales, claves API, etc.).
- **Archivos temporales y logs**: Generados automáticamente y sin valor en el control de versiones.
- **Binarios y compilados**: No deben versionarse porque aumentan innecesariamente el tamaño del repositorio y se pueden regenerar a partir del código fuente.
- **Dependencias externas**: Se instalan con el gestor de paquetes correspondiente, no es necesario almacenarlas en Git.

## Medidas de protección de la documentación

- **Uso de ramas protegidas**: Se debe proteger la rama **main** para impedir que se hagan cambios sin revisión.
- **Revisión de pull requests**: Todo cambio debe ser aprobado al menos por otro miembro del equipo antes de ser fusionado.
- **Copias de seguridad**: Se recomienda clonar el repositorio en ubicaciones seguras o usar las funciones de backup de GitHub.

---

## Niveles de acceso en el repositorio

- **Read (solo lectura)**: Útil para testers o revisores externos que solo necesitan consultar el código.  
- **Write (escritura)**: Adecuado para desarrolladores que trabajan activamente en nuevas funcionalidades.  
- **Admin**: Reservado para líderes de proyecto o responsables de la infraestructura. Este nivel permite modificar configuraciones críticas.  
