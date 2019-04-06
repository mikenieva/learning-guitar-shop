# Proyecto: Tienda Online de Guitarras

## Índice

- [Preambulo](#preámbulo)
- [Resumen del proyecto](#resumen-del-proyecto)
- [Consideraciones técnicas](#consideraciones-técnicas)
- [Descripción de alcances](#resumen-del-proyecto)

***

- [0. Instalación y configuraciones iniciales](#resumen-del-proyecto)
  - [Alcance 0.1 - Estructura de Carpetas](#alcances-001)
  - [Alcance 0.2 - Instalación de dependencias](#alcances-002)
  
- [1. Backend (Middlewares, Models & Routes)](#iteraciones)
  - [Alcance 1.1 - BACKEND · Creando el servidor, el archivo .env y "Middlewares"](#alcances-101)
  - [Alcance 1.2 - BACKEND · Creando el modelo "User"](#alcances-102)
  - [Alcance 1.3 - BACKEND · Registrando "users"](#alcances-103)
  - [Alcance 1.4 - BACKEND · Encriptando "passwords"](#alcances-104)
  - [Alcance 1.5 - BACKEND · Iniciando sesión con "users" y creando "tokens"](#alcances-105)
  - [Alcance 1.6 - BACKEND · Creando una ruta de Autenticación](#alcances-106)
  - [Alcance 1.7 - BACKEND · Cerrando sesión de "users"](#alcances-107)
  - [Alcance 1.8 - BACKEND · Creando el modelo "Brand" y sus rutas](#alcances-108)
  - [Alcance 1.9 - BACKEND · Creando el modelo "Woods" y sus rutas](#alcances-109)
  - [Alcance 1.10 - BACKEND · Agregando productos](#alcances-110)
  - [Alcance 1.11 - BACKEND · Obteniendo los productos por ID](#alcances-111)
  - [Alcance 1.11 - BACKEND · Obteniendo los productos ordenados por creación y los más vendidos](#alcances-112)

- [2. Frontend (Authentication)](#iteraciones)
  - [Alcance 2.1 - FRONTEND · Configuración, dependencias y scripts](#alcances-121)
  - [Alcance 2.2 - FRONTEND · Creando el Header y el Footer](#alcances-122)
  - [Alcance 2.3 - FRONTEND · Configurando Redux](#alcances-123)
  - [Alcance 2.4 - FRONTEND · Agregando componente de "Registro" e "Inicio de Sesión"](#alcances-124)
  - [Alcance 2.5 - FRONTEND · Desarrollando el inicio de sesión](#alcances-125)
  - [Alcance 2.6 - FRONTEND · Desarrollando el registro](#alcances-126)
  - [Alcance 2.7 - FRONTEND · Creando el "dashboard"](#alcances-127)
  - [Alcance 2.8 - FRONTEND · Prevención de rutas](#alcances-128)

- [3. Frontend (Landing Page + Shop + Admin Page)](#iteraciones)

- [4. Frontend (Checkout + Payment Process)](#iteraciones)

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

- [NodeJS](https://nodejs.org)
- [Postman](https://www.getpostman.com/)
- [MongoDB](https://docs.mongodb.com/manual/administration/install-community/)
- [MongoDB Compass](https://www.mongodb.com/products/compass)
- [Visual Studio Code](https://code.visualstudio.com/)
- [Git](https://git-scm.com/downloads)
- [GitHub Reposity: Projects & Issues](https://help.github.com/en/articles/about-project-boards)

***

## Alcances 0 · Instalación y configuraciones iniciales

En este módulo, trabajaremos nuestra estructura de carpetas, revisaremos las dependencias que nuestro BACKEND necesita y finalmente haremos la configuración mínima para levantar el servidor en el puerto 3002.

## 0.1 - Estructura de Carpetas

- Inicializa tu proyecto con `npm init` y crea el archivo `package.json`
- Crea una carpeta `client` y dentro coloca un proyecto de React con `create-react-app`
- Crea una carpeta `server` y dentro coloca un archivo `server.js`. Dentro levantaremos nuestro servidor para el ambiente "Backend"
- Crea un archivo .gitignore y coloca dentro los archivos que deberemos ignorar. Te recomendamos colocar:

**`./.gitignore`**

```javascript
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

```shell
|-- client
|-- server
|   |-- server.js
|  
|-- .gitignore
|-- package.json
```

## 0.2 - Instalación de dependencias BACKEND

- Instala las dependencias para el proyecto:

### `Servidor`

- [nodemon](https://www.npmjs.com/package/nodemon) - Herramienta para monitorear cambios en una aplicación y reiniciarla cada vez que suceda uno.
- [bcrypt](https://www.npmjs.com/package/bcrypt) - Encriptación de contraseñas.
- [cloudinary](https://www.npmjs.com/package/cloudinary) - Subir imágenes a plataforma de [Cloudinary](https://cloudinary.com/).
- [concurrently](https://www.npmjs.com/package/concurrently) - Levanta varias sesiones de Node.js en un sólo comando.
- [cookie-parser](https://www.npmjs.com/package/cookie-parser) - Mantener la sesión del usuario sobre el navegador (lado del cliente).
- [dotenv](https://www.npmjs.com/package/dotenv) - Archivo que mantiene tus datos sensibles, almacenados en `.env`, en la raiz de tu proyecto.
- [express](https://www.npmjs.com/package/express) - Framework Web para crear nuestro Backend y sus derivados.
- [express-formidable](https://www.npmjs.com/package/express-formidable) - Middleware de Node.js que permite convertir datos de formularios, incluyendo subida de archivos.
- [jsonwebtoken](https://www.npmjs.com/package/jsonwebtoken) -Implementación de Json Web Tokens (una manera de transmitir de forma segura información entre partes como un objeto JSON)
- [moment](https://www.npmjs.com/package/moment) - Convierte, valida y muestra fechas y tiempos en Javascript
- [mongoose](https://www.npmjs.com/package/mongoose) - Herramienta para modelar objetos con MongoDB
- [multer](https://www.npmjs.com/package/multer) - Middleware que permite la transmisión de formatos de datos del tipo imagen o archivos.

Verifica que estén colocadas en tu `package.json`, dentro de tus dependencias.

- Crea el script "server" dentro de tu package.json que corra `nodemon` sobre tu archivo `server.js`.

**`./package.json`**

```javascript
...
"scripts":{
    "server": "nodemon server/server.js"
  }
...
```

- Levanta el servidor en el puerto 3002

**`./server/server.js`**

```javascript
  const express = require('express')
  const app = express()
  const port = process.env.PORT || 3002
  
  app.listen(port, () => {
    console.log(`Servidor corriendo en el puerto ${port}`)
  })
  
```

***

## Alcances 1 · BACKEND (Middlewares, Models & Routes)

Durante todo este alcance, trabajaremos dentro de la carpeta "server". Crearemos toda la estructura de nuestro Backend, así como la conexión con nuestra base de datos con MongoDB.

## 1.1 - BACKEND · Configurando el servidor, el archivo .env y "Middlewares"

- Crea un archivo .env en la raiz del proyecto y dentro agrega la línea:

**`./.env`**

```javascript
DATABASE=mongodb://localhost:27017/tiendaguitarras
```

- Para poder utilizar .env, debes de agregar esta línea en el archivo de `server.js`:

**`./server/server.js`**

```javascript
...
require('dotenv').config()
```

- Agrega las dependencias `cookie-parser` y `mongoose` al servidor. Recuerda asignarlas a una variable `const`.

- Conéctate a tu base de datos de MongoDB a través de mongoose, bajo el nombre de "tiendaguitarras" y utilizando la variable de `env` como la dirección de conexión a la base de datos.

**`./server/server.js`**

```javascript
...
mongoose.connect(process.env.DATABASE, { useNewUrlParser: true }, (err) => {
    if(err) return err
    console.log("Conectado a MongoDB")
})
```

- Utiliza un middleware para convertir los datos que recibamos del cliente en Strings, arreglos o en JSON.

**`./server/server.js`**

```javascript
...
app.use(express.urlencoded({extended: true}))
app.use(express.json())
```

- Agregaremos uno más para gestionar las 'cookies' en la petición de datos desde el cliente.

**`./server/server.js`**

```javascript
...
app.use(cookieParser())
```

Tu código final en este alcance debería ser:

**`./server/server.js`**

```javascript
const express = require('express')
const cookieParser = require('cookie-parser')

const app = express()
const mongoose = require('mongoose')

require('dotenv').config()

mongoose.connect(process.env.DATABASE, { useNewUrlParser: true }, , (err) => {
    if(err) return err
    console.log("Conectado a MongoDB")
})

app.use(express.urlencoded({extended: true}))
app.use(express.json())
app.use(cookieParser())

const port = process.env.PORT || 3002

app.listen(port, () => {
  console.log(`Servidor corriendo en puerto ${port}`)
})

```

***

## 1.2 - BACKEND · Creando el modelo "User"

En este alcance, crearemos el modelo "User", el cual estará referido a los usuarios de nuestra aplicación.

- Crea el apartado de rutas “USERS” en `server.js` 

**`./server/server.js`**

```javascript
app.post('/api/users/register', (req, res)=> {
    res.status(200).send('Funciona la conexión')
})
```

- Crea tu carpeta de `models` y luego agrega `user.js` dentro de la misma. Observa las diferentes propiedades que agregaremos dentro del "Schema" y sus diferentes validaciones.

**`./server/models/user.js`**

```javascript

    const mongoose = require('mongoose')

    const userSchema = mongoose.Schema({
        email: {
            type: String,
            required: true,
            trim: true,
            unique: 1
        },
        password: {
            type: String,
            required: true,
            minlength: 5
        },
        name: {
            type: String,
            required: true,
            maxlength: 100
        },
        lastname: {
            type: String,
            required: true,
            maxlength: 100
        },
        cart: {
            type: Array,
            default: []
        },
        history:{
            type: Array,
            default:[]
        },
        role: {
            type: Number,
            default: 0
        },
        token: {
            type: String
        }
    })

    const User = mongoose.model('User', userSchema, "users")

    module.exports = { User }

```

- Una vez armado el modelo, entramos a `server.js` y lo importamos.

**`./server/server.js`**

```javascript

const  { User } = require('./models/user')

```

***

## 1.3 - BACKEND · Registrando "users"

- Entramos a Postman. Creamos una colección llamada GUITARSHOP.

- Creamos una variable en “Settings” y agregamos un “Environment”. 

- Creamos un "Key" llamado URL, y el nombre: `http://localhost:3002`. Todo esto con la intención de que cada vez que hagamos un request, no tengamos que reptir constantemente la URL. Confirmamos haciendo una llamada HTTP nuevamente.

- Vamos a `server.js`, en las rutas de `USERS`:

**`./server/server.js`**

```javascript

app.post('/api/users/register', (req, res) => {
    const user = new User(req.body)
    user.save((err, doc) => {
        if(err) return res.json({success: false, err})
        res.status(200).json({
            success: true,
            userdata: doc
        })
    })
})

```

- Ponemos en POSTMAN, una llamada POST. Cuidar el HEADERS agregando el correcto `Content-Type` y `application/json`.

- Luego, en BODY, pasamos un objeto JSON, con la opción 'raw':

```javascript
{
    "email": "mikenieva@gmail.com",
    "password": "password123",
    "name": "Mike",
    "lastname": "Nieva"
}
```

Con esto, creamos un usuario y confirmamos que aparece el documento en la base de datos. Observa que tenemos un `_id` que pertenece a MongoDB.

- Revisamos las validaciones del Backend, si enviamos el mismo mail.

- Guardamos nuestra llamada HTTP en Postman. (POST Register User)

***

## 1.4 - BACKEND · Encriptando "passwords"

- Ahora, el password deberíamos hashearlo o encriptarlo. Lo haremos en la siguiente parte. Lo que debemos hacer antes de guardar el password en base de datos es encriptarlo, para mantener la seguridad del mismo.

- Utilizaremos `.pre` dentro del modelo `user.js`

Lo que realiza este método es ejecutar antes del `.save()` sentencias que tú necesites realizar. Funciona como middleware.

Esto significa que antes de inyectar el password a la base de datos, primero lo encriptará y después lo pasará a la ruta que tenemos en `server.js`

Como dato adicional, observamos que tenemos un `this.isModified`. Esta línea implica que sólo hará la encriptación del password cuando estemos creando el usuario por primera vez o, estemos modificando literalmente el password. 

En caso de que no esté siendo modificado, entonces, no es necesario volver a hacer la encriptación.

**`./server/models/user.js`**

```javascript

// IMPORTACIONES
...
const bcrypt = require('bcrypt')
const SALT_I = 10

// SCHEMA
...

// MIDDLEWARE
userSchema.pre('save', async function (next){
    if(this.isModified('password')){
        try {
            const salt = await bcrypt.genSalt(SALT_I)
            const hash = await bcrypt.hash(this.password, salt)
            this.password = hash;
            next();
        } catch(err){
            return next(err);
        }
    }
})

```

- Para revisar que funciona, generemos un usuario nuevo y ahora deberemos ver el password en modo "hash" o mejor dicho, encriptado.

***

## 1.5 - BACKEND · Iniciando sesión con "users" y creando "tokens"

- Vamos a hacer una ruta POST para USER.

Para poder realizar el login, debemos lograr 3 objetivos:

1. Encontrar el correo dentro de la base de datos.
2. Obtener el password y revisar que el que se está enviando es el mismo que el que tenemos en base de datos.
3. Finalmente, generar un "token", el cual es un "string" largo que se guarda en el navegador para asegurar que tienes una sesión y no tengas que hacer login a cada momento que te mueves en la página.

Vayamos por partes. Encontremos el password.

Observemos que si no encuentra un usuario, entonces devolvemos un mensaje sobre el email no hallado.

**`./server/server.js`**

```javascript
…

app.post('/api/users/login', (req, res) => {
    // 1. Encuentra el correo
        User.findOne({'email': req.body.email}, (err,user) => {
            if(!user) return res.json({loginSuccess: false, message: 'Auth fallida, email no encontrado'})

        })

    // 2. Obtén el password y compruébalo

    // 3. Si todo es correcto, genera un token
})

```

Ahora, necesitaremos obtener ambos passwords y luego compararlos para saber si son los mismos.

Iremos a los `models`, en `user.js`, para crear un método que me permita realizar una comparativa. 

 `userSchema.methods.comparePassword`. Significa que estamos extendiendo una función a nuestro `Schema` para que los podamos ejecutar en la llamada desde `server.js`.

**`./server/models/user.js`**

```javascript
…

userSchema.methods.comparePassword = function(candidatePassword, cb){

}

```

Aún no tiene nada, pero está bien.

Regresamos a server.js para construir el segundo paso.

Observa que le estamos pasando como primer argumento el password que obtenemos de la llamada y en el segundo argumento hay un callback.

`isMatch` es un booleano que me determina si los passwords coinciden o no coinciden. En caso de que no coincidan o sea falso esto (!match), entonces pediremos que regrese un mensaje de password erróneo.

**`./server/server.js`**

```javascript
…
app.post('/api/users/login', (req, res) => {
    // 1. Encuentra el correo
        User.findOne({'email': req.body.email}, (err,user) => {
            if(!user) return res.json({loginSuccess: false, message: 'Auth fallida, email no encontrado'})
    // 2. Obtén el password y compruébalo
            user.comparePassword(req.body.password, (err, isMatch) => {
              if(!isMatch) return res.json({loginSuccess: false, message: "Password erróneo"})

    // 3. Si todo es correcto, genera un token

            })
        })
})
```

Regresamos al models/user.js para construir, ahora si, la función de `comparePassword`.

> Si quieres aprender más sobre los "methods" en `mongoose`, puedes leer más [aquí](https://mongoosejs.com/docs/2.7.x/docs/methods-statics.html).

Observa que estamos usando dos parámetros:

`candidatePassword`será el password que reciba de la llamada
`cb` es una función. ¿Cuál? La que dictemos en la llamada. Un callback, simplemente.

Al iniciar la función, usamos bcrypt para comparar el `candidatePassword` (el password de la llamada) con el de la base de datos (`this.password`).

Sea cual sea el resultado, efectuamos el callback y le pasamos el error si no coincidió, ó, si coincidió, un null como primer argumento y el isMatch como segundo, que indicaría que fue un `true`.

**`./server/models/user.js`**

```javascript
…
userSchema.methods.comparePassword = function(candidatePassword, cb){
        bcrypt.compare(candidatePassword, this.password, function(err, isMatch){
            if(err) return cb(err)
            cb(null, isMatch)
        })
}
```

Y listo, con esto tenemos armada una función que permite verificar si las contraseñas coinciden.

Como última parte, vamos a invocar una función llamada `user.generateToken`, el cual deberá inyectar el token al cliente a través de una 'cookie'.

**`./server/server.js`**

```javascript
…

app.post('/api/users/login', (req, res) => {
    // 1. Encuentra el correo
        User.findOne({'email': req.body.email}, (err,user) => {
            if(!user) return res.json({loginSuccess: false, message: 'Auth fallida, email no encontrado'})

    // 2. Obtén el password y compruébalo
            user.comparePassword(req.body.password, (err, isMatch) => {
              if(!isMatch) return res.json({loginSuccess: false, message: "Wrong Password"})

    // 3. Si todo es correcto, genera un token
              user.generateToken((err, user)=> {

                })
            })
        })

})
```

- Al igual que `comparePassword`, vamos a crear una función que me permita generar el token y posteriormente inyectarlo.

Para lograrlo, necesitamos la dependencia `jwt`. Una implementación para manejar JSON Web Tokens.

Luego, llamamos el método `generateToken` y observa que utilizaremos una función asíncrona y pasaremos un callback como parámetro `cb`.

Obtenemos el token a través de invocar jwt.sign() y le pasamos como argumento el `_id` del documento en cuestión que estamos trabajando y lo convertimos en String porque está en formato "Object_id" desde MongoDB. Como segundo argumento, pasamos un password que sólo tendrá el servidor, guardado en `process.env.SECRET`.

Recuerda que para poder utilizar las variables de `process.env` es importante importar e invocar `require('dotenv').config()`.

El token obtenido lo guardamos dentro del usuario respectivo a través de `this.token`

Finalmente, ejecutamos `this.save` para inyectar el dato en base de datos y si hay un error retornar el callback con el error. En caso de que todo bien, retornar el callback pero con un primer argumento `null` (porque no hay error) y en segundo argumento con los datos del usuario.

**`./server/models/user.js`**

```javascript
// IMPORTACIONES
const jwt = require(‘jsonwebtoken’)
…
require('dotenv').config()
…

userSchema.methods.comparePassword = function(candidatePassword, cb){
        bcrypt.compare(candidatePassword, this.password, function(err, isMatch){
            if(err) return cb(err)
            cb(null, isMatch)
        })
}

userSchema.methods.generateToken = async function(cb){

    const token = await jwt.sign(this._id.toHexString(),process.env.SECRET)

    this.token = token
    this.save((err, user) => {
        if(err) return cb(err)
        cb(null, user)
    })
}

```

Creamos el `SECRET` en `.env`.

**`./.env`**

```javascript
DATABASE=…
SECRET=PASSWORDSECRETO123
```

- Listo. Terminemos la función en `server.js`:

**`./server/server.js`**

```javascript
…
app.post('/api/users/login', (req, res) => {
    // 1. Encuentra el correo
        User.findOne({'email': req.body.email}, (err,user) => {
            if(!user) return res.json({loginSuccess: false, message: 'Auth fallida, email no encontrado'})

    // 2. Obtén el password y compruébalo

            user.comparePassword(req.body.password, (err, isMatch) => {
              if(!isMatch) return res.json({loginSuccess: false, message: "Wrong Password"})

    // 3. Si todo es correcto, genera un token

              user.generateToken((err, user)=> {
                    if(err) return res.status(400).send(err)
                    // Si todo bien, debemos guardar este token como un "cookie"
                    res.cookie('guitarshop_auth', user.token).status(200).json(
                        {loginSuccess: true}
                    )
                })
            })
        })
})
```

- Hagamos la prueba directamente en Postman con la ruta. Pasamos este JSON:

```javascript
{
    "email": "mike@gmail.com",
    "password": "password123"
}
```

- Si te retorna exitoso, todo excelente. Estamos con una sesión activa. Revisa el cookie en Postman.
  
- Haz una prueba con un password incorrecto para verificar que todo es correcto.

- Finalmente, salvemos la ruta en nuestra carpeta de POSTMAN: `POST Login User`

***

## 1.6 - BACKEND · Creando una ruta de Autenticación

- Ahora vamos a crear una ruta de autenticación. 
  
  Cada vez que vamos a una url distinta dentro de la misma aplicación, constantemente estaremos revisando si el usuario esta con sesión activa o no (con login).
  
  Podemos revisar esto directamente en la consola. Application -> Cookie.

  Si la 'Cookie' existe, excelente, hay una sesión. Si no hay una 'Cookie' entonces pedimos realizar 'login' o registrarse como usuario.

- Lo que vamos a hacer es crear esta verificación constante. No importa que URL visitas, siempre deberíamos revisar. Empezamos con la ruta:

**`./server/server.js`**

```javascript
app.get('/api/users/auth', (req, res) => {

})
```

- Ahora, vamos a crear un middleware para hacer la revisión. Creamos una carpeta llamada `middleware` y dentro crearemos un archivo llamado auth.js

**`./server/middleware/auth.js`**

```javascript

const { User } = require('./../models/user')
let auth = (req, res, next) => {

}
module.exports = { auth }

```

- Regresamos a `server.js`. Importamos `auth` y lo asignamos dentro de la ruta. Observa que se pone entre `'/api/users/auth'` y `(req,res) => ...`.
  
  Esto significa que una vez tocada la ruta, debería pasar siempre por `auth` primero.

**`./server/server.js`**

```javascript

const { auth } = require('./middleware/auth')

…

app.get('/api/users/auth', auth, (req, res) => {

})
```

- Una vez colocado esto, vamos nuevamente a `middleware/auth`.
  
  El objetivo es armar la función para obtener el token que viene de la petición del cliente.

  Una vez capturado, vamos a realizar una búsqueda por token en base de datos. Invocaremos una función (aún no declarada) llamada `.findByToken()`. Debería retornar un usuario.

**`./server/middleware/auth.js`**

```javascript

const { User } = require('./../models/user')

let auth = (req, res, next) => {

    let token = req.cookies.guitarshop_auth
    User.findByToken(token, (err, user)=> {

    })
}

module.exports = { auth }
```

- Ya hecho esto, declaramos la función de `.findByToken()`.
  
  Regresamos a `user.js` y observemos las diferentes sentencias.

**`./server/models/user.js`**

```javascript
…

userSchema.statics.findByToken = function(token,cb){
    var user = this

    jwt.verify(token, process.env.SECRET, function(err, decode){
        user.findOne({"_id": decode, "token": token}, function(err, user){
            if (err) cb(error)
            cb(null, user)
        }
    })
}

...
```

- Regresamos a nuestro servidor para ejecutar `.findByToken`.

**`./server/middleware/auth.js`**

```javascript

const { User } = require('./../models/user')
let auth = (req, res, next) => {

    let token = req.cookies.guitarshop_auth

    User.findByToken(token, (err, user)=> { 
        if(err) throw err
        if(!user) return res.json({
            isAuth: false,
            error: true
        })
        req.token = token;
        req.user = user;
        next()
    })

}
module.exports = { auth }
```

Una vez que completamos y damos next(), avanzamos al server.js. Ya pasó por el middleware, podemos avanzar con nuestra ruta.

**`./server/server.js`**

```javascript
// 2. MIDDLEWARES
const { auth } = require('./middleware/auth')

…
app.get('/api/users/auth', auth, (req, res) => {
    res.status(200).json({
        user: req.user

    })
})
```

- Vamos a Postman para validar la llamada. Deberías recibir el usuario como tal.

`GET  {{url}}/api/users/auth`

```javascript
{
  "user": {
    "cart": []
    ...
    }
}
```

- Finalmente, terminamos la ruta y hacemos un pequeño cambio en la ruta del register. No es necesario pasar toda la data.

**`./server/server.js`**

```javascript
// 2. MIDDLEWARES
const { auth } = require(‘./middleware/auth’)

…
app.get('/api/users/auth', auth, (req, res) => {
    res.status(200).json({
        isAdmin: req.user.role === 0 ? false : true,
        isAuth: true,
        email: req.user.email,
        name: req.user.name,
        lastname: req.user.lastname,
        role: req.user.role,
        cart: req.user.cart,
        history: req.user.history
    })
})

app.post( …

        res.status(200).json({
        success: true
    })
...

- Guarda tu ruta en POSTMAN. -> AUTH

```

***


## 1.7 - BACKEND · Cerrando sesión de "users"


- Hacemos la ruta y recuerda pasar `auth` como middleware.

**`./server/server.js`**

```javascript
app.get('/api/user/logout', auth, (req, res) => {
    User.findOneAndUpdate(
        {_id: req.user._id},
        {token: ''},
        (err, doc) => {
            if(err) return res.json({success: false, err})
            return res.status(200).json({
                success: true
            })
        }
    )
})
```

- Y eso es todo. Borramos el token cuando tocamos esa ruta.
- Y recuerda guardar tu ruta en POSTMAN.

***

## 1.8 - BACKEND · Creando el modelo "Brand" y sus rutas

- Vamos a crear un modelo llamado `brand.js`

- La ruta deberá ser en:

**`./server/server.js`**

```javascript
app.post('/api/product/brand', auth, (req, res) => {
    
})
```

- Entramos al archivo `models/brand.js` y creamos toda la estructura:

**`./server/models/brand.js`**

```javascript
./server/models/brand.js
const mongoose = require(‘mongoose’)
const brandSchema = mongoose.Schema({
    name: {
        required: true,
        type: String,
        unique: 1,
        maxlength: 100
    }
    
})


const Brand = mongoose.model(‘Brand’, brandSchema)
module.exports = { Brand }
```

- Regresamos a `server.js` para crear la ruta.

**`./server/server.js`**

```javascript
const { Brand } = require(‘./models/brand’)
app.post(‘/api/product/brand’, auth, (req, res) => {
    const brand = new Brand(req.body)
    brand.save((err, doc) => {
        if(err) return res.json({success: false, err})
        res.status(200).json({
            success: true,
            brand: doc
        })
    })
})
```
- Desde POSTMAN, crearemos una carpeta dentro de GUITARSHOP para BRANDS. 

- Desde POSTMAN, movemos todas las que habíamos creado anteriormente a una nueva carpeta llamada USERS.

- Y ahora, creamos una marca con POSTMAN. Hacemos una llamada HTTP:

`POST {{URL}}/api/product/brand`

```javascript
{
    "name": "Ibanez"
}
```

Revisamos y confirmamos que se haya creado. 

- Ahora, podrás notar que, para poder crear "Brands", puede hacerlo cualquier usuario, mientras tenga una sesión iniciada. Lo que debemos hacer es permitir **sólo** a los que tengan rol de admin (role: 1) que puedan subir cambios.

- Tendremos que crear un middleware que permita saber si es `admin` ese usuario. Agregamos la función `admin` dentro de la ruta. Obsserva que se coloca después de `auth`.


**`./server/server.js`**

```javascript
app.post(‘/api/product/brand’, auth, admin, (req, res) => …
```

- Ahora vamos a ./server/middleware/admin.js

**`./server/middleware/admin.js`**

```javascript
let admin = (req, res, next) => {
    if(req.user.role === 0){
        return res.send('No eres un administrador')
    }
    next()
}
module.exports = { admin } 
```

- Regresamos a importar el middleware:

**`./server/server.js`**

```javascript
const { auth } = require('./middleware/admin')
```

- Volvemos a hacer el POST en Postman y nos daremos cuenta que no te va a permitir porque no eres un administrador.

- Si hacemos el cambio de rol a un usuario, hacemos login con ese mismo y ejecutamos la llamada, entonces sí sucederá. Compruébalo.

- Ahora, obtengamos todas las marcas. Creamos la ruta.

**`./server/server.js`**

```javascript
app.get(‘/api/product/brands’, (req, res) => {
    Brand.find({}, (err, brands) => { 
        if(err) return res.status(400).send(err)
        res.status(200).send(brands)
    })
})
```

- Salvemos nuestra llamada HTTP en Postman y la comprobamos.

- Como último movimiento, vamos a agregar diferentes BRANDS para llenar la base de datos. Crea un JSON en el cual incluyas estas 9 marcas de guitarras:

    · Fender
    · Ibanez
    · Charvel    
    · Jackson
    · Gibson
    · Cort   
    · Schecter
    · Reverend
    · Ernie ball
    
Luego, importa ese JSON desde terminal hacia tu base de datos:

```shell
$ mongoimport --db tiendaguitarras --collection brands --file brands.json --jsonArray 
```

***

## 1.9 - BACKEND · Creando el modelo "Woods" y sus rutas

- Creamos la ruta para crear “WOOD". El tipo de madera que será la guitarra.

```javascript
app.post(‘/api/product/wood’, auth, admin, ( ) => { 
})
```

- Creamos el modelo `wood.js`

```javascript
const mongoose = require(‘mongoose’)
const woodSchema = mongoose.Schema({
    name: {
        required: true,
        type: String,
        unique: 1,
        maxlength: 100
    }
})
const Wood = mongoose.model(‘Wood’, woodSchema, “woods”)
module.exports = { Wood }
```

- Regresamos a nuestra `server.js`para crear las rutas. Generaremos dos. Una para crear un WOOD y otro para obtener todos los WOODS que tenemos en base de datos.

```javascript
const { Wood } = require(‘./models/wood’)

app.post(‘/api/product/wood’, auth, admin, (req,res)=>{
    const wood = new Wood(req.body)
    wood.save((err,doc) => {
        if(err) return res.json({success: false, err})
        res.status(200).json({
            success: true,
            wood: doc
        })
    })
})

app.get(‘/api/product/woods’, (req, res) => {
    Wood.find({}, (err, woods) => {
        if(err) return res.status(400).send(err)
        res.status(200).send(woods)
    }) 
})

```

- Probamos ambas rutas. Y verificamos que funcionen.

- Finalmente, crea 3 woods con estos nombres:

```javascript
{
    "name": "Alder"
}
{
    "name": "Mahogany"
}
{
    "name": "Basswood"
}
```

- Recuerda guardar tus nuevas rutas en las carpetas de POSTMAN.

***

## 1.10 - BACKEND · Agregando productos


- Ahora vamos a crear los productos de la tienda electrónica. Básicamente, `products`significarán las guitarras.

- Vamos a crear el modelo `product.js`

- Dentro, vamos a crear la estructura. Te pido que mientras generamos el código, observes un par de detalles:

  - Observar que en "Brand", vamos a realizar un concepto llamado relación. El "Product" contendrá el modelo "brand". La razón es porque si llegamos a cambiar datos de "brand" a futuro, no habría problema en "Product" porque los cambios están sucediendo independientemente.

  - Otra cosa a notar es que colocamos en la parte superior "mongoose.Schema".

  - El "ref" significa la colección que nosotros vamos a jalar. El modelo en singular, en "String".

  - Observar que agregamos "Timestamps" para que recuerda su fecha de creación.

**`./server/models/product.js`**

```javascript
const mongoose = require(‘mongoose’)
const Schema = mongoose.Schema;
const productSchema = mongoose.Schema({
    name: {
        required: true,
        type: String,
        unique: 1,
        maxlength: 100
    },
    description: {
        required: true,
        type: String,
        maxlength: 100000
    },
    price: {
        required: true,
        type: Number,
        maxlength: 255
    },
    brand: {
        type: Schema.Types.ObjectId,
        ref: ‘Brand’,
        required: true
    },
    shipping: {
        required: true,
        type: Boolean
    },
    available: {
        required: true,
        type: Boolean
    },
    wood: {
        type: Schema.Types.ObjectId,
        ref: ‘Wood’,
        required: true   
    },
    frets: {
        required: true,
        type: Number
    },
    sold: {
        type: Number,
        maxlength: 100,
        default: 0
    },
    publish: {
        required: true,
        type: Boolean
    },
    images: {
        type: Array,
        default: []
    }
}, {timestamps: true})

const Product = mongoose.model(“Product”, productSchema, “products”)
module.exports = { Product }

```

- Regresamos a `server.js` y creamos la ruta de creación del producto.

```javascript
const { Product } = require(‘./models/product’)
app.post(‘/api/product/article’, auth, admin, (req, res) => {
        const product = new Product(req.body)
        
        product.save((err, doc) => {
            if(err) return res.json({success: false, err})
            res.status(200).json({
                success: true,
                article: doc
            })
    })
})
```

- Revisamos en POSTMAN la url y crearemos un producto de ejemplo. 

  - **DETALLE IMPORTANTE:**  Observa el brand y el wood. Debemos de pasarle el "ObjectId" que tenemos con un documento "brand" para relacionarlo. También con "wood".

{
    "name": "A22402",
    "description": "Gran guitarra",
    "price": "2000",
    "brand": "5b2c11d2d37177aedfd6d962",
    "shipping": true,
    "available": true,
    "wood": "5b2c1264d37177aedfd6d964",
    "frets": 24,
    "publish": true
}

- Lo revisamos y debes obtener la respuesta. Observa tambiénq que ya te aparece "createdAt" y "updatedAt"

- Y en Brand y Wood te aparece, dentro de MongoDB Compass, “ObjectId(“...")"

- Recuerda salvar tu HTTP Request de Postman.

- Crea 5 productos, mezclando el brand y el wood.

***





- Vamos a obtener los productos a través del ID. Creamos la ruta.

Quiero ser capaz de que busque un ID o muchos IDs.querystring


Si el type está igualado a array, significa que debe buscar un arreglo de productos. Si tiene “single”, entonces estamos buscando un single id.

```javascript

// 1 id
/api/product/article?id=HSKKKSKS&type=array
// más de 1 id
/api/product/article?id=HSKKKSKS,akdjfañjf,kdjfalkñfja&type=dhjfljakhdf

app.get(‘/api/product/articles_by_id’, ( req, res ) => {
    let type = req.query.type
    let items = req.query.id
    
    if(type === “array”){
        let ids = req.query.id.split(‘,’)
        items = []
        items = ids.map(item => { 
            // Convertirlos en ObjectId de Mongoose
            return mongoose.Types.ObjectId(item)
        })
    }
    Product.
    find({ ‘_id': {$in:items}})
    .populate(‘brand’)
    .populate(‘wood’)
    .exec((err, docs)=> {
        return res.status(200).send(docs)
    })
})
```

- Vamos a Postman para probar la ruta. Recuerda pasar:

`{{url}}/api/product/articles_by_id?id=2345678,761372893,y1232131&type=array`

Lo que regresa es un arreglo de objectos. Cada objeto es un documento.

- Observa que estamos pasando un .populate. Lo que hace es que te permite obtener el desglose de Brand y Wood y no sólo el ObjectId. Con esto ya tenemos una relación mostrada en MongoDB Compass.

——

## 1.11 - BACKEND · Obteniendo los productos por creados y los más vendidos

- Creamos una ruta para "products". Observemos que utilizaremos un "query string" para pasarle qué tipo de variable queremos. Si buscamos obtener una lista de productos ordenados por creación o cuáles fueorn las guitarras más vendidas.

```javascript
// BY ARRIVAL (Más nuevas)
/articles?sortBy=createdAt&order=desc&limit=4

// BY SELL (Más Ventas)
/articles?sortBy=sold&order=desc&limit=4

app.get(‘/api/product/articles’, (req, res) => {
    let order = req.query.order ? req.query.order : ‘asc’
    let sortBy = req.query.sortBy ? req.query.sortBy : ‘_id’
    let limit = req.query.limit ? parseInt(req.query.limit) : 100
    
    Product
    .find()
    .populate(‘brand’)
    .populate(‘wood’)    
    .sort([[sortBy, order]])
    .limit(limit)
    .exec((err, articles) => {
        if(err) return res.status(400).send(err)
        res.send(articles)
    })
})
```

***




## 2. FRONTEND (Authentication)

## 2. FRONTEND (Landing Page + Shop + Admin Page)

## 3. FRONTEND (Checkout + Payment Process)






****
