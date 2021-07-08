## IDECDash Backend

### Requisitos
- Php 8.0
- Postgresql 13

IDECDash backend está desarrollada en laravel 8, por lo cual, hereda todos los requisitos de instalación de una aplicación laravel tradicional ([Ver requisitos aquí](https://laravel.com/docs/8.x/deployment#server-requirements "Requisitos de laravel")). Sin embarago, las versiones especificadas se deben respetar debido al uso de sintaxis y funciones exclusivas para dichas versiones. 
El motor de base de datos está limitado a postgres, el restos de los driver pueden ser modificados según su preferencia. 

Se recomienda utilizar Redis como driver de caché.


### Instalación

1) Descarga el proyecto

`git clone https://github.com/xxxxx/interactive_dashboard_backend/`

2) Instala las dependencias

`composer update`

3) Crea una base de datos en postgresql y ejecuta en ella el script DDL ubicado en:

`/LoadCanvasData/canvas_data_portal_ddl.sql`

4) Copia la plantilla del fichero de entorno `.env.example` y renombra la copia por `.env`

5) Modifica el fichero de entorno `.env` (Ve el apartado de configuración para entender las nuevas claves)

6) Ejecuta las migraciones
`php artisan migrate`

### Configuración
`php artisan serve`

##### Ir a la wiki para conocer más sobre IDECDash Backend
