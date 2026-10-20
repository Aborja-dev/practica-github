
En JavaScript podemos organizar información mediante estructuras de datos y reutilizar instrucciones mediante funciones.

## 1. Estructuras de datos

Las estructuras de datos permiten almacenar y organizar conjuntos de valores.

### Arrays

Un **array** es una estructura que permite almacenar varios elementos en una misma variable.

```
const frutas = ["manzana", "pera", "naranja"];
```

Los elementos tienen una posición o índice que comienza en `0`.

```
console.log(frutas[0]); // manzana
console.log(frutas[1]); // pera
```

Podemos consultar su tamaño mediante `length`:

```
console.log(frutas.length); // 3
```

### Métodos de arrays

Los arrays incluyen métodos para agregar, eliminar, buscar y transformar elementos.

|Método|Descripción|
|---|---|
|`push()`|Agrega elementos al final.|
|`pop()`|Elimina y devuelve el último elemento.|
|`shift()`|Elimina y devuelve el primer elemento.|
|`unshift()`|Agrega elementos al principio.|
|`includes()`|Comprueba si existe un valor.|
|`find()`|Devuelve el primer elemento que cumple una condición.|
|`filter()`|Crea un array con los elementos que cumplen una condición.|
|`map()`|Crea un array transformando cada elemento.|
|`forEach()`|Ejecuta una función por cada elemento.|
|`reduce()`|Acumula los elementos en un resultado.|
|`slice()`|Obtiene una porción sin modificar el array original.|
|`splice()`|Agrega, elimina o reemplaza elementos modificando el array.|

#### Ejemplos

```
const numeros = [1, 2, 3, 4, 5];

// Agregar un elemento
numeros.push(6);

// Transformar elementos
const dobles = numeros.map(numero => numero * 2);

// Filtrar elementos
const pares = numeros.filter(numero => numero % 2 === 0);

// Buscar un elemento
const encontrado = numeros.find(numero => numero > 3);

console.log(dobles);
console.log(pares);
console.log(encontrado);
```

**Importante:** algunos métodos modifican el array original, como `push` y `splice`, mientras que otros devuelven un nuevo array, como `map` y `filter`.

### Objetos

Un **objeto** permite organizar datos mediante propiedades formadas por claves y valores.

```
const usuario = {
  nombre: "Ana",
  edad: 25,
  activo: true
};
```

Los objetos también pueden contener arrays y otros objetos:

```
const usuario = {
  nombre: "Ana",
  habilidades: ["JavaScript", "Git"],
  direccion: {
    ciudad: "México",
    pais: "México"
  }
};
```

Para acceder a los valores:

```
console.log(usuario.habilidades[0]);
console.log(usuario.direccion.ciudad);
```

### Métodos de objetos

JavaScript proporciona métodos para consultar y transformar la información de los objetos.

|Método|Descripción|
|---|---|
|`Object.keys()`|Devuelve un array con las claves propias enumerables.|
|`Object.values()`|Devuelve un array con los valores de esas propiedades.|
|`Object.entries()`|Devuelve pares de clave y valor.|
|`Object.assign()`|Copia propiedades entre objetos.|
|`Object.hasOwn()`|Comprueba si un objeto tiene una propiedad propia.|
|`Object.freeze()`|Impide modificaciones directas al objeto, de forma superficial.|

#### Ejemplo

```
const usuario = {
  nombre: "Ana",
  edad: 25
};

console.log(Object.keys(usuario));
// ["nombre", "edad"]

console.log(Object.values(usuario));
// ["Ana", 25]

console.log(Object.entries(usuario));
// [["nombre", "Ana"], ["edad", 25]]
```

También podemos recorrer las propiedades:

```
Object.entries(usuario).forEach(([clave, valor]) => {
  console.log(`${clave}: ${valor}`);
});
```

## 2. Funciones

Una **función** es un bloque de código reutilizable que realiza una tarea determinada.

Puede recibir parámetros y devolver un resultado.

### Declaración de funciones

```
function sumar(a, b) {
  return a + b;
}

console.log(sumar(5, 3)); // 8
```

En este ejemplo:

- `sumar` es el nombre de la función.
    
- `a` y `b` son parámetros.
    
- `return` devuelve el resultado.
    
- `sumar(5, 3)` es una llamada a la función con dos argumentos.
    

### Expresiones de funciones

También podemos almacenar una función en una variable:

```
const sumar = function(a, b) {
  return a + b;
};
```

### Arrow Functions

Las **arrow functions** son una sintaxis para escribir funciones utilizando el operador `=>`.

```
const sumar = (a, b) => {
  return a + b;
};
```

Cuando una función contiene una sola expresión, podemos utilizar un retorno implícito:

```
const sumar = (a, b) => a + b;
```

Si recibe un único parámetro, los paréntesis pueden omitirse:

```
const duplicar = numero => numero * 2;
```

Las arrow functions son especialmente útiles al trabajar con métodos de arrays:

```
const numeros = [1, 2, 3, 4];

const cuadrados = numeros.map(numero => numero ** 2);

console.log(cuadrados); // [1, 4, 9, 16]
```

**Nota:** Las arrow functions no tienen su propio `this`, a diferencia de las funciones tradicionales. Por ello, no siempre son intercambiables.

## 3. Primera práctica

Vamos a combinar arrays, objetos y funciones para procesar información.

```
const estudiantes = [
  { nombre: "Ana", calificacion: 90 },
  { nombre: "Luis", calificacion: 65 },
  { nombre: "María", calificacion: 85 }
];

const aprobados = estudiantes.filter(
  estudiante => estudiante.calificacion >= 70
);

const nombres = aprobados.map(
  estudiante => estudiante.nombre
);

console.log(nombres);
```

El programa utiliza:

1. Un array para almacenar estudiantes.
    
2. Objetos para representar cada estudiante.
    
3. `filter()` para seleccionar a quienes aprobaron.
    
4. `map()` para obtener sus nombres.
    

El resultado será:

```
["Ana", "María"]
```

Esta combinación de estructuras de datos y funciones es habitual en el desarrollo de aplicaciones JavaScript.