# Módulo práctico de Git

En este módulo pondremos en práctica los principales comandos de Git mediante ejercicios que simulan situaciones habituales durante el desarrollo de software.

El objetivo es aprender a gestionar cambios, sincronizar repositorios, integrar ramas y recuperar versiones anteriores.

## Ejercicio 1. Configuración y conexión

**Objetivo:** Configurar nuestra identidad de Git y establecer una conexión con el repositorio remoto.

**Consigna:**

1. Configura tu nombre de usuario (`user.name`) y correo electrónico (`user.email`) en Git.
2. Genera una clave SSH y agrégala a tu cuenta de GitHub o GitLab.
3. Verifica que la conexión SSH funcione correctamente.
4. Ejecuta `git pull` sobre la rama principal para asegurarte de tener la versión más reciente del repositorio.

## Ejercicio 2. Flujo básico de trabajo (Staging y Commit)

**Objetivo:** Aprender a registrar modificaciones utilizando el área de preparación y los commits.

**Consigna:**

1. Abre el archivo `marvel.js`.
2. Agrega dos nuevos héroes al array, por ejemplo, *Wolverine* y *Storm*.
3. Consulta el estado del repositorio mediante `git status`.
4. Agrega los cambios al área de preparación (*staging area*).
5. Crea un commit con un mensaje que describa las modificaciones realizadas.

## Ejercicio 3. Sincronización e integración (Fetch y Merge)

**Objetivo:** Comprender cómo obtener cambios de un repositorio remoto e integrar modificaciones de diferentes ramas.

**Consigna:**

1. Ejecuta `git fetch` para descargar las referencias y los cambios disponibles en el repositorio remoto, sin integrarlos automáticamente.
2. Comprueba qué ramas se encuentran disponibles.
3. Realiza un `git merge` de la rama `dc` hacia tu rama actual.
4. Verifica que los cambios se hayan integrado correctamente.

## Ejercicio 4. Recuperación ante errores (Merge y Reset)

**Objetivo:** Aprender a recuperar una versión anterior del repositorio después de una integración incorrecta.

**Consigna:**

1. Realiza un `git merge` con la rama `error` para simular una integración problemática.
2. Examina los cambios o conflictos producidos por la operación.
3. Localiza en el historial el commit identificado con el mensaje `checkout ok`.
4. Utiliza `git reset --hard` para regresar al estado de ese commit.
5. Verifica que el repositorio haya recuperado la versión esperada.
6. actualizar el repositorio remoto con la version correcta, utiliza `git push --force-with-lease` para publicar el historial restaurado.

**Precaución:** `git reset --hard` descarta cambios locales y `git push --force-with-lease` puede reescribir el historial remoto. Realiza este ejercicio únicamente en una rama de práctica y nunca sobre una rama compartida sin autorización.


