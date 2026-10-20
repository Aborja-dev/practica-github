
## ¿Qué es TypeScript?

**TypeScript** es un lenguaje desarrollado por Microsoft que amplía JavaScript incorporando un sistema de tipos estáticos.

Permite detectar numerosos errores durante el desarrollo, antes de ejecutar el programa.

Por ejemplo, en JavaScript podemos escribir:

```
let edad = 25;
edad = "veinticinco";
```

En TypeScript podemos especificar que la variable debe contener un número:

```
let edad: number = 25;
edad = "veinticinco"; // Error de tipo
```

TypeScript comprueba los tipos durante el desarrollo, pero normalmente el código debe transformarse a JavaScript para ejecutarse en entornos habituales.

## 1. Tipar variables y tipos primitivos

Para indicar un tipo utilizamos `:` seguido del nombre del tipo.

```
const nombre: string = "Ana";
const edad: number = 25;
const activo: boolean = true;
```

Los tipos más habituales son:

|Tipo|Descripción|
|---|---|
|`string`|Cadenas de texto.|
|`number`|Valores numéricos.|
|`boolean`|Verdadero o falso.|
|`bigint`|Números enteros grandes.|
|`symbol`|Identificadores únicos.|
|`null`|Ausencia de valor.|
|`undefined`|Valor no definido.|

### Inferencia de tipos

TypeScript puede identificar automáticamente el tipo de una variable a partir de su valor.

```
const nombre = "Ana";
const edad = 25;
```

En este ejemplo, no necesitamos declarar explícitamente los tipos.

### Arrays tipados

Podemos indicar qué tipo de elementos contiene un array:

```
const numeros: number[] = [1, 2, 3];
const nombres: string[] = ["Ana", "Luis"];
```

Esto evita agregar valores incompatibles:

```
numeros.push("Hola"); // Error
```

### Objetos tipados

También podemos definir los tipos de las propiedades:

```
const usuario: {
  nombre: string;
  edad: number;
} = {
  nombre: "Ana",
  edad: 25
};
```

## 2. Tipar funciones

TypeScript permite definir los tipos de los parámetros y el valor que devuelve una función.

```
function sumar(a: number, b: number): number {
  return a + b;
}
```

En este ejemplo:

- `a: number` indica que el primer parámetro es numérico.
    
- `b: number` indica que el segundo parámetro es numérico.
    
- `: number` después de los paréntesis indica el tipo de retorno.
    

### Arrow functions tipadas

```
const sumar = (a: number, b: number): number => {
  return a + b;
};
```

También podemos tipar funciones que no devuelven un valor:

```
function saludar(nombre: string): void {
  console.log(`Hola ${nombre}`);
}
```

El tipo `void` indica que no esperamos utilizar un valor de retorno.

### Parámetros opcionales

Podemos indicar que un parámetro es opcional mediante `?`:

```
function saludar(nombre: string, apellido?: string): string {
  return `Hola ${nombre} ${apellido ?? ""}`;
}
```

### Union Types

Los tipos de unión permiten aceptar más de un tipo:

```
let identificador: string | number;

identificador = 123;
identificador = "ABC-123";
```

Esto resulta útil cuando un valor puede representarse de diferentes maneras.

## 3. Types vs Interfaces

TypeScript permite definir estructuras reutilizables mediante `type` e `interface`.

Ambos sirven para describir la forma que deben tener los datos, especialmente los objetos.

### Type

Un **type alias** permite asignar un nombre a un tipo.

```
type Usuario = {
  nombre: string;
  edad: number;
};

const usuario: Usuario = {
  nombre: "Ana",
  edad: 25
};
```

También permite crear tipos de unión:

```
type Identificador = string | number;

type Estado = "activo" | "inactivo" | "pendiente";
```

### Interface

Una **interface** permite describir la estructura que debe cumplir un objeto.

```
interface Usuario {
  nombre: string;
  edad: number;
}

const usuario: Usuario = {
  nombre: "Ana",
  edad: 25
};
```

Podemos extender una interfaz para agregar propiedades:

```
interface Usuario {
  nombre: string;
}

interface Administrador extends Usuario {
  permisos: string[];
}
```

### Diferencias entre Type e Interface

|Type|Interface|
|---|---|
|Puede representar primitivos, objetos, uniones y tuplas.|Se utiliza principalmente para describir estructuras de objetos.|
|Puede combinar tipos mediante `&`.|Puede extender otras interfaces mediante `extends`.|
|No admite fusionar declaraciones con el mismo nombre.|Permite fusionar declaraciones compatibles con el mismo nombre.|
|Es útil para uniones y composiciones de tipos.|Es útil para contratos de objetos extensibles.|

### ¿Cuál utilizar?

En muchos casos, ambas opciones son válidas.

Como convención inicial:

- Utiliza **interface** para definir estructuras de objetos.
    
- Utiliza **type** para crear uniones, tipos literales y otras composiciones.
    

No es una regla obligatoria; los equipos pueden adoptar sus propias convenciones.

## 4. Primera práctica

Vamos a crear una lista de estudiantes utilizando interfaces y funciones tipadas.

```
interface Estudiante {
  nombre: string;
  calificacion: number;
}

const estudiantes: Estudiante[] = [
  { nombre: "Ana", calificacion: 90 },
  { nombre: "Luis", calificacion: 65 },
  { nombre: "María", calificacion: 85 }
];

const obtenerAprobados = (
  lista: Estudiante[]
): Estudiante[] => {
  return lista.filter(estudiante => estudiante.calificacion >= 70);
};

console.log(obtenerAprobados(estudiantes));
```

En este ejercicio:

1. Definimos una interfaz llamada `Estudiante`.
    
2. Creamos un array que únicamente acepta objetos con esa estructura.
    
3. Declaramos una función tipada que recibe y devuelve un array de estudiantes.
    
4. Utilizamos `filter()` para seleccionar los estudiantes aprobados.
    

Para ejecutar el ejercicio mediante el compilador de TypeScript, instala TypeScript en tu proyecto:

```
pnpm add -D typescript
```

Guarda el programa como `estudiantes.ts` y compílalo:

```
pnpm exec tsc estudiantes.ts
```

Esto generará un archivo JavaScript que puedes ejecutar:

```
node estudiantes.js
```

**Nota:** TypeScript comprueba tipos durante el desarrollo, pero no valida automáticamente los datos externos durante la ejecución.