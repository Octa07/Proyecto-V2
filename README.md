Guía para ejecutar SAGER localmente con **MySQL Workbench** y el servidor integrado de **PHP**.

## Requisitos

- MySQL Server instalado y en ejecución.
- MySQL Workbench.

Workbench administra la base de datos; el servidor MySQL debe estar iniciado por separado. El servidor integrado de PHP ejecuta la página web, por lo que no hace falta iniciar Apache.

## 1. Crear la base de datos

1. Abre MySQL Workbench y conecta a tu servidor local: host `localhost`, puerto `3306`, usando la cuenta administradora que configuraste al instalar MySQL (normalmente `root`).
2. Abre una pestaña SQL y crea el usuario que usará PHP:

	```sql
	CREATE USER IF NOT EXISTS 'usuarioClases'@'localhost' IDENTIFIED BY 'Pass123';
	```

3. Abre el archivo `Proyecto/prototipo/database.sql` desde **File > Open SQL Script** y ejecútalo con el botón del rayo. El script crea `sistema_reservas`, sus tablas, los servicios y el insumo inicial, y concede permisos a `usuarioClases`.
4. En **SCHEMAS**, actualiza la lista y confirma que aparece `sistema_reservas`.

Si el usuario `usuarioClases` ya existe con otra contraseña, actualízalo en Workbench o cambia las credenciales correspondientes en `Proyecto/prototipo/config/conexion.php`. La contraseña del usuario administrador de MySQL es la que configuraste tú; no está guardada en el proyecto.


## 2. Credenciales locales

| Cuenta | Usuario | Contraseña |
| --- | --- | --- |
| Administrador de SAGER, en la base local existente | `admin@sager.com` | `pass123` |
| Conexión PDO de la aplicación | `usuarioClases` | `Pass123` |
| Administrador de MySQL Workbench | `root` o el usuario administrador de tu instalación | La que configuraste al instalar MySQL |

Las contraseñas distinguen mayúsculas de minúsculas. En una base recién creada, si el administrador de SAGER aún no existe, abre otra terminal en `Proyecto/prototipo` y ejecuta `php crear_admin.php`; elige el correo y la contraseña que quieras usar para el panel.
