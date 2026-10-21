# GitHub

## ¿Qué es GitHub?

**GitHub** es una plataforma que permite alojar repositorios Git en la nube, compartir código y colaborar con otros desarrolladores.

Además de almacenar proyectos, ofrece herramientas para revisar cambios, administrar tareas y trabajar en equipo.

### Diferencias entre Git y GitHub

Aunque están relacionados, Git y GitHub no son lo mismo.

|Git|GitHub|
|---|---|
|Es un sistema de control de versiones.|Es una plataforma de alojamiento y colaboración.|
|Funciona localmente.|Es un servicio en línea.|
|Registra cambios mediante commits.|Permite compartir y revisar esos cambios.|
|No necesita una cuenta.|Requiere una cuenta para crear repositorios propios.|
|Se utiliza desde la terminal o aplicaciones gráficas.|Se utiliza desde la web, aplicaciones y herramientas de desarrollo.|

Git es como el historial de versiones de un documento, que permite guardar cambios y recuperar versiones anteriores. GitHub es como una biblioteca en línea, donde puedes almacenar esos documentos, compartirlos y trabajar en ellos con otras personas.

## 1. Conceptos básicos

### Repositorio remoto

Un repositorio remoto es una versión de nuestro repositorio Git alojada en otro lugar, como GitHub.

Podemos conectarlo con nuestro repositorio local para enviar y recibir cambios.

### Visibilidad

GitHub permite configurar la visibilidad de nuestros repositorios:

- **Public:** cualquier persona puede consultar el repositorio.
    
- **Private:** únicamente las personas autorizadas pueden acceder al repositorio.
    

Un repositorio público puede ser consultado y clonado por otros usuarios, pero esto no significa que tengan permiso para modificarlo directamente.

### Fork

Un **fork** es una copia de un repositorio de GitHub creada bajo nuestra propia cuenta.

Permite experimentar o proponer modificaciones sin afectar directamente el repositorio original.

### Pull Request

Un **Pull Request (PR)** es una solicitud para integrar los cambios de una rama en otra.

Permite revisar el código, discutir modificaciones y aprobar cambios antes de incorporarlos.

### Merge

Un **merge** es una operación de Git que permite integrar los cambios de diferentes ramas.

En GitHub, normalmente se realiza después de revisar y aprobar un Pull Request.

Si dos cambios modifican partes incompatibles del mismo código, puede producirse un **conflicto**, que deberá resolverse manualmente.

---

## 2. Primeros pasos con GitHub

Antes de comenzar, asegúrate de tener instalado Git y configurado tu nombre y correo electrónico.

### Crear una cuenta

1. Ingresa a [GitHub](https://github.com/).
    
2. Crea una cuenta o inicia sesión.
    
3. Verifica tu dirección de correo electrónico si es necesario.
    

### Configurar una SSH Key

Una clave SSH permite autenticarnos con GitHub de forma segura sin introducir nuestras credenciales cada vez que enviamos cambios.

Las claves SSH funcionan mediante un par de archivos:

- **Clave pública:** puede compartirse con GitHub.
    
- **Clave privada:** debe permanecer protegida en nuestra computadora.
    

#### 1. Generar una clave SSH

Abre Git Bash y ejecuta:

```
ssh-keygen -t ed25519 -C "tu@email.com"
```

Sustituye el correo por el de tu cuenta.

Presiona `Enter` para aceptar la ubicación predeterminada, siempre que no sobrescribas una clave existente, y configura una contraseña de protección (_passphrase_).

#### 2. Agregar la clave al agente SSH

Ejecuta:

```
eval "$(ssh-agent -s)"
ssh-add ~/.ssh/id_ed25519
```

El agente SSH permite administrar las claves durante la sesión.

#### 3. Copiar la clave pública

```
cat ~/.ssh/id_ed25519.pub | clip
```

Este comando copia la clave pública al portapapeles de Windows.

**Importante:** Nunca compartas el archivo `id_ed25519` sin la extensión `.pub`, ya que contiene tu clave privada.

#### 4. Registrar la clave en GitHub

1. Abre GitHub y entra a **Settings**.
    
2. Selecciona **SSH and GPG keys**.
    
3. Haz clic en **New SSH key**.
    
4. Selecciona **Authentication Key**.
    
5. Asigna un nombre y pega tu clave pública.
    
6. Guarda los cambios.
    

#### 5. Verificar la conexión

```
ssh -T git@github.com
```

si la conexión marca el siguiente error kex_exchange_identification: read: Software caused connection abort es necesario configurar el puerto apra ello siga estos pasos
1 ve a C:\Users\tu-usaurio\.ssh
2 entra al archivo config o crealo si no existe
3 abrelo con bloc de notas
4 pega este fragmento
Host github.com
       Hostname ssh.github.com
       Port 443
       User git
5 prueba con ssh -T git@github.com te pedira permiso escribe yes para aceptar

La primera vez puede solicitarte confirmar la identidad del servidor. Comprueba su huella digital antes de aceptarla.

Si la autenticación funciona, GitHub mostrará un mensaje de bienvenida.

Documentación: [Conectar GitHub mediante SSH](https://docs.github.com/es/authentication/connecting-to-github-with-ssh).

---


### Diferencias entre HTTPS y SSH

GitHub permite conectarnos a un repositorio remoto mediante dos protocolos: **HTTPS y SSH**.

Ambos permiten enviar y descargar cambios de manera segura, pero utilizan diferentes métodos de autenticación.

- **HTTPS:** utiliza una conexión cifrada y permite autenticarse mediante credenciales, como un token de acceso personal o un gestor de credenciales.
    
- **SSH:** utiliza un par de claves criptográficas, una pública y otra privada, para autenticar nuestra computadora con GitHub.

HTTPS es más sencillo de configurar, ya que no requiere claves SSH y utiliza tokens o gestores de credenciales para autenticarse. Por otro lado, SSH requiere configurar un par de claves criptográficas, pero facilita la autenticación al trabajar frecuentemente con GitHub sin necesidad de introducir credenciales en cada operación.
## 3. Crear un repositorio

### Desde GitHub

1. Inicia sesión en GitHub.
    
2. Haz clic en **New repository**.
    
3. Escribe un nombre para tu proyecto.
    
4. Selecciona su visibilidad.
    
5. Haz clic en **Create repository**.
    

### Conectar un proyecto local

Si ya tenemos un proyecto inicializado con Git, podemos conectarlo al repositorio remoto.

```
git remote add origin git@github.com:USUARIO/REPOSITORIO.git
```

Sustituye `USUARIO` y `REPOSITORIO` por los datos correspondientes.

Para comprobar la conexión:

```
git remote -v
```

Si la rama principal se llama `main`, podemos publicar nuestros commits:

```
git push -u origin main
```

**Nota:** Para este ejemplo, el repositorio remoto debe estar vacío o tener un historial compatible con el local.

### Clonar un repositorio

También podemos descargar un repositorio existente:

```
git clone git@github.com:USUARIO/REPOSITORIO.git
```

Esto crea una copia local con los archivos y el historial del proyecto.

---

## 4. Cómo hacer commits

Un commit permite registrar los cambios realizados en nuestro proyecto.

El flujo habitual consiste en modificar archivos, preparar los cambios y crear un commit.

### 1. Consultar el estado

```
git status
```

Muestra los archivos nuevos, modificados y preparados para el siguiente commit.

### 2. Preparar los cambios

Para agregar un archivo específico:

```
git add README.md
```

Para agregar todos los cambios del directorio actual:

```
git add .
```

### 3. Crear un commit

```
git commit -m "Actualizar documentación"
```

El mensaje debe describir brevemente los cambios realizados.

### 4. Enviar los cambios a GitHub

```
git push
```

Este comando envía los commits locales al repositorio remoto asociado a nuestra rama.

### 5. Obtener cambios del remoto

```
git pull
```

Obtiene los cambios del repositorio remoto y los integra en la rama actual.

---

## 5. Manejo de versiones

Git permite consultar versiones anteriores, cambiar de rama, recuperar archivos y reorganizar el historial del proyecto.

### Consultar el historial

```
git log --oneline
```

Muestra una lista resumida de los commits junto con sus identificadores.

### Checkout

`git checkout` permite cambiar de rama o recuperar archivos y estados anteriores.

Para visitar temporalmente un commit:

```
git checkout HASH
```

Sustituye `HASH` por el identificador del commit.

Esto permite consultar una versión anterior del proyecto, pero deja el repositorio en un estado llamado _detached HEAD_.

Para regresar a la rama principal:

```
git switch main
```

Actualmente se recomienda utilizar `git switch` para cambiar de rama y `git restore` para recuperar archivos, porque sus funciones son más específicas.

### Reset

`git reset` permite mover la referencia de la rama actual a otro commit y, según la opción utilizada, modificar el área de preparación o los archivos de trabajo.

|Comando|Resultado|
|---|---|
|`git reset --soft HEAD~1`|Deshace el último commit y conserva los cambios preparados.|
|`git reset --mixed HEAD~1`|Deshace el último commit y conserva los cambios sin preparar.|
|`git reset --hard HEAD~1`|Deshace el último commit y descarta los cambios correspondientes del directorio de trabajo.|

**Precaución:** `--hard` puede provocar la pérdida de cambios locales. Evita utilizarlo si no estás seguro de qué archivos se modificarán.

Si necesitas deshacer un commit que ya compartiste con otros desarrolladores, normalmente es preferible utilizar:

```
git revert HASH
```

Este comando crea un nuevo commit que revierte los cambios del commit indicado, sin reescribir el historial existente.

### Rebase

`git rebase` permite reorganizar commits y trasladar los cambios de una rama para que partan de otro commit.

Por ejemplo, estando en una rama de trabajo:

```
git switch nueva-funcionalidad
git rebase main
```

Esto vuelve a aplicar los commits de `nueva-funcionalidad` sobre el estado actual de `main`.

También podemos utilizar rebase interactivo:

```
git rebase -i HEAD~3
```

Este comando permite revisar y modificar los últimos tres commits, por ejemplo, para combinarlos, reordenarlos o modificar sus mensajes.

**Precaución:** Rebase reescribe el historial. Evita aplicarlo sobre commits compartidos sin coordinarte con los demás colaboradores.

### Diferencias entre Merge y Rebase

- **Merge:** integra dos líneas de desarrollo y puede crear un commit de fusión, conservando la estructura de sus historiales.
    ![615](data:image/svg+xml;charset=utf-8,%3Csvg%20font-family%3D%22-apple-system-body%2C%20ui-sans-serif%2C%20-apple-system%2C%20system-ui%2C%20%26quot%3BSegoe%20UI%26quot%3B%2C%20Helvetica%2C%20%26quot%3BApple%20Color%20Emoji%26quot%3B%2C%20Arial%2C%20sans-serif%2C%20%26quot%3BSegoe%20UI%20Emoji%26quot%3B%2C%20%26quot%3BSegoe%20UI%20Symbol%26quot%3B%22%20font-weight%3D%22400%22%20data-d-component%3D%22svg%22%20fill%3D%22currentColor%22%20style%3D%22color%3Argb\(13%2C%2013%2C%2013\)%22%20viewBox%3D%220%200%20330%20126%22%20width%3D%22100%25%22%20xmlns%3D%22http%3A%2F%2Fwww.w3.org%2F2000%2Fsvg%22%3E%3Ccircle%20cx%3D%2230%22%20cy%3D%2289%22%20r%3D%2213%22%20fill%3D%22%23477FC8%22%2F%3E%3Ctext%20x%3D%2230%22%20y%3D%2293%22%20text-anchor%3D%22middle%22%20font-size%3D%2211%22%20fill%3D%22white%22%20font-weight%3D%22600%22%3EA%3C%2Ftext%3E%3Ccircle%20cx%3D%2291%22%20cy%3D%2289%22%20r%3D%2213%22%20fill%3D%22%23477FC8%22%2F%3E%3Ctext%20x%3D%2291%22%20y%3D%2293%22%20text-anchor%3D%22middle%22%20font-size%3D%2211%22%20fill%3D%22white%22%20font-weight%3D%22600%22%3EB%3C%2Ftext%3E%3Ccircle%20cx%3D%22153%22%20cy%3D%2289%22%20r%3D%2213%22%20fill%3D%22%23477FC8%22%2F%3E%3Ctext%20x%3D%22153%22%20y%3D%2293%22%20text-anchor%3D%22middle%22%20font-size%3D%2211%22%20fill%3D%22white%22%20font-weight%3D%22600%22%3EC%3C%2Ftext%3E%3Ccircle%20cx%3D%22213%22%20cy%3D%2289%22%20r%3D%2213%22%20fill%3D%22%23477FC8%22%2F%3E%3Ctext%20x%3D%22213%22%20y%3D%2293%22%20text-anchor%3D%22middle%22%20font-size%3D%2211%22%20fill%3D%22white%22%20font-weight%3D%22600%22%3ED%3C%2Ftext%3E%3Ccircle%20cx%3D%22275%22%20cy%3D%2289%22%20r%3D%2213%22%20fill%3D%22%2313876E%22%2F%3E%3Ctext%20x%3D%22275%22%20y%3D%2293%22%20text-anchor%3D%22middle%22%20font-size%3D%2211%22%20fill%3D%22white%22%20font-weight%3D%22600%22%3EM%3C%2Ftext%3E%3Ccircle%20cx%3D%22153%22%20cy%3D%2229%22%20r%3D%2213%22%20fill%3D%22%23D58A30%22%2F%3E%3Ctext%20x%3D%22153%22%20y%3D%2233%22%20text-anchor%3D%22middle%22%20font-size%3D%2211%22%20fill%3D%22white%22%20font-weight%3D%22600%22%3EE%3C%2Ftext%3E%3Ccircle%20cx%3D%22213%22%20cy%3D%2229%22%20r%3D%2213%22%20fill%3D%22%23D58A30%22%2F%3E%3Ctext%20x%3D%22213%22%20y%3D%2233%22%20text-anchor%3D%22middle%22%20font-size%3D%2211%22%20fill%3D%22white%22%20font-weight%3D%22600%22%3EF%3C%2Ftext%3E%3Cpath%20d%3D%22M43%2089%20H78%20M104%2089%20H140%20M166%2089%20H200%20M226%2089%20H262%22%20stroke%3D%22currentColor%22%20opacity%3D%22.55%22%20stroke-width%3D%222%22%20fill%3D%22none%22%2F%3E%3Cpath%20d%3D%22M91%2076%20Q99%2029%20140%2029%20M166%2029%20H200%20M226%2029%20Q275%2029%20275%2076%22%20stroke%3D%22%23D58A30%22%20stroke-width%3D%222%22%20fill%3D%22none%22%2F%3E%3Ctext%20x%3D%22305%22%20y%3D%2293%22%20font-size%3D%2210%22%20fill%3D%22currentColor%22%3Emain%3C%2Ftext%3E%3Ctext%20x%3D%22236%22%20y%3D%2224%22%20font-size%3D%2210%22%20fill%3D%22currentColor%22%3Erama%3C%2Ftext%3E%3C%2Fsvg%3E)
- **Rebase:** vuelve a aplicar commits sobre otra base, creando un historial más lineal, pero modificando sus identificadores.
    ![604](data:image/svg+xml;charset=utf-8,%3Csvg%20font-family%3D%22-apple-system-body%2C%20ui-sans-serif%2C%20-apple-system%2C%20system-ui%2C%20%26quot%3BSegoe%20UI%26quot%3B%2C%20Helvetica%2C%20%26quot%3BApple%20Color%20Emoji%26quot%3B%2C%20Arial%2C%20sans-serif%2C%20%26quot%3BSegoe%20UI%20Emoji%26quot%3B%2C%20%26quot%3BSegoe%20UI%20Symbol%26quot%3B%22%20font-weight%3D%22400%22%20data-d-component%3D%22svg%22%20fill%3D%22currentColor%22%20style%3D%22color%3Argb\(13%2C%2013%2C%2013\)%22%20viewBox%3D%220%200%20330%20126%22%20width%3D%22100%25%22%20xmlns%3D%22http%3A%2F%2Fwww.w3.org%2F2000%2Fsvg%22%3E%3Cpath%20d%3D%22M30%2072%20H294%22%20stroke%3D%22currentColor%22%20stroke-width%3D%222%22%20opacity%3D%22.5%22%2F%3E%3Ccircle%20cx%3D%2230%22%20cy%3D%2272%22%20r%3D%2214%22%20fill%3D%22%23477FC8%22%2F%3E%3Ctext%20x%3D%2230%22%20y%3D%2276%22%20font-size%3D%2211%22%20text-anchor%3D%22middle%22%20fill%3D%22white%22%20font-weight%3D%22600%22%3EA%3C%2Ftext%3E%3Ccircle%20cx%3D%2286%22%20cy%3D%2272%22%20r%3D%2214%22%20fill%3D%22%23477FC8%22%2F%3E%3Ctext%20x%3D%2286%22%20y%3D%2276%22%20font-size%3D%2211%22%20text-anchor%3D%22middle%22%20fill%3D%22white%22%20font-weight%3D%22600%22%3EB%3C%2Ftext%3E%3Ccircle%20cx%3D%22142%22%20cy%3D%2272%22%20r%3D%2214%22%20fill%3D%22%23477FC8%22%2F%3E%3Ctext%20x%3D%22142%22%20y%3D%2276%22%20font-size%3D%2211%22%20text-anchor%3D%22middle%22%20fill%3D%22white%22%20font-weight%3D%22600%22%3EC%3C%2Ftext%3E%3Ccircle%20cx%3D%22198%22%20cy%3D%2272%22%20r%3D%2214%22%20fill%3D%22%23477FC8%22%2F%3E%3Ctext%20x%3D%22198%22%20y%3D%2276%22%20font-size%3D%2211%22%20text-anchor%3D%22middle%22%20fill%3D%22white%22%20font-weight%3D%22600%22%3ED%3C%2Ftext%3E%3Ccircle%20cx%3D%22250%22%20cy%3D%2272%22%20r%3D%2214%22%20fill%3D%22%23D58A30%22%2F%3E%3Ctext%20x%3D%22250%22%20y%3D%2276%22%20font-size%3D%2211%22%20text-anchor%3D%22middle%22%20fill%3D%22white%22%20font-weight%3D%22600%22%3EE'%3C%2Ftext%3E%3Ccircle%20cx%3D%22300%22%20cy%3D%2272%22%20r%3D%2214%22%20fill%3D%22%23D58A30%22%2F%3E%3Ctext%20x%3D%22300%22%20y%3D%2276%22%20font-size%3D%2211%22%20text-anchor%3D%22middle%22%20fill%3D%22white%22%20font-weight%3D%22600%22%3EF'%3C%2Ftext%3E%3Ctext%20x%3D%22190%22%20y%3D%2238%22%20font-size%3D%2211%22%20fill%3D%22currentColor%22%3Emain%3C%2Ftext%3E%3Ctext%20x%3D%22237%22%20y%3D%22109%22%20font-size%3D%2210%22%20fill%3D%22currentColor%22%3ECommits%20reaplicados%3C%2Ftext%3E%3C%2Fsvg%3E)

Ambos permiten integrar trabajo, aunque lo hacen de manera diferente.

---

## 6. Primera práctica con github

Vamos a crear un repositorio, registrar cambios y publicarlo en GitHub.

### Crear el proyecto

Abre Git Bash y ejecuta:

```
mkdir mi-primer-repositorio
cd mi-primer-repositorio
git init -b main
```

### Crear el primer archivo

```
echo "# Mi primer repositorio" > README.md
```

### Registrar los cambios

```
git add README.md
git commit -m "Crear README inicial"
```

### Publicar el repositorio

Primero, crea un repositorio vacío en GitHub.

Después, conecta el proyecto local:

```
git remote add origin git@github.com:USUARIO/REPOSITORIO.git
git push -u origin main
```

### Crear una nueva versión

Modifica el archivo `README.md` y ejecuta:

```
git status
git diff
git add README.md
git commit -m "Actualizar README"
git push
```

Finalmente, consulta el historial:

```
git log --oneline
```

Si todos los comandos funcionan correctamente, habrás creado un repositorio local, registrado dos versiones de tu proyecto y publicado sus cambios en GitHub.
