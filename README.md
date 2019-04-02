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

***

## Alcances 0 · Instalación y configuraciones iniciales

En este módulo, trabajaremos nuestra estructura de carpetas, revisaremos las dependencias que nuestro BACKEND necesita y finalmente haremos la configuración mínima para levantar el servidor en el puerto 3002.


## 0.1 - Estructura de Carpetas

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

## 0.2 - Instalación de dependencias BACKEND

- Instala las dependencias para el proyecto:

#### `Servidor`
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

- Levanta el servidor en el puerto 3002

#### `./server/server.js`
```javascript
  const express = require('express')
  const app = express()
  const port = process.env.PORT || 3002
  
  app.listen(port, () => {
    console.log(`Servidor corriendo en el puerto ${port}`)
  }
  
```

***

## Alcances 1 · BACKEND (Middlewares, Models & Routes)

Durante todo este alcance, trabajaremos dentro de la carpeta "server". Crearemos toda la estructura de nuestro Backend, así como la conexión con nuestra base de datos con MongoDB.

## 1.1 - BACKEND · Configurando el servidor, el archivo .env y "Middlewares"

- Crea un archivo .env en la raiz del proyecto y dentro agrega la línea:

```javascript
DATABASE=mongodb://localhost:27017/tiendaguitarras
```

- Para poder utilizar .env, debes de agregar esta línea en el archivo de `server.js`:

```javascript
...
require('dotenv').config()
```

- Agrega las dependencias `cookie-parser` y `mongoose` al servidor. Recuerda asignarlas a una variable `const`.

- Conéctate a tu base de datos de MongoDB a través de mongoose, bajo el nombre de "tiendaguitarras" y utilizando la variable de `env` como la dirección de conexión a la base de datos.

```javascript
...
mongoose.connect(process.env.DATABASE)
```

- Utiliza un middleware para convertir los datos que recibamos del cliente en Strings, arreglos o en JSON.

```javascript
...
app.use(express.urlencoded({extended: true}))
app.use(express.json())
```

- Utiliza un middleware para la inyección de cookies en la petición de datos desde el cliente.

```javascript
...
app.use(cookieParser())
```

Tu código final en este alcance debería ser:

```javascript
const express = require('express')
const cookieParser = require('cookie-parser')

const app = express()
const mongoose = require('mongoose')

require('dotenv').config()

mongoose.connect(process.env.DATABASE)

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

```javascript
app.post(‘/api/users/register’, ( )=> {
    res.status(200)
})
```

- Crea tu carpeta de `models` y luego agrega `user.js` dentro de la misma. Observa las diferentes propiedades que agregaremos dentro del "Schema" y sus diferentes validaciones.

*`models/user.js`*

```javascript
    const mongoose = require(‘mongoose’)
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
            type: Number
            default: 0
        },
        token: {
            type: String
        }
    })
    
    const User = mongoose.model(‘User’, userSchema)
    module.exports = { User }
```

- Una vez armado el modelo, entramos a `server.js` y lo importamos.

`./server/server.js`

```javascript

const  { User } = require(‘./models/user’)

```

***

## 1.3 - BACKEND · Registrando "users"

- Entramos a Postman. Creamos una colección llamada GUITARSHOP.

- Creamos una variable en “Settings” y agregamos un “Environment”. 

- Creamos un Key” llamado URL, y el nombre: http://localhost:3002. Todo esto con la intención de que cada vez que hagamos un request, no tengamos que reptir constantemente la URL.

- Revisamos para hacer la llamada todo lo que necesitamos. Vamos a `server.js` en el área de USERS y rutas:

```javascript
app.post(‘/api/users/register’, (req, res) => {
    const user = new User(req.body)
    user.save((err, doc) => {
        if(err) return res. json({success: false, err})
        res.status(200).json({
            success: true,
            userdata: doc
        })
    })
})
```

- Ponemos en POSTMAN, una llamada POST. Cuidar el Headers con Content-Type y application/json.

- Luego, en BODY, pasamos un objeto JSON, en raw:

```javascript
{
    “email”: “mikeœgmail.com”,
    “password”: “password123”,
    “name”: “Mike”,
    “lastname”: “Nieva"
}
```

Con esto, creamos un usuario y confirmamos que aparece el documento en la base de datos. Observa que tenemos un `_id` que pertenece a MongoDB.

- Revisamos las validaciones del Backend, si enviamos el mismo mail.

- Guardamos nuestra llamada HTTP en Postman. (POST Register User)

***

## 1.4 - BACKEND · Encriptando "passwords"

- Ahora, el password deberíamos hashearlo o encriptarlo. Lo haremos en la siguiente parte.
- Lo que vamos a hacer antes de guardar el password en base de datos, es encriptarlo.
- Vamos al modelo, de user.js

```javascript
// IMPORTACIONES
...
const bcrypt = require(‘bcrypt’)
CONST SALT_I = 10
// SCHEMA
...
// MIDDLEWARE
userSchema.pre(’save’, function(next){
    var user = this
    
    bcrypt.genSalt(SALT_I, function(err, salt){
        if(err) return next(err)
        bcrypt.hash(user.password, salt, function(err, hash){
             if(err) return next(err)
             user.password = hash
             next()           
        })
    })
})
```

- Para revisar que funciona, generemos un usuario nuevo y ahora deberemos ver el password “hasheado”.

Ahora, para evitar que si, más adelante, el usuario cambia su nombre y se vuelva a “hashear” el password porque salvó, tenemos que agregar un par de líneas más.


```javascript
userSchema.pre(’save’, function(next){
    var user = this
    if(user.isModified(‘password')){
        bcrypt.genSalt(SALT_I, function(err, salt){
            if(err) return next(err)
            bcrypt.hash(user.password, salt, function(err, hash){
                if(err) return next(err)
                user.password = hash
                next()           
            })
        })
    } else {
        next()
    }
})
```


- Revisamos en POSTMAN que sigue registrando sin problemas los usuarios

***

## 1.5 - BACKEND · Iniciando sesión con "users" y creando "tokens"

LOGIN USERS AND CREATING TOKENS

- Vamos a hacer una ruta POST en las rutas USER

```javascript
…
app.post(‘/api/users/login’, (req, res) => {
    // Find the email
        User.findOne({‘email’: req.body.email}, (err,user) => {
            if(!user) return res.json({loginSuccess: false, message: ‘Auth failed, email not found’})
            
        })
    // Grab the password and check the password

    // If everything is correct, we generate a token
})

- A partir de aquí, necesitamos bcrypt para decriptar el password. Iremos a los models, en user.js, para crear un método
que me permita extraerlo.


models/user.js
…
userSchema.methods.comparePassword = function(candidatePassword, cb){
        
}
```

- Vamos al servidor nuevamente...

```javascript
…
app.post(‘/api/users/login’, (req, res) => {
    // Find the email
        User.findOne({‘email’: req.body.email}, (err,user) => {
            if(!user) return res.json({loginSuccess: false, message: ‘Auth failed, email not found’})
            
            user.comparePassword(req.body.password, (err, isMatch) => {
              if(!isMatch) return res.json({loginSuccess: false, message: “Wrong Password"})               
              
              //
            })
        })
    // Grab the password and check the password

    // If everything is correct, we generate a token
})
```


- Ahora, ¿cómo comparamos los passwords?, regresamos a models/user.js


models/user.js

```javascript
…
userSchema.methods.comparePassword = function(candidatePassword, cb){
        bcrypt.compare(candidatePassword, this.password, this.password, function(err, isMatch){
            if(err) return cb(err)
            cb(null, isMatch)
        })    
}


- Y listo, con esto tenermos armada la función para que podamos verificar si los passwords matchean.
- Ahora bien, si matchean, lo que debe pasar es generar un token de identificación.

- Vamos a invocar una función llamada user.generateToken
…

app.post(‘/api/users/login’, (req, res) => {
    // Find the email
        User.findOne({‘email’: req.body.email}, (err,user) => {
            if(!user) return res.json({loginSuccess: false, message: ‘Auth failed, email not found’})
            
            user.comparePassword(req.body.password, (err, isMatch) => {
              if(!isMatch) return res.json({loginSuccess: false, message: “Wrong Password"})               
              user.generateToken((err, user)=> {
                    
                })
            })
        })
    // Grab the password and check the password

    // If everything is correct, we generate a token
})
```

- Y luego, vamos a declararla en nuestros models/user.js

models/user.js

```javascript
// IMPORTACIONES
const jwt = require(‘jsonwebtoken’)
…
userSchema.methods.comparePassword = function(candidatePassword, cb){
        bcrypt.compare(candidatePassword, this.password, this.password, function(err, isMatch){
            if(err) return cb(err)
            cb(null, isMatch)
        })    
}

userSchema.methods.generateToken = function(){
    var user = this
    var token = jwt.sign()
    
    // user.id + password (the password of environment, the server only know)
}
```

- Vamos a .env y vamos a crear el password para los tokens

.env

```javascript
DATABASE=…
SECRET=SUPERSECRETPASSWORD123

- Regresamos a nuestro models/user.js
models/user.js
// IMPORTACIONES
const jwt = require(‘jsonwebtoken’)
…
require(‘dotenv’).config()
…
userSchema.methods.comparePassword = function(candidatePassword, cb){
        bcrypt.compare(candidatePassword, this.password, this.password, function(err, isMatch){
            if(err) return cb(err)
            cb(null, isMatch)
        })    
}


userSchema.methods.generateToken = function(cb){
    var user = this
    var token = jwt.sign(user._id.toHexString(),process.env.SECRET)
    
    // token = user.id + password (the password of environment, the server only know)
    user.token = token
    user.save(function(err, user){
        if(err) return cb(err)        
        cb(null, user)
    })
}
```

- Listo. Ahora, regresamos a nuestro server.js

```javascript
…
app.post(‘/api/users/login’, (req, res) => {
    // Find the email
        User.findOne({‘email’: req.body.email}, (err,user) => {
            if(!user) return res.json({loginSuccess: false, message: ‘Auth failed, email not found’})
    // Grab the password and check the password
            user.comparePassword(req.body.password, (err, isMatch) => {
              if(!isMatch) return res.json({loginSuccess: false, message: “Wrong Password"})               
    // If everything is correct, we generate a token
              user.generateToken((err, user)=> {
                    if(err) return res.status(400).send(err)
                    // Si todo bien, debemos guardar este token como un “cookie”
                    res.cookie(‘w_auth’, user.token).status(200).json(
                        {loginSuccess: true}
                    )
                })
            })
        })
})
```

- Hagamos la prueba directamente en Postman, a través de raw. Le pasamos este json:

```javascript
{
    “email”: “mike@gmail.com”
    “password”: “password123"
}
```

- Prueba con un login incorrecto
- Prueba con un login correcto
- Revisa el cookie en Postman y también en el usuario loggeado.
- Finalmente, salvemos la ruta en nuestra carpeta de POSTMAN: `GET Login User`

***

## 1.6 - BACKEND · Creando una ruta de Autenticación

- Ahora vamos a crear una ruta de autenticación. Cada vez que vamos a una url distinta, constantemente estamos revisando si el usuario posee el token correcto. Podemos revisarlo directamente en la consola. Application -> Cookie.

- Lo que vamos a hacer es crear esta verificación constante. No importa que URL visitas, siempre revisaremos si tiene la cookie o no.

./server.js

```javascript
app.get(‘/api/users/auth’, (req, res) => {
            
})

Ahora, vamos a crear un middleware para hacer la revisión.
- Creamos una carpeta llamada middleware y dentro crearemos un archivo llamado auth.js

const { User } = require(‘./../models/user’)
let auth = (req, res, next) => {
        
}
module.exports = { auth }

- Regresamos a server.js. Para preparar el auth

// 2. MIDDLEWARES
const { auth } = require(‘./middleware/auth’)

…
app.get(‘/api/users/auth’, auth, (req, res) => {
            
})
```


- Volvemos a middlewares/auth. Preparamos para buscar por token la función auth.

```javascript

const { User } = require(‘./../models/user’)
let auth = (req, res, next) => {
    
//// Token
    let token = req.cookies.w_auth
    User.findByToken(token, (err, user)=> { 
        
    })

}
module.exports = { auth }
```

- Vamos al models/user.js para crear la función findByToken (porque no existe)


```javascript
…

userSchema.statics.findByToken = function(token,cb){
    var user = this
    // DECODE THE TOKEN TO CHECK IF THE TOKEN IS OK
    jwt.verify(token, process.env.SECRET, function(err, decode){
        user.findOne(“_id”: decode, “token”: token, function(err, user){
            if (err) cb(error)
            cb(null, user)
        }         
    })
}

const User = mongoose.model...
...
```


- Regresamos a ./middlewares/auth

```javascript

const { User } = require(‘./../models/user’)
let auth = (req, res, next) => {
    
//// Token
    let token = req.cookies.w_auth
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

Una vez que completamos y damos next( ), avanzamos al server.js. Ya pasó por el middleware, podemos avanzar con nuestra ruta.

```javascript
// 2. MIDDLEWARES
const { auth } = require(‘./middleware/auth’)

…
app.get(‘/api/users/auth’, auth, (req, res) => {
    res.status(200).json({
        user: req.user
        
    })
})

- Vamos a Postman para validar la llamada. Deberías recibir el usuario como tal.
GET  {{url}}/api/users/auth

=> {
        "user”: {
                “cart”: []
                ...
            }
    }
```

- Ahora, no quiero retornar toda la información. No será necesario. Sólo algunos datos. Para ello, vamos a cambiar:
Y hacemos un pequeño cambio en la ruta del register. No es necesario pasar toda la data. Quitamos esa línea

```javascript
// 2. MIDDLEWARES
const { auth } = require(‘./middleware/auth’)

…
app.get(‘/api/users/auth’, auth, (req, res) => {
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


- Hacemos la ruta y el auth.

```javascript
app.get(‘/api/user/logout’, auth, (req, res) => {
    User.findOneAndUpdate(
        {_id: req.user._id},
        {token: ‘’},
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


## 2. FRONTEND (Authentication)

## 2. FRONTEND (Landing Page + Shop + Admin Page)

## 3. FRONTEND (Checkout + Payment Process)






