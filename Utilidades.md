
Además de las herramientas de desarrollo, existen algunas otras utilidades que nos ayudan para el desarrollo y hacer la documentacion

## 1. Markdown

Markdown es un lenguaje que permite dar formato a documentos utilizando una sintaxis sencilla.
Muchos archivos de documentación, especialmente los `README.md` de GitHub, están escritos en Markdown. Por esta razón, es importante conocer sus elementos básicos. Los archivos con terminación .md son archivos markdown, se pueden abrir con bloc de notas

### Sintaxis básica
Markdown utiliza texto plano y una sintaxis sencilla para dar formato al contenido e insertar elementos como títulos, listas, enlaces, imágenes y bloques de código, sin necesidad de utilizar un editor de texto enriquecido.

|Elemento|Sintaxis|Descripción|
|---|---|---|
|Título|`# Título`|Crea un encabezado principal.|
|Subtítulo|`## Subtítulo`|Crea un encabezado secundario.|
|Negrita|`**texto**`|Resalta texto en negrita.|
|Cursiva|`*texto*`|Aplica cursiva.|
|Lista|`- Elemento`|Crea una lista de viñetas.|
|Enlace|`[Texto](URL)`|Inserta un enlace.|
|Imagen|`![Descripción](imagen.png)`|Inserta una imagen.|
|Código|`` `código` ``|Resalta código en línea.|
|Separador|`---`|Inserta una línea horizontal.|

### Bloques de código

Markdown permite insertar bloques de código indicando el lenguaje utilizado:

````
```javascript
console.log("Hola mundo");
```
````

Esto facilita la lectura de ejemplos y permite resaltar la sintaxis.
### Frontmatter
El **frontmatter** es una sección de metadatos que se coloca al inicio de un archivo Markdown. Se utiliza para definir información como el título, autor, fecha, etiquetas o categoría del documento.

Generalmente utiliza sintaxis YAML y se delimita mediante tres guiones (`---`).

```yaml
---
title: Mi primer documento
author: Abraham
date: 2026-10-19
tags:
  - markdown
  - documentación
---
```

El frontmatter no forma parte del Markdown estándar, pero es utilizado por herramientas para organizar y procesar archivos.

### Vista previa en VS Code

VS Code permite visualizar cómo se renderiza un archivo Markdown.

1. Abre un archivo con extensión `.md`.
    
2. Presiona `Ctrl + Shift + V` para abrir la vista previa.
    
3. Utiliza `Ctrl + K`, seguido de `V`, para mostrar la vista previa a un lado del editor.
    

Para más información, consulta la [guía de Markdown de GitHub](https://docs.github.com/es/get-started/writing-on-github).

---

## 2. Snippets de VS Code

Los _snippets_ son fragmentos de código reutilizables que permiten escribir estructuras comunes utilizando abreviaciones.

Son útiles para ahorrar tiempo, reducir errores y evitar escribir repetidamente el mismo código.

### ¿Cómo funcionan?

Un snippet se activa escribiendo una palabra clave y seleccionando la sugerencia del editor, normalmente mediante la tecla `Tab` o `Enter`, dependiendo de la configuración.

Por ejemplo, podemos crear un snippet que al escribir:

```
clg
```

Genere automáticamente:

```
console.log();
```

### Crear un snippet personalizado

1. Abre VS Code.
    
2. Presiona `Ctrl + Shift + P`.
    
3. Busca **Snippets: Configure Snippets**.
    
4. Selecciona `javascript.json` para crear un snippet de JavaScript.
    
5. Agrega la siguiente configuración:
    

```json
{
  "Console Log": {
    "prefix": "clg",
    "body": [
      "console.log($1);"
    ],
    "description": "Inserta un console.log"
  }
}
```

### Estructura de un snippet

- **prefix:** abreviación que activa el snippet.
    
- **body:** código que se insertará automáticamente.
    
- **description:** descripción que aparece en las sugerencias.
    
- **$1:** posición donde se colocará el cursor después de insertar el snippet.
    

### Utilizar el snippet

En un archivo JavaScript, escribe `clg` y selecciona el snippet en las sugerencias.

VS Code insertará:

```javascript
console.log();
```

El cursor quedará dentro de los paréntesis, listo para escribir.

Puedes consultar la [documentación oficial de snippets de VS Code](https://code.visualstudio.com/docs/editing/userdefinedsnippets).

# 3. Obsidian

## ¿Qué es Obsidian?

**Obsidian** es una aplicación para tomar notas, organizar información y crear una base de conocimiento personal.

Utiliza archivos Markdown (`.md`) que se almacenan localmente en nuestra computadora, permitiendo editar las notas incluso desde otros editores como VS Code.

Una de sus principales características es la posibilidad de conectar notas mediante enlaces, facilitando la organización de conceptos y documentación.

Puedes descargarlo desde [Obsidian](https://obsidian.md/).

## 1. Crear un Vault

Un **Vault** o bóveda es una carpeta donde Obsidian almacena nuestras notas y archivos.

Para crear uno:

1. Abre Obsidian.
    
2. Selecciona **Create new vault**.
    
3. Escribe un nombre, por ejemplo `Mis apuntes`.
    
4. Selecciona la ubicación donde se guardará.
    
5. Haz clic en **Create**.
    

Una vez creado, podrás organizar tus notas mediante carpetas y archivos Markdown.

## 2. Crear notas

Para crear una nota, selecciona **New note** en el explorador de archivos.

Las notas utilizan la sintaxis de Markdown:

```
# JavaScript

JavaScript es un lenguaje de programación.

## Variables

Las variables permiten almacenar valores.

- let
- const
- var
```

Obsidian permite editar Markdown y visualizar su formato mediante la vista previa.

## 3. Enlazar notas

Una de las funciones más importantes de Obsidian es la posibilidad de relacionar diferentes notas.

Para crear un enlace interno, utiliza dobles corchetes:

```
[[JavaScript]]
```

También puedes cambiar el texto visible del enlace:

```
[[JavaScript|Introducción a JavaScript]]
```

Esto permite construir una red de conocimientos conectados.

### Backlinks

Los **backlinks** o enlaces entrantes muestran qué otras notas contienen enlaces hacia la nota actual.

Por ejemplo, si una nota sobre React contiene un enlace a `[[JavaScript]]`, podremos encontrar esa relación desde la nota de JavaScript.

### Graph View

La vista de grafo muestra una representación visual de las notas y sus conexiones.

Permite explorar las relaciones entre diferentes conceptos.

## 4. Organizar notas con etiquetas y propiedades

### Etiquetas

Las etiquetas permiten clasificar notas por temas.

```
#javascript
#programacion
#apuntes
```

### Propiedades (Frontmatter)

También podemos agregar metadatos al inicio de una nota mediante YAML:

```
---
tags:
  - javascript
  - programacion
status: en-progreso
---
```

Obsidian permite editar estas propiedades desde su interfaz.

## 5. Comandos y atajos útiles

|Atajo|Función|
|---|---|
|`Ctrl + O`|Buscar y abrir una nota.|
|`Ctrl + N`|Crear una nueva nota.|
|`Ctrl + P`|Abrir la paleta de comandos.|
|`Ctrl + Shift + F`|Buscar contenido en las notas.|
|`Ctrl + E`|Alternar entre edición y lectura.|
|`[[`|Insertar un enlace interno.|

_Los atajos corresponden a configuraciones habituales en Windows y pueden personalizarse._

## 6. Plugins

Obsidian permite ampliar sus funcionalidades mediante plugins.

Existen dos tipos:

- **Core plugins:** funciones integradas que podemos activar o desactivar desde la configuración.
    
- **Community plugins:** extensiones desarrolladas por la comunidad que agregan nuevas funcionalidades.
    

Para gestionar los plugins, abre **Settings → Core plugins** o **Settings → Community plugins**.

Instala únicamente plugins de fuentes confiables, ya que las extensiones comunitarias pueden ejecutar código dentro de la aplicación.

