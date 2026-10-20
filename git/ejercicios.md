# Módulo práctico de Git y GitHub

En estos ejercicios pondremos en práctica los principales comandos de Git y las herramientas de colaboración de GitHub mediante ejercicios que simulan situaciones habituales durante el desarrollo de software.


## Ejercicio 1. Instalación y configuración de Git

Objetivo: Instalar Git, comprobar que funciona correctamente y configurar el nombre y correo electrónico que identificarán nuestros commits.

¿Qué es Git y para qué se utiliza?
Git es un sistema de control de versiones que permite registrar los cambios realizados en los archivos de un proyecto.

Gracias a Git podemos consultar versiones anteriores, recuperar archivos, trabajar en distintas ramas y colaborar sin perder el historial de cambios.

Git y GitHub no son lo mismo. Git es la herramienta de control de versiones; GitHub es una plataforma para alojar repositorios y colaborar en proyectos.

Pasos a seguir:

1. Descarga e instala Git desde su [sitio oficial](https://git-scm.com/downloads?utm_source=chatgpt.com).
2. Abre Git Bash, PowerShell o la terminal de Visual Studio Code.
3. Comprueba que Git esté instalado correctamente mediante `git --version`.
4. Configura tu nombre de usuario mediante `git config --global user.name`.
5. Configura tu correo electrónico mediante `git config --global user.email`.
6. Comprueba los valores configurados utilizando `git config --global --list`.


si todo esta bien veras algo como esto:

```sh
user.email=tu-email@ejemplo.com
user.name=Tu Nombre
```

## Ejercicio 2. Fork, Clone y Checkout

Objetivo: Aprender a crear una copia de un repositorio, descargarlo a nuestra computadora y trabajar con diferentes ramas.

Objetivo: Obtener una copia de un repositorio de GitHub, descargarla en nuestra computadora y aprender a cambiar de rama.
Conceptos fundamentales
- Fork: copia de un repositorio dentro de otra cuenta de GitHub.
- Clone: descarga un repositorio y su historial a nuestra computadora.
- Checkout: permite cambiar de rama o recuperar archivos de una versión determinada. Para cambiar de rama también podemos utilizar git switch.

Pasos a seguir:

1. Ingresa al repositorio [practica-github](https://github.com/Aborja-dev/practica-github?utm_source=chatgpt.com).
2. Realiza un `Fork` del repositorio en tu cuenta personal de GitHub. Para ello haz click en el boton fork en la esquina superior derecha abajo de la cinta de opciones
3. Copia la dirección HTTPS del Fork del repositorio.
4. Utiliza `git clone` para descargar el repositorio a tu computadora.
5. Entra al directorio del proyecto desde la terminal.
6. Consulta las ramas disponibles mediante `git branch -a`.
7. Utiliza `git checkout` para cambiar a la rama `main`, si no te encuentras ya en ella.
8. Crea una nueva rama llamada `practica` mediante `git checkout -b practica`.
9. Comprueba que te encuentras en la nueva rama.

si todo sale bien veras el nombre del repositorio y la rama en la consola
```sh
usuario@usuario:~/practica-github (practica) $
```

## Práctica adicional. Configuración de SSH

Objetivo: Configurar una conexión segura entre nuestra computadora y GitHub mediante claves SSH. Esto nos permite hacer peticiones pull y push sin necesidad de ingresar nuestras credenciales cada vez.

Pasos a seguir:

1. Comprueba si tienes claves SSH configuradas en tu computadora. Teclea el comando `ls -al ~/.ssh` en tu terminal. Si existe un directorio llamado .ssh, es posible que ya tengas claves SSH configuradas.
2. Genera una nueva clave SSH mediante `ssh-keygen -t ed25519`.
3. Localiza la clave pública generada. El archivo con la clave pública suele terminar en .pub, por ejemplo id_ed25519.pub. copiala con el comando clip < ~/.ssh/id_ed25519.pub
4. Ingresa a la configuración de tu cuenta de GitHub. Para ello haz click en tu foto de perfil en la esquina superior derecha y luego en Settings.
5. Agrega tu clave pública en Settings → SSH and GPG keys.
6. Verifica la conexión utilizando `ssh -T git@github.com`.
7. Consulta la dirección de tu repositorio remoto mediante `git remote -v`.
8. Cambia la dirección del remoto de HTTPS a SSH mediante `git remote set-url origin`, si corresponde.
9. Comprueba que la nueva dirección se configuró correctamente.

## Solución al error de conexión SSH

Si al intentar conectarte a GitHub aparece el siguiente error:

kex_exchange_identification: read: Software caused connection abort

Es posible que la conexión SSH esté siendo bloqueada a través del puerto predeterminado 22. Una alternativa es configurar SSH para conectarse a GitHub mediante el puerto 443.

Para hacerlo, sigue estos pasos:

Abre el Explorador de archivos y dirígete a la carpeta C:\Users\tu-usuario\.ssh, reemplazando tu-usuario por tu nombre de usuario de Windows.

Busca el archivo config. Si no existe, crea un archivo nuevo con ese nombre, sin extensión .txt.

Abre el archivo config con el Bloc de notas.

Agrega el siguiente contenido:

```
Host github.com
    HostName ssh.github.com
    Port 443
    User git
```

Guarda los cambios y abre una terminal.

Comprueba la conexión ejecutando:

ssh -T git@github.com

Si es la primera vez que te conectas, SSH puede solicitarte que confirmes la autenticidad del servidor. Verifica que la huella digital corresponda a una de las claves oficiales de GitHub. Si coincide, escribe yes y presiona Enter.

Si la conexión se establece correctamente, aparecerá un mensaje similar al siguiente:

Hi usuario! You've successfully authenticated, but GitHub does not provide shell access.

Esto confirma que la autenticación SSH con GitHub funciona correctamente.

Nota: Esta configuración utiliza el puerto 443 en lugar del 22 para las conexiones SSH dirigidas a github.com. Es una alternativa útil cuando el puerto predeterminado está bloqueado, aunque no resuelve todos los posibles problemas de conexión.

## Ejercicio 3. Flujo básico de trabajo (Staging, Commit y Push)

Objetivo: Aprender a registrar modificaciones utilizando el área de preparación, crear commits y publicar los cambios en un repositorio remoto.

Pasos a seguir:

1. Comprueba que te encuentras en la rama `practica`.
2. Abre el archivo `git/marvel.js`.
3. Agrega dos nuevos héroes al arreglo, por ejemplo, Wolverine y Storm.
4. Consulta el estado del repositorio mediante `git status`.
5. Examina las modificaciones utilizando `git diff`. Para salir de diff presiona q en la consola si presionas enter te mostrara mas cambios hasta el final 
6. Agrega los cambios al área de preparación mediante `git add .`.
7. Crea un commit con un mensaje que describa las modificaciones realizadas con `git commit -m ""`.
8. Agrega el repositorio remoto mediante `git remote add origin <url>`.
9. Envía los cambios a tu Fork utilizando `git push origin practica`.
10. Comprueba en GitHub que los cambios se publicaron correctamente.

sitodo sale bien veras algo como esto en la consola:
```sh
Enumerating objects: 7, done.
Counting objects: 100% (7/7), done.
Delta compression using up to 8 threads
Compressing objects: 100% (4/4), done.
Writing objects: 100% (4/4), 460 bytes | 230.00 KiB/s, done.
Total 4 (delta 2), reused 0 (delta 0), pack-reused 0 (from 0)
remote: Resolving deltas: 100% (2/2), completed with 2 local objects.
remote: 
remote: Create a pull request for 'practica' on GitHub by visiting:
remote:      https://github.com/Aborja-dev/practica-github/pull/new/practica
remote:
To github.com:Aborja-dev/practica-github.git
 * [new branch]      practica -> practica

```

## Ejercicio 4. Sincronización e integración (Fetch y Merge)

Objetivo: Comprender cómo obtener cambios de un repositorio remoto e integrar modificaciones de diferentes ramas.

Consigna:

1. Comprueba que te encuentras en la rama `practica`.
2. Ejecuta `git fetch` para descargar las referencias y los cambios disponibles en el repositorio remoto, sin integrarlos automáticamente.
3. Consulta las ramas disponibles mediante `git branch -a`.
4. Localiza la rama `dc`. Si existe únicamente como rama remota, crea una rama local a partir de ella `git checkout -b dc`.
5. Regresa a la rama `practica`.
6. Realiza un `git merge` de la rama `dc` hacia tu rama actual.
7. Examina los cambios o conflictos que puedan producirse.
8. Crea un archivo heroes.js y copia ambos arrays dentro
8. Verifica que los cambios se hayan integrado correctamente.
9. Consulta el historial mediante `git log --oneline --graph`.
10. Publica la rama actualizada en tu Fork.

Nota: Si la rama `dc` pertenece al repositorio original y no aparece en tu Fork, primero deberás agregar dicho repositorio como remoto `upstream` y obtener sus referencias.

Si todo sale bien veras un archivo dc.js en tu editor de codigo una vez hagas el comit si ingrsas al repositorio veras un commit de merge ademas de los archivos dc y heroes


## Ejercicio 5. Recuperación ante errores (Merge y Reset)

Objetivo: Aprender a recuperar una versión anterior del repositorio después de una integración incorrecta.

pasos a seguir:

1. Crea una rama independiente llamada `practica/reset` a partir de tu rama de trabajo, para evitar modificar accidentalmente una rama compartida.
2. Realiza un `git merge` con la rama `error` para simular una integración problemática.
3. Examina los cambios o conflictos producidos por la operación.
4. Consulta el historial mediante `git log --oneline`.
5. Localiza el commit identificado con el mensaje `checkout ok`.
6. Utiliza `git reset --hard` junto con el identificador de ese commit para regresar al estado anterior.
7. Verifica que el repositorio haya recuperado la versión esperada.
8. Actualiza el repositorio remoto mediante `git push --force-with-lease`.
9. Consulta nuevamente el historial para comprobar los resultados.

Precaución: `git reset --hard` descarta cambios locales de archivos rastreados y `git push --force-with-lease` puede reescribir el historial remoto. Realiza este ejercicio únicamente en una rama desechable y nunca sobre una rama compartida sin autorización.

Nota: Si la fusión se detiene debido a conflictos, primero deberás resolverlos y completar la integración para practicar la recuperación de un commit de fusión. También puedes utilizar `git merge --abort` para cancelar una integración que todavía no se ha completado.

Si todo sale bien al ingresar al repositorio y ver el array de vengadores veras solo 5 objetos y en el log veras que el ultimo commit es el de merge

usamos git reset en vez de corregir los cambios manuelamente por que se trata de informacion que no sabemos ni podemos saber ej: cuando se unio Thor que id tenia iron man, etc



## Ejercicio 6. Trabajo colaborativo (Pull Request)

Objetivo: Aprender a proponer cambios a un repositorio, solicitar su revisión e integrarlos mediante un Pull Request.

pasos a seguir:

1. Actualiza tu rama principal con los cambios más recientes del repositorio original.
2. Crea una nueva rama llamada `feat/mis-heroes`.
3. Crea un archivo personajes.js.
4. Agrega un array con los nombres que quieras.
5. Consulta los cambios mediante `git status` y `git diff`.
6. Prepara las modificaciones mediante `git add`.
7. Crea un commit con un mensaje descriptivo.
8. Publica la nueva rama en tu Fork mediante `git push`.
9. Ingresa a GitHub y abre la sección Pull requests.
10. Crea un Pull Request desde la rama `feat/mis-heroes` de tu Fork hacia `main` del repositorio original.
11. Agrega un título y una descripción que expliquen los cambios realizados.
12. Examina la pestaña Files changed para comprobar qué archivos se modificarán.
13. Solicita una revisión y realiza las correcciones que sean necesarias.
14. Una vez aprobado, integra el Pull Request si tienes autorización; en caso contrario, deja la integración a cargo del responsable del repositorio.

si todo sale bien el pull request se fusionara y veras el commit en el historial ademas de tu archivo en el repositorio orginal
