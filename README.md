# Que es el CRUD?

CRUD es un acrónimo que se utiliza comúnmente en el desarrollo de software y se refiere a las operaciones básicas que se pueden realizar en cualquier sistema de gestión de bases de datos relacionales (RDBMS). Las letras CRUD representan las siguientes operaciones:

Create (Crear): Agregar nuevos registros a la base de datos.
Read (Leer): Leer o recuperar registros existentes de la base de datos.
Update (Actualizar): Modificar registros existentes en la base de datos.
Delete (Eliminar): Eliminar registros existentes de la base de datos.
Estas operaciones son fundamentales en cualquier aplicación que necesite interactuar con una base de datos. Por ejemplo, en una aplicación de gestión de empleados, el CRUD se usaría para agregar nuevos empleados (Create), mostrar la lista de empleados (Read), actualizar la información de un empleado (Update) y eliminar a un empleado (Delete).

El CRUD proporciona una estructura básica y esencial para el desarrollo de aplicaciones que manejan datos. La mayoría de las aplicaciones web y de software realizan estas operaciones en algún momento para interactuar con la base de datos subyacente.

# Aplicación CRUD de PHP

Este repositorio contiene una aplicación PHP CRUD (Create, Read, Update, Delete) simple. Es una demostración básica de cómo integrar PHP con una base de datos MySQL para gestionar datos de usuarios. La aplicación permite a los usuarios agregar, ver, editar y eliminar información de usuario.

## Tecnologías Utilizadas

- **PHP:** Lenguaje de script del lado del servidor utilizado para el desarrollo web.
- **MySQL:** Sistema de gestión de base de datos utilizado para almacenar datos de usuario.
- **HTML & CSS:** Utilizados para estructurar y dar estilo a las páginas web.
- **Tailwind CSS:** Un framework de CSS utilitario para el desarrollo rápido de interfaces de usuario.

## Páginas y Funcionalidades

### 1. Página de Inicio (`display.php`)

![Página de Inicio](images/display.png)

- **Funcionalidad:** Muestra todos los usuarios de la base de datos en un formato de tabla.
- **Características:** 
  - Ver todos los usuarios.
  - Enlaces de navegación para agregar, editar o eliminar información de usuario.

### 2. Agregar Usuario (`user.php`)

![Agregar Usuario](images/add.png)

- **Funcionalidad:** Permite agregar un nuevo usuario a la base de datos.
- **Características:** 
  - Formulario para ingresar detalles del usuario (nombre, correo electrónico, teléfono móvil, contraseña).
  - Validación de datos y envío a la base de datos.

### 3. Editar Usuario (`edit.php`)

![Editar Usuario](images/edit.png)

- **Funcionalidad:** Permite editar detalles de usuarios existentes.
- **Características:** 
  - Formulario prellenado con la información actual del usuario.
  - Actualización de detalles del usuario en la base de datos.

### 4. Eliminar Usuario (`delete.php`)

- **Funcionalidad:** Facilita la eliminación de un usuario de la base de datos.
- **Características:** 
  - Eliminación de información de usuario basada en el ID de usuario.

## Conexión a la Base de Datos (`connect.php`)

- **Propósito:** Establece una conexión con la base de datos MySQL.
- **Credenciales:** Utiliza nombre de host, nombre de usuario, contraseña y nombre de la base de datos para la conexión.

## Cómo Ejecutar

1. Clona el repositorio en tu máquina local.
2. Configura un entorno PHP y MySQL (como XAMPP).
3. Crea la base de datos usando phpmyadmin.
4. Ejecuta la aplicación en un servidor local.

## Nota de Seguridad

Esta aplicación es una demostración básica y no implementa medidas avanzadas de seguridad. Es recomendable utilizar declaraciones preparadas (prepared statements) u ORM para las interacciones con la base de datos para prevenir ataques de inyección SQL.

## Para diseñar formularios que formen parte de un sistema CRUD (Crear, Leer, Actualizar, Eliminar) en una aplicación, es importante considerar tanto la funcionalidad como la facilidad de uso para los usuarios finales. Aquí te dejo una guía básica sobre cómo puedes estructurar estos formularios para diferentes funciones, asumiendo que estamos hablando de una aplicación web o móvil con un backend SQL. 

PHP es un lenguaje de programación del lado del servidor muy popular para el desarrollo web. 

# 1. Formulario de Creación (Create)

Permitir a los usuarios ingresar todos los datos necesarios para crear un nuevo registro.
Campos de texto, selección o fechas para cada atributo del registro.
Validaciones para asegurar que los datos ingresados son correctos y completos.
Un botón para enviar el formulario y guardar el nuevo registro en la base de datos.

ejemplo de codigo:

<!DOCTYPE html>
<html lang="en">
<head>
  <meta charset="UTF-8">
  <meta name="viewport" content="width=device-width, initial-scale=1.0">
  <title>Formulario de Creación</title>
  <link rel="stylesheet" href="https://stackpath.bootstrapcdn.com/bootstrap/4.5.2/css/bootstrap.min.css">
</head>
<body>
  <div class="container mt-5">
    <div class="row justify-content-center">
      <div class="col-md-6">
        <h2 class="mb-4">Crear Nuevo Usuario</h2>
        <form action="crear_usuario.php" method="POST">
          <div class="form-group">
            <label for="nombre">Nombre:</label>
            <input type="text" class="form-control" id="nombre" name="nombre" required>
          </div>
          <div class="form-group">
            <label for="email">Email:</label>
            <input type="email" class="form-control" id="email" name="email" required>
          </div>
          <button type="submit" class="btn btn-primary">Crear Usuario</button>
        </form>
      </div>
    </div>
  </div>
</body>
</html>


En este ejemplo:

Utilizamos Bootstrap para el diseño y los estilos del formulario.
Creamos un formulario simple que solicita el nombre y el correo electrónico del usuario.
Cada campo de entrada está envuelto en un elemento div con la clase form-group para proporcionar estilos y espaciado adecuados.
Utilizamos el atributo required en los campos de entrada para garantizar que el usuario complete ambos campos antes de enviar el formulario.
El formulario se envía a crear_usuario.php utilizando el método POST para procesar los datos del usuario.
Puedes crear un archivo PHP (crear_usuario.php) para manejar la lógica de creación del usuario, donde puedes tomar los datos del formulario y guardarlos en tu base de datos.

# 2. Formulario de Lectura (Read)

Mostrar los datos existentes. Aunque técnicamente no es un "formulario", es parte de la funcionalidad CRUD.
Lista o tabla que muestre los registros existentes.
Opciones para filtrar o buscar registros específicos.

Ejemplo de codigo:

<!DOCTYPE html>
<html lang="en">
<head>
  <meta charset="UTF-8">
  <meta name="viewport" content="width=device-width, initial-scale=1.0">
  <title>Usuarios</title>
  <link rel="stylesheet" href="https://stackpath.bootstrapcdn.com/bootstrap/4.5.2/css/bootstrap.min.css">
</head>
<body>
  <div class="container mt-5">
    <div class="row justify-content-center">
      <div class="col-md-8">
        <h2 class="mb-4">Lista de Usuarios</h2>
        <table class="table">
          <thead>
            <tr>
              <th>ID</th>
              <th>Nombre</th>
              <th>Email</th>
            </tr>
          </thead>
          <tbody>
            <?php
            // Conexión a la base de datos
            $servername = "localhost";
            $username = "usuario";
            $password = "contraseña";
            $dbname = "basedatos";

            $conn = new mysqli($servername, $username, $password, $dbname);

            // Verificar la conexión
            if ($conn->connect_error) {
                die("Error de conexión: " . $conn->connect_error);
            }

            // Consulta SQL para obtener los usuarios
            $sql = "SELECT id, nombre, email FROM usuarios";
            $result = $conn->query($sql);

            if ($result->num_rows > 0) {
                // Imprimir los datos de cada usuario en filas de la tabla
                while($row = $result->fetch_assoc()) {
                    echo "<tr><td>" . $row["id"] . "</td><td>" . $row["nombre"] . "</td><td>" . $row["email"] . "</td></tr>";
                }
            } else {
                echo "<tr><td colspan='3'>No hay usuarios registrados</td></tr>";
            }
            $conn->close();
            ?>
          </tbody>
        </table>
      </div>
    </div>
  </div>
</body>
</html>


En este ejemplo:

Utilizamos Bootstrap para el diseño y los estilos de la tabla.
Creamos una tabla HTML con encabezados para ID, Nombre y Email.
Conectamos a la base de datos MySQL y ejecutamos una consulta SQL para seleccionar todos los usuarios.
Iteramos sobre los resultados de la consulta y mostramos los datos de cada usuario en filas de la tabla.
Si no hay usuarios en la base de datos, mostramos un mensaje indicando que no hay usuarios registrados.
Recuerda reemplazar "usuario", "contraseña" y "basedatos" con tus propias credenciales y nombre de base de datos.

# 3. Formulario de Actualización (Update)

Permitir a los usuarios modificar datos de un registro existente.
Campos de formulario prellenados con los datos existentes del registro.
Campos que el usuario puede cambiar, típicamente con la misma estructura que el formulario de creación.
Validaciones para asegurar que los cambios son válidos.
Un botón para enviar los cambios al servidor y actualizar el registro en la base de datos.

Ejemplo de codigo:

<!DOCTYPE html>
<html lang="en">
<head>
  <meta charset="UTF-8">
  <meta name="viewport" content="width=device-width, initial-scale=1.0">
  <title>Formulario de Actualización</title>
  <link rel="stylesheet" href="https://stackpath.bootstrapcdn.com/bootstrap/4.5.2/css/bootstrap.min.css">
</head>
<body>
  <div class="container mt-5">
    <div class="row justify-content-center">
      <div class="col-md-6">
        <h2 class="mb-4">Actualizar Usuario</h2>
        <?php
        // Conexión a la base de datos
        $servername = "localhost";
        $username = "usuario";
        $password = "contraseña";
        $dbname = "basedatos";

        $conn = new mysqli($servername, $username, $password, $dbname);

        // Verificar la conexión
        if ($conn->connect_error) {
            die("Error de conexión: " . $conn->connect_error);
        }

        // Obtener el ID del usuario seleccionado
        $usuario_id = $_GET['id'];

        // Consulta SQL para obtener los datos del usuario seleccionado
        $sql = "SELECT nombre, email FROM usuarios WHERE id=$usuario_id";
        $result = $conn->query($sql);

        if ($result->num_rows > 0) {
            // Mostrar el formulario de actualización con los datos del usuario
            $row = $result->fetch_assoc();
            echo "<form action='actualizar_usuario.php' method='POST'>";
            echo "<input type='hidden' name='id' value='" . $usuario_id . "'>";
            echo "<div class='form-group'>";
            echo "<label for='nombre'>Nombre:</label>";
            echo "<input type='text' class='form-control' id='nombre' name='nombre' value='" . $row["nombre"] . "' required>";
            echo "</div>";
            echo "<div class='form-group'>";
            echo "<label for='email'>Email:</label>";
            echo "<input type='email' class='form-control' id='email' name='email' value='" . $row["email"] . "' required>";
            echo "</div>";
            echo "<button type='submit' class='btn btn-primary'>Actualizar Usuario</button>";
            echo "</form>";
        } else {
            echo "No se encontró ningún usuario con el ID proporcionado.";
        }
        $conn->close();
        ?>
      </div>
    </div>
  </div>
</body>
</html>


En este ejemplo:

Utilizamos Bootstrap para el diseño y los estilos del formulario.
Conectamos a la base de datos MySQL y obtenemos el ID del usuario seleccionado de la URL utilizando $_GET.
Ejecutamos una consulta SQL para seleccionar los datos del usuario con el ID proporcionado.
Mostramos un formulario de actualización con los datos del usuario seleccionado.
Cuando se envía el formulario, los datos actualizados se envían a actualizar_usuario.php para procesar la actualización en la base de datos.

# 4. Formulario de Eliminación (Delete)

Permitir a los usuarios eliminar un registro.
No siempre se usa un formulario completo; a veces basta con un botón de "Eliminar" en la interfaz de cada registro.
Una confirmación, usualmente en forma de un modal, preguntando si el usuario está seguro de querer eliminar el registro.

Ejemplo de codigo:

<!DOCTYPE html>
<html lang="en">
<head>
  <meta charset="UTF-8">
  <meta name="viewport" content="width=device-width, initial-scale=1.0">
  <title>Formulario de Eliminación</title>
  <link rel="stylesheet" href="https://stackpath.bootstrapcdn.com/bootstrap/4.5.2/css/bootstrap.min.css">
</head>
<body>
  <div class="container mt-5">
    <div class="row justify-content-center">
      <div class="col-md-6">
        <h2 class="mb-4">Eliminar Usuario</h2>
        <?php
        // Conexión a la base de datos
        $servername = "localhost";
        $username = "usuario";
        $password = "contraseña";
        $dbname = "basedatos";

        $conn = new mysqli($servername, $username, $password, $dbname);

        // Verificar la conexión
        if ($conn->connect_error) {
            die("Error de conexión: " . $conn->connect_error);
        }

        // Obtener el ID del usuario seleccionado
        $usuario_id = $_GET['id'];

        // Consulta SQL para obtener los datos del usuario seleccionado
        $sql = "SELECT nombre, email FROM usuarios WHERE id=$usuario_id";
        $result = $conn->query($sql);

        if ($result->num_rows > 0) {
            // Mostrar los datos del usuario y el formulario de confirmación de eliminación
            $row = $result->fetch_assoc();
            echo "<p>¿Estás seguro de que deseas eliminar el usuario '" . $row["nombre"] . "'?</p>";
            echo "<form action='eliminar_usuario.php' method='POST'>";
            echo "<input type='hidden' name='id' value='" . $usuario_id . "'>";
            echo "<button type='submit' class='btn btn-danger'>Eliminar Usuario</button>";
            echo "</form>";
        } else {
            echo "No se encontró ningún usuario con el ID proporcionado.";
        }
        $conn->close();
        ?>
      </div>
    </div>
  </div>
</body>
</html>


En este ejemplo:

Utilizamos Bootstrap para el diseño y los estilos del formulario.
Conectamos a la base de datos MySQL y obtenemos el ID del usuario seleccionado de la URL utilizando $_GET.
Ejecutamos una consulta SQL para seleccionar los datos del usuario con el ID proporcionado.
Mostramos un mensaje de confirmación de eliminación junto con un formulario de eliminación.
Cuando se envía el formulario, el ID del usuario se envía a eliminar_usuario.php para procesar la eliminación en la base de datos.

---


