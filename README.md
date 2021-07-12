# IDECDash Backend
IDECDash Backend es un componente de IDECDash, visite la wiki del repositorio para encontrar más información sobre este y otros componentes.

## Requisitos
- Php 8.0
- Postgresql 13

IDECDash backend está desarrollada en laravel 8, por lo cual, hereda todos los requisitos de instalación de una aplicación laravel tradicional ([Ver requisitos aquí](https://laravel.com/docs/8.x/deployment#server-requirements "Requisitos de laravel")). Sin embarago, las versiones especificadas se deben respetar debido al uso de sintaxis y funciones exclusivas para dichas versiones. 
El motor de base de datos está limitado a postgresql, el restos de los driver pueden ser modificados según su preferencia. 

Se recomienda utilizar Redis como driver de caché.


## Instalación

1) Descarga el proyecto

`git clone https://github.com/xxxxx/interactive_dashboard_backend/`

2) Instala las dependencias

`composer update`

3) Crea una base de datos en postgresql y ejecuta en ella el script DDL ubicado en:

`/LoadCanvasData/canvas_data_portal_ddl.sql`

4) Copia la plantilla del fichero de entorno **.env.example** y renombra la copia por **.env**

5) Modifica el fichero de entorno **.env** (Ve el apartado de configuración para entender las nuevas claves)

6) Ejecuta las migraciones

`php artisan migrate`

## Configuración
Una vez que tengamos nuestro fichero de entorno podremos ver que posee nuevas claves en comparación a un fichero de entorno tradicional de laravel, para saber que valores asignar se explicará que hace cada apartado.

 

------------


Habilita el modo de debug para no notificar a usuarios finales y define un correo en donde recibirás sus notificaciones.
````
NOTIFICATIONS_DEBUG_MODE=true 
NOTIFICATIONS_DEBUG_EMAIL=example@domain.cl
````

------------



La aplicación procesará en lotes (chunk) las interacciones, define una cantidad acorde a sus capacidades de procesamiento.

````
PROCESS_REQUETS_CHUNK_SIZE=5000000
````


------------


Limita la cantidad de solicitudes de actualización de reprotes

**Observación:** Actualmente canvas data portal tiene un desfase de 48 Horas y una limitancia de actualización de datos de 24 Hrs. Tener un tiempo de actualización menor consumirá procesamiento y no reflejará datos diferentes.
````
COURSE_UPDATE_HOURS_LIMIT=24
````

------------


Distribución de cursos para cada cola de trabajo, se asigna la cantidad de miembros maximos por cola.
````
MAX_MEMBERS_SMALL_COURSES=35
MAX_MEMBERS_MEDIUM_COURSES=60
MAX_MEMBERS_BIG_COURSES=95
MAX_MEMBERS_HEAVY_COURSES=3000
````

------------


Define el dominio donde se encontrará el frontend
````
FRONTEND_URL= https://www.example.com
````

------------


Agrega la url de tu instancia de Canvas LMS. Registra una nueva aplicación OAuth en Canvas LMS y agrega el id y secreto que te proporcionará. 

**Observación:** La instancia Oauth creada en Canvas LMS es la misma que se utilizará en IDECDash Frontend e IDECDash Backend, si ya haz creado una deberás reutilizar las credenciales.
`
````
CANVAS_URL=https://your_instance.instructure.com
CANVAS_CLIENT_ID= 
CANVAS_CLIENT_SECRET= 
````
