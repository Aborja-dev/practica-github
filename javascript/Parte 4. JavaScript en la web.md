JavaScript permite agregar comportamiento a las páginas web, modificar su contenido y comunicarse con servicios externos.

Para comprender cómo funciona, primero necesitamos conocer su relación con HTML y CSS.

## 1. HTML, CSS y JavaScript

Una página web utiliza principalmente tres tecnologías:

- **HTML (HyperText Markup Language):** define la estructura y el contenido de la página.
    
- **CSS (Cascading Style Sheets):** controla su apariencia, incluyendo colores, tamaños y distribución.
    
- **JavaScript:** permite agregar lógica, interactividad y modificar el contenido dinámicamente.
    

### HTML básico

HTML utiliza etiquetas para definir elementos dentro de una página.

```
<!DOCTYPE html>
<html lang="es">
  <head>
    <meta charset="UTF-8">
    <title>Mi primera página</title>
  </head>
  <body>
    <h1>Hola mundo</h1>
    <p>Mi primera página web.</p>
    <button>Presionar</button>
  </body>
</html>
```

Algunas etiquetas habituales son:

|Etiqueta|Descripción|
|---|---|
|`<h1>` a `<h6>`|Encabezados.|
|`<p>`|Párrafo de texto.|
|`<a>`|Enlace.|
|`<img>`|Imagen.|
|`<div>`|Contenedor genérico.|
|`<button>`|Botón.|
|`<input>`|Campo de entrada.|
|`<form>`|Formulario.|
|`<script>`|Incorpora JavaScript.|
|`<link>`|Vincula recursos como hojas de estilo.|

### CSS básico

CSS permite definir estilos mediante selectores y propiedades.

```
body {
  font-family: Arial, sans-serif;
  background-color: #f5f5f5;
}

h1 {
  color: blue;
}

button {
  padding: 10px;
  cursor: pointer;
}
```

La sintaxis se compone de un **selector**, una **propiedad** y un **valor**.

Podemos vincular una hoja de estilos desde HTML:

```
<link rel="stylesheet" href="./style.css">
```

### Incorporar JavaScript

Para utilizar JavaScript en una página podemos agregar un archivo mediante la etiqueta `<script>`.

```
<script src="./script.js" defer></script>
```

El atributo `defer` permite descargar el script sin bloquear el análisis del HTML y ejecutarlo cuando el documento haya sido procesado.

---

## 2. DOM (Document Object Model)

El **DOM** es una representación del documento HTML mediante una estructura de objetos que JavaScript puede consultar y modificar.

Gracias al DOM podemos cambiar textos, agregar elementos, modificar estilos y responder a las acciones del usuario.

### Seleccionar elementos

Podemos seleccionar elementos utilizando `document.querySelector()`.

```
<h1 id="titulo">Hola mundo</h1>
```

```
const titulo = document.querySelector("#titulo");
```

Algunos métodos habituales son:

|Método|Descripción|
|---|---|
|`querySelector()`|Selecciona el primer elemento que coincide con un selector CSS.|
|`querySelectorAll()`|Selecciona todos los elementos que coinciden.|
|`getElementById()`|Busca un elemento mediante su ID.|
|`createElement()`|Crea un elemento HTML.|

### Modificar contenido

```
const titulo = document.querySelector("#titulo");

titulo.textContent = "Bienvenido a JavaScript";
```

También podemos modificar clases CSS:

```
titulo.classList.add("activo");
titulo.classList.remove("activo");
titulo.classList.toggle("activo");
```

### Crear elementos

```
const parrafo = document.createElement("p");

parrafo.textContent = "Este elemento fue creado con JavaScript";

document.body.append(parrafo);
```

### Eventos

Los eventos permiten ejecutar código cuando ocurre una acción, como hacer clic, escribir o enviar un formulario.

```
<button id="boton">Saludar</button>
<p id="mensaje"></p>
```

```
const boton = document.querySelector("#boton");
const mensaje = document.querySelector("#mensaje");

boton.addEventListener("click", () => {
  mensaje.textContent = "¡Hola!";
});
```

El método `addEventListener()` permite asociar una función a un evento.

Otros eventos comunes son `input`, `change`, `submit` y `keydown`.

---

## 3. Promesas y asincronía

JavaScript permite realizar operaciones que pueden tardar en completarse, como solicitar información a un servidor.

Una **Promise** representa el resultado futuro de una operación asíncrona.

Una promesa puede encontrarse en tres estados:

- **Pending:** la operación todavía no termina.
    
- **Fulfilled:** la operación terminó correctamente.
    
- **Rejected:** la operación falló.
    

### Utilizar una promesa

```
const promesa = new Promise((resolve) => {
  setTimeout(() => {
    resolve("Operación completada");
  }, 1000);
});

promesa.then(resultado => {
  console.log(resultado);
});
```

### Métodos de promesas

|Método|Descripción|
|---|---|
|`.then()`|Procesa el resultado de una promesa cumplida.|
|`.catch()`|Maneja un rechazo o error en la cadena.|
|`.finally()`|Ejecuta código al finalizar, independientemente del resultado.|
|`Promise.all()`|Espera que todas las promesas se cumplan o rechaza si alguna falla.|
|`Promise.allSettled()`|Espera que todas finalicen, independientemente del resultado.|

### Async y Await

`async` y `await` permiten trabajar con promesas utilizando una sintaxis más sencilla.

```
async function obtenerDatos() {
  try {
    const resultado = await Promise.resolve("Hola mundo");
    console.log(resultado);
  } catch (error) {
    console.error(error);
  }
}

obtenerDatos();
```

- **async:** declara una función asíncrona que devuelve una promesa.
    
- **await:** espera el resultado de una promesa dentro de un contexto que lo permita.
    
- **try/catch:** permite manejar errores.
    

`await` no bloquea toda la página mientras espera la operación.

### Fetch API

La función `fetch()` permite realizar peticiones HTTP para obtener información de servidores y APIs.

```
async function obtenerUsuarios() {
  try {
    const respuesta = await fetch(
      "https://jsonplaceholder.typicode.com/users"
    );

    if (!respuesta.ok) {
      throw new Error("Error al obtener usuarios");
    }

    const usuarios = await respuesta.json();
    console.log(usuarios);
  } catch (error) {
    console.error(error);
  }
}

obtenerUsuarios();
```

La función `fetch()` devuelve una promesa y `response.json()` permite interpretar el cuerpo de la respuesta como JSON.

---

## 4. Módulos de JavaScript

Los **módulos** permiten dividir nuestro código en diferentes archivos, facilitando su organización y reutilización.

JavaScript utiliza las palabras clave `export` e `import` para compartir funciones, variables y otros valores entre módulos.

### Exportar funciones

Archivo `operaciones.js`:

```
export function sumar(a, b) {
  return a + b;
}

export function restar(a, b) {
  return a - b;
}
```

### Importar funciones

Archivo `main.js`:

```
import { sumar, restar } from "./operaciones.js";

console.log(sumar(5, 3));
console.log(restar(5, 3));
```

### Exportación por defecto

También podemos exportar un valor por defecto:

```
export default function saludar(nombre) {
  return `Hola ${nombre}`;
}
```

E importarlo sin utilizar llaves:

```
import saludar from "./saludar.js";
```

### Utilizar módulos en HTML

Para cargar un módulo desde HTML utilizamos `type="module"`.

```
<script type="module" src="./main.js"></script>
```

Los módulos utilizan su propio ámbito, admiten importaciones y se ejecutan en modo estricto.

**Nota:** Para trabajar con módulos en el navegador, se recomienda utilizar un servidor de desarrollo en lugar de abrir el archivo directamente mediante `file://`, debido a las restricciones de seguridad del navegador.

---

## 5. Primera práctica: página interactiva

Vamos a combinar HTML, CSS, módulos y manipulación del DOM para crear un contador.

### Estructura del proyecto

```
mi-primera-web/
├── index.html
├── style.css
├── main.js
└── contador.js
```

### index.html

```
<!DOCTYPE html>
<html lang="es">
  <head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1">
    <title>Mi contador</title>
    <link rel="stylesheet" href="./style.css">
    <script type="module" src="./main.js"></script>
  </head>
  <body>
    <h1>Contador</h1>
    <p id="contador">0</p>
    <button id="incrementar">Incrementar</button>
  </body>
</html>
```

### style.css

```
body {
  font-family: Arial, sans-serif;
  text-align: center;
  padding: 40px;
}

button {
  padding: 10px 20px;
  cursor: pointer;
}

#contador {
  font-size: 32px;
}
```

### contador.js

```
export function incrementar(valor) {
  return valor + 1;
}
```

### main.js

```
import { incrementar } from "./contador.js";

const boton = document.querySelector("#incrementar");
const contador = document.querySelector("#contador");

let valor = 0;

boton.addEventListener("click", () => {
  valor = incrementar(valor);
  contador.textContent = valor;
});
```

### Ejecutar el proyecto

Abre una terminal dentro del directorio y ejecuta:

```
npx serve .
```

Si el paquete no está instalado, `npx` puede solicitar permiso para descargarlo.

Abre la dirección local que aparezca en la terminal.

Cada vez que presiones el botón, el contador aumentará una unidad.

Con esta práctica habrás utilizado:

- HTML para construir la interfaz.
    
- CSS para aplicar estilos.
    
- JavaScript para responder a eventos.
    
- DOM para modificar el contenido.
    
- Módulos para separar la lógica en diferentes archivos.