# ¿Qué es Git?

**Git** es un sistema de control de versiones que permite registrar, consultar y administrar los cambios realizados en los archivos de un proyecto.

Su principal función es mantener un historial de cambios, permitiendo recuperar versiones anteriores, trabajar en diferentes funcionalidades y colaborar con otros desarrolladores sin perder el trabajo realizado.

Git funciona de manera local, por lo que no necesita una conexión a Internet para registrar cambios.

## Conceptos básicos

### Repositorio (Repository)

Un **repositorio** es un directorio en el que Git registra y administra el historial de cambios de un proyecto.

Para convertir una carpeta en un repositorio, utilizamos:

```
git init
```

Esto crea un directorio oculto llamado `.git`, donde se almacena la información necesaria para el control de versiones.

### Commit

Un **commit** es un registro de los cambios realizados en el proyecto en un momento determinado.

Cada commit contiene un identificador único, información del autor, una fecha y un mensaje que describe los cambios.

```
git commit -m "Agregar página principal"
```

### Working Directory

El **directorio de trabajo** es la carpeta donde creamos, modificamos y eliminamos los archivos de nuestro proyecto.

Los cambios realizados aquí no se guardan automáticamente en el historial de Git.

### Staging Area

El **área de preparación** (_staging area_) permite seleccionar los cambios que queremos incluir en el siguiente commit.

Para agregar archivos utilizamos:

```
git add archivo.txt
```

También podemos preparar todos los cambios del directorio actual:

```
git add .
```

### Branch (Rama)

Una **rama** es una línea de desarrollo que permite trabajar en cambios de manera independiente sin modificar directamente la rama principal.

```
git branch nueva-rama
```

Para cambiar de rama:

```
git switch nueva-rama
```

La rama principal suele llamarse `main`.

### Merge (Fusión)

**Merge** permite integrar los cambios de una rama en otra.

Por ejemplo, estando en `main`, podemos integrar los cambios de `nueva-rama`:

```
git merge nueva-rama
```

### Repositorio remoto

Un **repositorio remoto** es una copia de un repositorio alojada en otra ubicación, generalmente en servicios como GitHub o GitLab.

Esto permite compartir el código y colaborar con otros desarrolladores.

- **Clone:** descarga un repositorio remoto a nuestra computadora.
    
- **Push:** envía commits locales a un repositorio remoto.
    
- **Pull:** obtiene e integra cambios de un repositorio remoto.
    
- **Fetch:** descarga información y cambios del remoto sin integrarlos automáticamente en nuestra rama de trabajo.
    

## Flujo básico de Git

El trabajo cotidiano con Git consiste en modificar archivos, seleccionar los cambios que queremos registrar y crear un commit.

```
Working Directory
       |
       | git add
       v
  Staging Area
       |
       | git commit
       v
Repositorio local
       |
       | git push
       v
Repositorio remoto
```

# Comandos básicos

|Comando|Descripción|
|---|---|
|`git init`|Inicializa un repositorio.|
|`git status`|Muestra el estado de los archivos.|
|`git add .`|Prepara los cambios del directorio actual.|
|`git commit -m "mensaje"`|Crea un commit con los cambios preparados.|
|`git log`|Muestra el historial de commits.|
|`git branch`|Lista las ramas locales.|
|`git switch rama`|Cambia a otra rama.|
|`git merge rama`|Integra los cambios de otra rama.|
|`git clone URL`|Clona un repositorio remoto.|
|`git push`|Envía commits al repositorio remoto.|
|`git pull`|Obtiene e integra cambios del remoto.|

**Nota:** Git y GitHub no son lo mismo. Git es el sistema de control de versiones, mientras que GitHub es una plataforma que permite alojar y compartir repositorios Git.

