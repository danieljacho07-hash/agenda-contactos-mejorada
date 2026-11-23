# Agenda Personal de Contactos — Práctica de mejoras y despliegue

Aplicación PHP + MySQL con registro, inicio de sesión y contactos privados por usuario.

- URL pública: https://agenda-daniel-jacho.fwh.is/login.php
- Repositorio GitHub: https://github.com/danieljacho07-hash/agenda-contactos-mejorada

## Tecnologías
PHP 8+, MySQL/MariaDB, PDO, HTML5, CSS3, Apache (XAMPP o hosting PHP).

## Mejoras respecto a la versión anterior
1. **Opción A, búsqueda:** filtra por nombre, correo o ciudad desde el panel. Usa consultas preparadas y mantiene el filtro `id_usuario`.
2. **Opción D, favoritos:** campo `favorito` (0/1), casilla en creación y edición, botón para marcar/desmarcar y filtro «Solo favoritos».

Se mantienen registro, login, cierre de sesión, CRUD, protección CSRF, hash de contraseñas y aislamiento entre usuarios.

## Instalación local (XAMPP)
1. Copia `agenda_contactos` a `C:\xampp\htdocs\`.
2. Inicia Apache y MySQL.
3. Si instalas desde cero, importa `database/agenda_contactos.sql` desde phpMyAdmin. Si YA tienes la base anterior, **no borres tus datos**: haz copia de seguridad y ejecuta solamente `database/actualizar_desde_version_anterior.sql` una vez.
4. Configura `config/conexion.php` (por defecto host localhost, BD agenda_contactos, usuario root, contraseña vacía) o crea `config/conexion.local.php` tomando como ejemplo `config/conexion.local.ejemplo.php`.
5. Abre `http://localhost/agenda_contactos/registro.php`.
6. Registra dos usuarios y verifica que cada uno vea solamente sus contactos. Prueba búsqueda, favoritos, edición y eliminación.

## Despliegue en hosting PHP + MySQL gratuito
1. Crea una cuenta en un proveedor que ofrezca **PHP, MySQL y acceso a phpMyAdmin** (por ejemplo InfinityFree, según disponibilidad actual).
2. Crea una base de datos MySQL y anota host, nombre, usuario y contraseña que te entregue el proveedor.
3. Importa `database/agenda_contactos.sql` en el phpMyAdmin del hosting. Si el proveedor no permite `CREATE DATABASE` o `USE`, quita las dos primeras instrucciones y selecciona antes la base creada por el panel.
4. Sube el contenido de la carpeta `agenda_contactos` al directorio público (`htdocs` o equivalente), mediante administrador de archivos o FTP.
5. En el hosting crea `config/conexion.local.php` con los datos reales, usando `config/conexion.local.ejemplo.php` como guía. **No subas las credenciales a GitHub.**
6. Visita `https://TU-DOMINIO/registro.php`, registra un usuario y prueba todo. Si subiste la carpeta completa como subdirectorio, usa `/agenda_contactos/registro.php`.
7. Copia la URL pública real y el repositorio GitHub en las secciones pendientes de este README.

## Capturas de pantalla para incluir en el README
Sustituye los marcadores siguientes por capturas reales de la aplicación:

### Registro e inicio de sesión
![Registro y login — pendiente de captura](capturas/registro_login.png)

### Panel con búsqueda
![Búsqueda de contactos — pendiente de captura](capturas/busqueda.png)

### Favoritos
![Filtro de favoritos — pendiente de captura](capturas/favoritos.png)

### Aplicación publicada
![Aplicación en hosting — pendiente de captura](capturas/hosting.png)

Guarda las imágenes en `capturas/` con esos nombres para que GitHub las muestre.

## Archivos SQL
- `database/agenda_contactos.sql`: instalación nueva con tabla contactos y campo favorito.
- `database/actualizar_desde_version_anterior.sql`: migración de la base anterior conservando contactos existentes (ejecutar solo una vez).

## Seguridad
Consultas preparadas con PDO, escape HTML, contraseñas con hash, validación CSRF y filtrado por `id_usuario` en cada operación. Evita publicar contraseñas de MySQL o datos personales de usuarios de prueba.
