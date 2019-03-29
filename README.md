# Proyecto: Tienda Online de Guitarras

## Índice

- [Preámbulo](#preámbulo)
- [Resumen del proyecto](#resumen-del-proyecto)
- [Consideraciones técnicas](#consideraciones-tecnicas)
- [Descripción de alcances](#resumen-del-proyecto)

* [0. Instalación y configuraciones iniciales](#resumen-del-proyecto)
  - [Alcance 0.1 - Estructura de Carpetas](#alcances-01)
  - [Alcance 0.2 - Instalación de dependencias](#alcances-02)
  
* [1. Backend (Middlewares, Models & Routes)](#iteraciones)
  * [Alcance 1.1 - BACKEND · Creando el servidor, el archivo .env y "Middlewares"]()
  * [Alcance 1.2 - BACKEND · Creando el modelo "User"]()
  * [Alcance 1.3 - BACKEND · Registrando "users"]()
  * [Alcance 1.4 - BACKEND · Encriptando "passwords"]()
  * [Alcance 1.5 - BACKEND · Iniciando sesión con "users" y creando "tokens"]()
  * [Alcance 1.6 - BACKEND · Creando una ruta de Autenticación]()
  * [Alcance 1.7 - BACKEND · Cerrando sesión de "users"]()
  * [Alcance 1.8 - BACKEND · Creando el modelo "Brand" y sus rutas]()
  * [Alcance 1.9 - BACKEND · Creando el modelo "Woods" y sus rutas]()
  * [Alcance 1.10 - BACKEND · Agregando productos]()
  * [Alcance 1.11 - BACKEND · Obteniendo los productos por ID]()
  * [Alcance 1.12 - BACKEND · Obteniendo los productos por orden]()

* [2. Frontend (Authentication)](#iteraciones)

  * [Alcance 2.1 - FRONTEND · Configuración, dependencias y scripts]()
  * [Alcance 2.2 - FRONTEND · Creando el Header y el Footer]()
  * [Alcance 2.3 - FRONTEND · Configurando Redux]()
  * [Alcance 2.4 - FRONTEND · Agregando componente de "Registro" e "Inicio de Sesión"]()
  * [Alcance 2.5 - FRONTEND · Desarrollando el inicio de sesión]()
  * [Alcance 2.6 - FRONTEND · Desarrollando el registro]()
  * [Alcance 2.7 - FRONTEND · Creando el "dashboard"]()
  * [Alcance 2.8 - FRONTEND · Prevención de rutas]()

* [3. Frontend (Landing Page + Shop + Admin Page)](#iteraciones)

* [4. Frontend (Checkout + Payment Process)](#iteraciones)

***

## Preámbulo

![Imgur](https://i.imgur.com/XHpENHF.jpg)

La pasión de tu vida siempre ha sido la música. 

Has destacado en la industria por tus conocimientos en el mundo de las guitarras. Se te reconoce por ayudar entusiastas a elegir su primer instrumento y a los más veteranos en una más apropiada para sus necesidades. 

Además, tu trabajo principal es realizar consultorías a distribuidoras de instrumentos, mejorando su flujo de ventas en todo el país.

Por ello, después de varios años, has juntado suficiente dinero y confianza para aprovechar toda tu experiencia e invertir en crear un negocio propio.

Tomas la decisión de programar una tienda de comercio electrónico y vender guitarras con un sistema más automatizado. 

Con los conocimientos del Bootcamp de programación que terminaste hace un par de meses, afirmas que cuentas con los conocimientos suficientes para ejecutarlo.

Trazas una estrategia y planeas terminar el proyecto en 30 días.

## Resumen del proyecto

Construirás una tienda de comercio electrónico bajo el esquema MERN, en el cual se vincularán el siguiente conjunto de tecnologías:

- MongoDB
- Express
- React + Redux
- NodeJS

El proyecto estará dividido en alcances. Su intención es brindarte un camino para que lo puedas ir resolviendo paso a paso.

Recuerda que al terminar cada alcance, deberás realizar un "commit" para asegurar tu progreso dentro de tu repositorio.
 

## Consideraciones técnicas

* [NodeJS](https://nodejs.org)
* [Postman](https://www.getpostman.com/)
* [MongoDB](https://docs.mongodb.com/manual/administration/install-community/)
* [MongoDB Compass](https://www.mongodb.com/products/compass)
* [Visual Studio Code](https://code.visualstudio.com/)
* [Git](https://git-scm.com/downloads)
* ["GitHub Reposity: Projects & Issues"](https://help.github.com/en/articles/about-project-boards)


## 0. Instalación y configuraciones iniciales

## Alcance 0.1 - Estructura de Carpetas

- Inicializa tu proyecto con `npm init` y crea el archivo `package.json`
- Crea una carpeta `client` y dentro coloca un proyecto de React con `create-react-app`
- Crea una carpeta `server` y dentro coloca un archivo `server.js`. Dentro levantaremos nuestro servidor para el ambiente "Backend"
- Crea un archivo .gitignore y coloca dentro los archivos que deberemos ignorar. Te recomendamos colocar:

#### `./.gitignore`
```
/node_modules
/build
/client/node_modules

.DS_Store
.env

npm-debug.log*
yarn-debug.log*
yarn-error.log*
```

- Al finalizar la iteración, deberías tener esta estructura de carpetas:

```
|--client
|--server
|   |--server.js
|  
|--.gitignore
|--package.json
```

## Alcance 0.2 - Instalación de dependencias BACKEND

- Instala las dependencias para el proyecto:

`Servidor`
- nodemon - Herramienta para monitorear cambios en una aplicación y reiniciarla cada vez que suceda uno.
- bcrypt - Encriptación de contraseñas.
- cloudinary - Subir imágenes a plataforma de [Cloudinary](https://cloudinary.com/).
- concurrently - Levanta varias sesiones de Node.js en un sólo comando.
- cookie-parser - Mantener la sesión del usuario sobre el navegador (lado del cliente).
- dotenv - Archivo que mantiene tus datos sensibles, almacenados en `.env`, en la raiz de tu proyecto.
- express - Framework Web para crear nuestro Backend y sus derivados.
- express-formidable - Middleware de Node.js que permite convertir datos de formularios, incluyendo subida de archivos.
- jsonwebtoken -Implementación de Json Web Tokens (una manera de transmitir de forma segura información entre partes como un objeto JSON)
- moment - Convierte, valida y muestra fechas y tiempos en Javascript
- mongoose - Herramienta para modelar objetos con MongoDB
- [multer](https://www.npmjs.com/package/multer) - Middleware que permite la transmisión de formatos de datos del tipo imagen o archivos.

Verifica que estén colocadas en tu `package.json`, dentro de tus dependencias.

- Crea el script "server" dentro de tu package.json que corra `nodemon` sobre tu archivo `server.js`.

#### `./package.json`
```javascript
...
"scripts":{
    "server": "nodemon server/server.js"
  }
...
```

- Levanta el servidor

#### `./server/server.js`
```javascript
  const express = require('express')
  const app = express()
  const port = process.env.PORT || 3002
  
  app.listen(port, () => {
    console.log(`Servidor corriendo en el puerto ${port}`)
  }
  
```



## 1. BACKEND (Middlewares, Models & Routes)

En las siguientes iteraciones, trabajaremos en la carpeta "server".

## 2. FRONTEND (Authentication)

## 2. FRONTEND (Landing Page + Shop + Admin Page)

## 3. FRONTEND (Checkout + Payment Process)






