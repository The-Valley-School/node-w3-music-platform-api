# WORKSHOP 3 - API de música

En este WorkShop vamos a crear una API que nos sirva para almacenar toda la información de una plataforma de música, como si de Spotify se tratase!

Aquí tienes una captura de todos los endpoints disponibles para que te hagas una idea:

![Untitled](/assets/Untitled.png)

## **ENTIDADES**

Debes crear las siguientes entidades con los datos que indicamos:

**USUARIO**

- Nombre
- Apellidos
- Email

**ARTISTA**

- Nombre
- Género
- Activo desde año
- País de origen

**CANCIÓN**

- Título
- Duración
- Año de lazamiento
- Artista (debe hacer referencia a la entidad ARTISTA)

**PLAYLIST**

- Nombre
- Canciones (debe ser una lista de referencias a la entidad CANCIÓN)
- Creador (debe ser una referencia a la referencia USUARIO)

## CRUD

Por otro lado, debes crear todas las operaciones CRUD de cada una de estas entidades, de manera que podamos crear, leer, actualizar y borrar cualquier elemento de nuestra base de datos.

## SEEDS

Recuerda también crear seeds para todas las entidades, te recomendamos que lo hagas en este orden:

1. Usuarios
2. Artistas
3. Canciones (porque necesitan artistas)
4. Playlists (porque necesitan usuario y canciones)

## **OPERACIONES ESPECIALES**

Normalmente cuando modificamos una playlist no actualizamos todas las canciones de golpe, si no que vamos añadiendo y borrando canciones una a una. Por este motivo cuando el usuario cree o modifique una playlist siempre se creará vacía y posteriormente tendrá que modificarla haciendo uso de dos endpoints custom:

POST a /playlist/id/song:

En este endpoint mandaremos en el body el ID de una canción y se deberá añadir a la playlist indicada en la ruta (ID).

Si la canción o el API no existe, debemos devolver 404, en caso de que se añada devolveremos un código 200. Si la canción ya estaba en el API devolveremos un error 409. Si no se indica el ID de la canción en el body devolveremos error 400.

DELETE a /playlist/id/song:

En este endpoint mandaremos en el body el ID de una canción y se deberá eliminar de la playlist indicada en la ruta (ID).

Si la canción o el API no existe, debemos devolver 404, en caso de que se elimine correctamente devolveremos un código 200. Si la canción no estaba en el API devolveremos un error 404. Si no se indica el ID de la canción en el body devolveremos error 400.

## OTRAS CONSIDERACIONES

- Debes desplegar el API en vercel
- Debes mantener dos BBDD: DEVELOPMENT y PRODUCTION
