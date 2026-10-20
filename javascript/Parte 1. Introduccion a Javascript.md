# ¿Qué es JavaScript?

**JavaScript** es un lenguaje de programación que permite crear aplicaciones interactivas y dinámicas.

Originalmente fue desarrollado para ejecutarse en navegadores web, pero actualmente también puede utilizarse fuera de ellos mediante entornos como **Node.js**.

JavaScript se utiliza principalmente para:

- **Frontend:** agregar interactividad y lógica a interfaces web.
    
- **Backend:** desarrollar servidores y aplicaciones mediante Node.js.
    
- **Automatización:** crear scripts para ejecutar tareas repetitivas.
    

A diferencia de HTML, que define la estructura de una página, y CSS, que define su apariencia, JavaScript permite programar su comportamiento.

## Parte 1. Fundamentos de JavaScript

### 1. Variables

Una variable permite almacenar un valor para utilizarlo posteriormente en nuestro programa.

En JavaScript podemos declarar variables utilizando `let`, `const` y `var`.

```
let nombre = "Ana";
const edad = 25;
var ciudad = "México";
```

Las diferencias son:

- **let:** permite declarar variables cuyo valor puede cambiar.
    
- **const:** declara variables que no pueden ser reasignadas.
    
- **var:** es una forma antigua de declarar variables, cuyo uso generalmente se evita en código moderno.
    

```
let contador = 1;
contador = 2; // Válido

const nombre = "Ana";
nombre = "Luis"; // Error
```

**Importante:** `const` impide reasignar una variable, pero no hace inmutables los objetos o arrays que contiene.

### 2. Tipos de datos primitivos

JavaScript tiene siete tipos de datos primitivos.

|Tipo|Descripción|Ejemplo|
|---|---|---|
|`string`|Cadenas de texto.|`"Hola"`|
|`number`|Números enteros y decimales.|`25`, `3.14`|
|`boolean`|Valores verdadero o falso.|`true`|
|`undefined`|Valor no definido.|`undefined`|
|`null`|Ausencia intencional de valor.|`null`|
|`bigint`|Números enteros de gran tamaño.|`123n`|
|`symbol`|Identificadores únicos.|`Symbol("id")`|

JavaScript es un lenguaje de tipado dinámico, por lo que una variable puede contener valores de diferentes tipos durante su ejecución.

```
let dato = 10;
dato = "Hola";
dato = true;
```

Para consultar el tipo de un valor utilizamos `typeof`:

```
console.log(typeof "Hola"); // string
console.log(typeof 25); // number
console.log(typeof true); // boolean
```

### 3. Scope (Ámbito)

El **scope** determina dónde puede utilizarse una variable dentro de nuestro programa.

Existen diferentes ámbitos:

- **Global:** variables accesibles desde diferentes partes del programa, según el entorno.
    
- **Función:** variables declaradas dentro de una función.
    
- **Bloque:** variables declaradas mediante `let` o `const` dentro de un bloque `{}`.
    

```
let nombre = "Ana";

function saludar() {
  let mensaje = "Hola";
  console.log(nombre); // Ana
  console.log(mensaje); // Hola
}

saludar();
console.log(mensaje); // Error
```

#### Diferencias entre let, const y var

```
if (true) {
  var a = 10;
  let b = 20;
  const c = 30;
}

console.log(a); // 10
console.log(b); // Error
console.log(c); // Error
```

`var` tiene ámbito de función o global, mientras que `let` y `const` tienen ámbito de bloque.

Por esta razón, se recomienda utilizar `const` por defecto y `let` cuando necesitemos reasignar una variable.

### 4. Template Strings

Los **template strings** o _template literals_ permiten construir cadenas de texto utilizando comillas invertidas (`` ` ``).

Su principal ventaja es que permiten insertar expresiones mediante `${}`.

```
const nombre = "Ana";
const edad = 25;

const mensaje = `Hola, soy ${nombre} y tengo ${edad} años`;

console.log(mensaje);
```

También permiten escribir cadenas de varias líneas:

```
const mensaje = `
Hola, bienvenido.
Este es mi primer programa.
`;
```

### 5. Objetos: clave y valor

Un **objeto** permite agrupar información mediante pares de clave y valor.

Cada clave identifica una propiedad y cada valor contiene su información.

```
const usuario = {
  nombre: "Ana",
  edad: 25,
  activo: true
};
```

Podemos acceder a sus propiedades utilizando el punto `.` o corchetes `[]`:

```
console.log(usuario.nombre);
console.log(usuario["edad"]);
```

También podemos modificar o agregar propiedades:

```
usuario.edad = 26;
usuario.correo = "ana@ejemplo.com";
```

Aunque `usuario` fue declarado con `const`, sus propiedades pueden modificarse.

### Primera práctica

Crea un archivo llamado `fundamentos.js` y escribe:

```
const nombre = "Ana";
let edad = 20;

const estudiante = {
  nombre: nombre,
  edad: edad,
  activo: true
};

console.log(`Hola, soy ${estudiante.nombre}`);
console.log(`Tengo ${estudiante.edad} años`);
```

Ejecuta el archivo desde la terminal:

```
node fundamentos.js
```

Si aparece el mensaje en la consola, habrás ejecutado tu primer programa de JavaScript con Node.js.