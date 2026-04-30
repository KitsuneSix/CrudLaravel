Sistema CRUD de Productos
Se desarrolló un sistema de gestión de productos utilizando el framework Laravel 13. El sistema permite realizar las cuatro operaciones básicas de persistencia de datos (CRUD): Crear, Leer, Actualizar y Eliminar registros de una base de datos MySQL gestionada a través de WampServer.

Estructura de la Base de Datos 
Para la persistencia, se creó una tabla llamada products. La estructura se definió mediante una migración de Laravel para asegurar la integridad de los datos.

Archivo: database/migrations/xxxx_xx_xx_create_products_table.php

Campos:

id: Identificador único (Auto-incremental).

nombre: String (Requerido).

descripcion: Text (Opcional).

precio: Decimal (10,2).

timestamps: Registro de fecha de creación y edición.

Modelo de Datos
El modelo Product actúa como el puente entre la lógica del código y la base de datos. Se habilitó la asignación masiva para permitir la entrada de datos desde los formularios de forma segura.

Archivo: app/Models/Product.php

Atributo clave: protected $fillable = ['nombre', 'descripcion', 'precio'];

Controlador de Lógica 
El controlador gestiona el flujo de la aplicación, desde la validación de los datos hasta la redirección de las vistas.

Archivo: app/Http/Controllers/ProductController.php

Métodos principales:

index(): Recupera todos los productos de la base de datos usando Product::all() y los muestra en la tabla principal.

store(): Valida que el nombre sea obligatorio y el precio sea numérico antes de guardar el registro.

update(): Permite modificar los datos de un producto existente.

destroy(): Elimina el registro seleccionado de la base de datos.

Sistema de Rutas
Se utilizó una ruta de tipo Resource para generar automáticamente las 7 rutas necesarias para el CRUD (Index, Create, Store, Show, Edit, Update, Destroy).

Archivo: routes/web.php

Código: Route::resource('products', ProductController::class);

 Interfaz de Usuario 
Las vistas se diseñaron utilizando el motor de plantillas Blade y se les aplicó estilo moderno mediante Tailwind CSS para un diseño limpio y responsivo.

Vistas principales (resources/views/products/):

layout.blade.php: Plantilla base con la estructura HTML, el contenedor principal y los mensajes de éxito.

index.blade.php: Muestra la tabla de productos con acciones de "Editar" y "Eliminar".

create.blade.php / edit.blade.php: Formularios con validación de campos y manejo de métodos HTTP (POST y PUT).

 Comandos Utilizados en el Proyecto
Para mantener el entorno sincronizado, se utilizaron los siguientes comandos en la terminal de VS Code:

php artisan make:migration create_products_table: Crear el archivo de la tabla.

php artisan migrate:fresh: Borrar y recrear la base de datos para limpiar errores.

php artisan serve: Iniciar el servidor local de desarrollo.
