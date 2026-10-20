---
descripcion: El objetivo de esta guía es aprender a instalar, configurar y utilizar las herramientas básicas que emplearemos durante las prácticas.
---

# Primeros pasos

Antes de comenzar con este repositorio, se necesita preparar el entorno de desarrollo.

## 1. Instalar el entorno

Asegúrate de tener instaladas las siguientes herramientas:

| Herramienta        | ¿Para qué sirve?                                                                | Instalación                                         |
| ------------------ | ------------------------------------------------------------------------------- | --------------------------------------------------- |
| Visual Studio Code | Editor de código para trabajar con nuestros proyectos.                          | [Descargar VS Code](https://code.visualstudio.com/) |
| Node.js            | Permite ejecutar JavaScript fuera del navegador.                                | [Descargar Node.js](https://nodejs.org/)            |
| pnpm               | Administrador de paquetes para instalar y gestionar dependencias.               | [Instalar pnpm](https://pnpm.io/installation)       |
| Git                | Sistema de control de versiones que permite registrar los cambios del proyecto. | [Descargar Git](https://git-scm.com/downloads)      |
| Git Bash           | Terminal que permite utilizar comandos de Bash en Windows.                      | Se incluye con Git para Windows.                    |

**Nota:** Se recomienda utilizar VS Code, pero puedes trabajar con cualquier editor de código de tu preferencia.


### Verificar las instalaciones

Para verificar que este instalado abre una terminal y ejecuta los siguientes comandos:

```
node --version
npm --version
pnpm --version
git --version
```

Cada comando debería mostrar la versión de la herramienta correspondiente.

## Lista de programas
- [ ] Editor de código
- [ ] Node
- [ ] pnpm
- [ ] git
## Diferencias entre Bash y PowerShell

Bash y PowerShell son intérpretes de comandos que permiten interactuar con el sistema operativo mediante instrucciones escritas. Aunque ambos se usan para realizar tareas similares, tienen diferencias importantes. Las cuales son:

**Nota**: la diferencia entre `/` y `\`: no es simplemente una cuestión estética. La barra invertida `\` también se utiliza en Bash para escapar caracteres, mientras que PowerShell usa el acento grave para ese propósito. Esto explica por qué copiar exactamente un comando de una terminal a otra puede producir resultados inesperados.
### Principales diferencias

- **Separadores de rutas:**
    
    - Bash utiliza la barra diagonal `/`.
        
    - PowerShell en Windows utiliza habitualmente la barra invertida `\`, aunque también acepta `/` en muchas rutas.
        
    
    ```bash
    # Bash
    cd proyectos/mi-app
    ```
    
    ```powershell
    # PowerShell
    cd proyectos\mi-app
    ```
    
- **Variables de entorno:**
    
    - Bash utiliza `$NOMBRE`.
        
    - PowerShell utiliza `$env:NOMBRE`.
        
    
    ```bash
    # Bash
    echo $PATH
    ```
    
    ```powershell
    # PowerShell
    echo $env:PATH
    ```
    
- **Declaración de variables:**
    
    - Bash no utiliza espacios alrededor del signo `=`.
        
    - PowerShell utiliza `$` antes del nombre de la variable y permite espacios.
        
    
    ```bash
    # Bash
    nombre="Juan"
    echo "$nombre"
    ```
    
    ```powershell
    # PowerShell
    $nombre = "Juan"
    echo $nombre
    ```
    
- **Ejecución de archivos:**
    
    - Bash utiliza `./` para ejecutar un script ubicado en el directorio actual.
        
    - PowerShell utiliza `.\` para ejecutar un script ubicado en el directorio actual.
        
    
    ```bash
    # Bash
    ./script.sh
    ```
    
    ```powershell
    # PowerShell
    .\script.ps1
    ```
    
- **Comandos para consultar archivos:**
    
    - Bash utiliza principalmente comandos como `ls`, `cat` y `grep`.
        
    - PowerShell utiliza comandos como `Get-ChildItem`, `Get-Content` y `Select-String`.
        
    
    ```bash
    # Bash
    ls
    cat archivo.txt
    ```
    
    ```powershell
    # PowerShell
    Get-ChildItem
    Get-Content archivo.txt
    ```
    
    PowerShell también admite algunos alias como `ls` y `cat`, aunque no necesariamente tienen el mismo comportamiento que en Bash.
    
- **Operadores para combinar comandos:**
    
    - Bash permite utilizar `&&` para ejecutar el siguiente comando únicamente si el anterior terminó correctamente.
        
    - PowerShell 7 también admite `&&`, pero Windows PowerShell 5.1 no lo reconoce.
        
    
    ```bash
    # Bash
    mkdir proyecto && cd proyecto
    ```
    
    ```powershell
    # PowerShell 7
    mkdir proyecto && cd proyecto
    ```
    
- **Continuación de comandos en varias líneas:**
    
    - Bash utiliza una barra invertida `\` al final de la línea.
        
    - PowerShell utiliza el acento grave o _backtick_ `` ` ``.
        
    
    ```bash
    # Bash
    npm install \
      react \
      react-dom
    ```
    
    ```powershell
    # PowerShell
    npm install `
      react `
      react-dom
    ```
    
- **Scripts:**
    
    - Bash suele utilizar archivos con extensión `.sh`.
        
    - PowerShell utiliza archivos con extensión `.ps1`.
        
- **Diferencias en el procesamiento de datos:**
    
    - Bash trabaja principalmente con flujos de texto.
        
    - PowerShell permite transmitir objetos estructurados entre comandos, facilitando el acceso a sus propiedades.


## 2. Configuracion de pnpm

Después de instalar Node.js y pnpm, verifica que funcionan correctamente:

```powershell
node --version
pnpm --version
```

### 1. Comprobar PATH

Si PowerShell no reconoce `pnpm`, consulta su ubicación y las rutas configuradas:

```powershell
Get-Command pnpm -All
$env:Path -split ';'
```

Si la ruta de instalación no aparece, agrégala desde **Variables de entorno → Variables de usuario → Path** y reinicia la terminal.

### 2. Habilitar ejecución de scripts

Si PowerShell bloquea `pnpm.ps1`, puedes utilizar:

```powershell
pnpm.cmd --version
```

O permitir la ejecución de scripts locales para tu usuario:

```powershell
Set-ExecutionPolicy -Scope CurrentUser -ExecutionPolicy RemoteSigned
```

**Nota:** Este último comando modifica la política de seguridad de PowerShell. Utilízalo únicamente si es necesario y está permitido en tu equipo.

### 3. Verificar instalación

```powershell
pnpm --version
```

Si muestra la versión instalada, pnpm está listo para utilizarse.

## 3. Configuración de Git

Por último, debemos configurar nuestro nombre y correo electrónico para identificar los cambios que realicemos en los repositorios.

### 1. Verificar instalación

Abre Git Bash o PowerShell y ejecuta:

```bash
git --version
```

### 2. Configurar usuario

Ejecuta los siguientes comandos utilizando tu nombre y correo electrónico:

```bash
git config --global user.name "Tu nombre"
git config --global user.email "tu@email.com"
```

### 3. Verificar configuración

Consulta la configuración actual:

```bash
git config --global --list
```

**Nota:** La opción `--global` aplica esta configuración a todos los repositorios de tu usuario. No es necesario repetirla para cada proyecto.
## 4. Primera práctica

Aunque Git puede ejecutarse desde diferentes terminales, gran parte de su documentación y tutoriales utilizan comandos de Bash. Por esta razón, utilizaremos **Git Bash** para trabajar con Git 

Antes de comenzar, vamos a familiarizarnos con algunos comandos básicos para navegar entre directorios, crear carpetas y archivos, y ejecutar programas.

Abre Git Bash y ejecuta los siguientes comandos:

```bash
# Crear una carpeta
mkdir mi-primer-proyecto

# Entrar en la carpeta
cd mi-primer-proyecto

# Crear un archivo
touch README.md

# Mostrar el contenido de la carpeta
ls -la

# Abrir el proyecto en VS Code
code .
```

Si todos los comandos funcionan correctamente, habrás creado tu primer directorio de trabajo y podrás comenzar a desarrollar dentro de él.
## Configuración de PATH

### ¿Qué es PATH?

PATH es una variable de entorno que contiene una lista de directorios donde el sistema operativo busca los programas que ejecutamos desde la terminal. Antes de iniciar debemos de configurarlo para que la terminal de Windows pueda buscar el ejecutable de los programas

Gracias a PATH, no tenemos que escribir la ubicación completa del programa cada vez que queremos utilizarlo.
### Consultar PATH

En PowerShell:

```
$env:PATH
```

En Git Bash:

```
echo "$PATH"
```

### Configurar PATH en Windows

1. Abre el menú Inicio y busca **Variables de entorno**.
    
2. Selecciona **Editar las variables de entorno del sistema**.
    
3. Haz clic en **Variables de entorno**.
    
4. En las variables de usuario, selecciona `Path`.
    
5. Haz clic en **Editar** y agrega la carpeta que contiene el ejecutable que necesitas utilizar.
    
6. Guarda los cambios y abre una nueva terminal.
    

**Importante:** Normalmente los instaladores configuran PATH automáticamente. No es necesario modificarlo si tus herramientas ya funcionan.



### ¿Por qué utilizamos Git Bash?

Git Bash nos proporciona un entorno familiar para trabajar con comandos habituales de Unix en Windows.

Esto resulta útil porque muchos proyectos, tutoriales y herramientas de desarrollo utilizan comandos de Bash.

También permite trabajar con Git desde la terminal.

**Nota:** Git Bash no convierte Windows en Linux. Algunos comandos y scripts específicos de Linux pueden no funcionar de la misma manera.

## Bash Cheatsheet

### Basicos
| Comando      | Descripción                                                       |
| ------------ | ----------------------------------------------------------------- |
| `pwd`        | Muestra el directorio actual.                                     |
| `ls`         | Lista archivos y carpetas.                                        |
| `ls -la`     | Lista archivos, incluidos los ocultos, con información adicional. |
| `cd carpeta` | Entra en una carpeta.                                             |
| `cd ..`      | Regresa al directorio superior.                                   |
| `cd ~`       | Va al directorio personal.                                        |
| `clear`      | Limpia la pantalla de la terminal.                                |

### Navegación

|Comando|Descripción|
|---|---|
|`pwd`|Muestra el directorio actual.|
|`ls`|Lista archivos y carpetas.|
|`ls -la`|Lista archivos, incluidos los ocultos, con información adicional.|
|`cd carpeta`|Entra en una carpeta.|
|`cd ..`|Regresa al directorio superior.|
|`cd ~`|Va al directorio personal.|
|`clear`|Limpia la pantalla de la terminal.|

### Archivos y directorios

|Comando|Descripción|
|---|---|
|`mkdir proyecto`|Crea una carpeta.|
|`touch archivo.txt`|Crea un archivo vacío o actualiza su fecha de modificación.|
|`cp origen destino`|Copia un archivo.|
|`mv origen destino`|Mueve o renombra un archivo.|
|`rm archivo.txt`|Elimina un archivo.|
|`rm -r carpeta`|Elimina una carpeta y su contenido.|
|`cat archivo.txt`|Muestra el contenido de un archivo.|

**Precaución:** Los comandos `rm` y `rm -r` pueden eliminar información sin enviarla a la papelera de reciclaje.

### Comandos útiles

| Comando             | Descripción                                                          |
| ------------------- | -------------------------------------------------------------------- |
| `echo "Hola mundo"` | Imprime texto en la terminal.                                        |
| `history`           | Muestra el historial de comandos de Bash.                            |
| `which node`        | Indica qué ejecutable se encuentra en PATH.                          |
| `code .`            | Abre el directorio actual en VS Code, si el comando está disponible. |
| `Ctrl + C`          | Interrumpe el proceso en ejecución.                                  |
| `Tab`               | Autocompleta nombres y rutas cuando es posible.                      |

