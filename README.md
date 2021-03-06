<p align='center'>
    <img alt="ecommerce" style="border-radius:5px" src='./img/home.png' </img>
</p>

# GardenRy

## Proyecto

- App construida con JavaScript desde cero.
- Usando buenas prácticas,  Metodologías Ágiles y  en equipo.


## Arrancando

El proyecto cuenta con dos carpetas: `api` y `client`. En estas carpetas estará el código del back-end y el front-end respectivamente.


__API:__

En `api` vas a tener que crear un archivo llamado: `.env` que tenga la siguiente forma:

```
DB_USER=xxxxxxxxx
DB_PASSWORD=xxxxxxxxx
DB_HOST=xxxxxxxxx
GOOGLE_CLIENT_ID= xxxxxxx
GOOGLE_CLIENT_SECRET=xxxxxxxx
FACEBOOK_APP_ID=xxxxxxxx
FACEBOOK_APP_SECRET=xxxxxxxx
MAILGUN_API_KEY=xxxxxxxxx
MAILGUN_DOMAIN=xxxxxxxxx
MELI_PUBLIC_KEY=xxxxxxxxx
MELI_ACCESS_TOKEN=xxxxxxxxx
CALLBACK_URL_BASE=http://localhost:3001
API=http://localhost:3001
```
Tenés que reemplazar los campos con tus propias credenciales para conectarte. 

Hacer `npm install`

__CLIENT:__


En `client` vas a tener que crear un archivo llamado: `.env` que tenga la siguiente forma:

```
REACT_APP_API=http://localhost:3001
```

Hacer `npm install`


## Funcionalidades

### Usuarios no Autenticados

Un Visitante anónimo puede navegar el e-commerce, ver y buscar productos.

#### Como visitante puede:

<p align='center'>
    <img alt="e-commerce" style="border-radius:5px" src='./img/products.png' </img>
</p>

- PRODUCTOS:
    + ver la lista completa de productos (catálogo), para ver todo lo disponible para comprar.
    + refinar el listado por categorías, para poder ver los items en los que estoy interesado.
    + buscas productos, para poder encontrar rápido los productos que quiero comprar.
    + ver los detalles de un producto individual (incluida las fotos, descripciones, reviews, etc...), asi puede determinar si quiero ese producto o no.

    <p align='center'>
    <img alt="Ecommerce" style="border-radius:5px" src='./img/productDetail.png' </img>
</p>

- CARRITO:
    + poder agregar items a mi carrito de compras desde el listado o desde a página de detalles de un producto, para poder comprarlos despues.
    + sacar items de mi carrito, en caso que decida no quererlos.
    + editar cantidades de los items de mi carrito, en caso que quiera mas o menos cantidad de un item en particular.
    + refrescar la página, o irme y volver, y todavía tener mi carrito de compras (sin haberme creado una cuenta). (Podés usar sessionStorage, localStorage, cookies, o JWT).
    + poder crearme una cuenta, loguearme y seguir editando ese mismo carrito, asi no pierdo los items seleccionados.
    <p align='center'>
    <img alt="Ecommerce" style="border-radius:5px" src='./img/shopCart.png' </img>
</p>

- GESTION DE CUENTA:
    + poder crear una cuenta, asi puede hacer otras cosas como dejar un review.
    + poder logearme usando Google o Github, para no tener que acordarme de un password nuevo.

    <p align='center'>
    <img alt="Ecommerce" style="border-radius:5px" src='./img/register.png' </img>
</p>

## Usuarios Autenticados

Los usuarios que hayan creado su cuenta, podrán hacer todo lo que puede hacer un usuario guest y además:

### Como un Usuario Autenticado puedo:

- GESTION DE CUENTA:
    + poder desloguearme, asi nadie más pueda usar mi sesión.
- REVIEWS:
    + poder dejar reviews a los productos, que incluyan texto y un sistema de cinco estrellas.
- CHECKOUT:
    + poder comprar todos los items de un mi carrito.
    + especificar una dirección de envio y un email cuando hago el checkout, asi me envien la compra a lugar que dije.
    + recibir un email de confirmación que hice la compra.
    + recibir un email de notificación cuando la orden fue despachada.
    <p align='center'>
    <img alt="Ecommerce" style="border-radius:5px" src='./img/finish.png' </img>
</p>

## Admin

Los usuarios administradores pueden manejar el sitio, los productos que se listan y los items que están disponibles.

### Como un administrador puedo:

- GESTION DE PRODUCTOS:
    +  crear y editar productos, con nombre, descripción, precio y uno o más fotos, tal que los visitantes puedan ver la última información de lo que se vende.
    
    +  crear categorías, para que los usuarios puedan filtrar los items.
    +  agregar o sacar categorías de los items (los items deben poder aceptar múltiples categorías).
    + gestionar la disponibilidad de un item. (un item que no esta disponible, no deberá estar listado en la página, pero su detalle debe seguir siendo accesible desde el historial de compras o con su URL, pero debe mencionar que el item no está disponible).
    <p align='center'>
    <img alt="Ecommerce" style="border-radius:5px" src='./img/modal.png' </img>
</p>


- GESTION DE ORDENES:
    +  ver una lista de todas las ordenes, para poder ver y revisar las ordener.
    +  filtrar as ordenes por su estado (creada, procesando, cancelada, completa).
    + ver los detalles de una orden específica, asi puedo revisarla y actualizar su estado.
    +  cambiar el estado de una orden (creada => procesando, procesando => cancelada || completa).
    <p align='center'>
    <img alt="Ecommerce" style="border-radius:5px" src='./img/listOrders.png' </img>
</p>

- GESTION DE USUARIOS:
    +  hacer que un usuario se convierta en admin.
    + borrar a un usuario, asi no puedan logearse más.
    + forzar una password reset para un usuario.

### Validación de Datos

- Productos:
    + Deben tienen `titulo`, `descripcion`, `precio`, `cantidad`
    + Deben tener una foto, si no tienen una foto, deben tener un placeholder de foto por defecto.
- Usuarios:
    + Deben tener una dirección de mail válida.
    + Su email debe ser único.
- Ordenes:
    + Una orden debe pertenecer a un usuario o a un guest (autenticado vs no autenticado).
    + Las ordenes deben tener línea de orden que contiene el `precio`, `productId`, y `cantidad`.
    + Si un usuario completa una orden, esa orden debe mantener el precio del item al momento de la compra, sin importar que el precio del producto cambie después.
- Reviews:
    + Todas las reviews pertenecen a un producto.
    + Todas las reviews pertenecen a un usuario.
    + Todas las reviews deben tener por lo menos x caractéres.

