
GitHub permite que varios desarrolladores trabajen en un mismo proyecto sin necesidad de modificar directamente el código de los demás.

Para organizar este trabajo se utilizan herramientas como **Forks, Branches, Pull Requests, revisiones de código y permisos de acceso**.

### 1. Fork

Un **Fork** es una copia de un repositorio que se crea dentro de nuestra cuenta de GitHub.

Permite realizar modificaciones de manera independiente, sin afectar directamente el repositorio original.

Es especialmente útil cuando queremos contribuir a proyectos en los que no tenemos permisos de escritura.

Para crear un Fork:

1. Abre el repositorio al que deseas contribuir.
    
2. Selecciona **Fork**.
    
3. Elige tu cuenta como destino.
    
4. Clona tu Fork para trabajar localmente.
    
5. Realiza tus cambios y envíalos a tu Fork.
    
6. Abre un Pull Request hacia el repositorio original.
    

**Diferencia entre Fork y Branch:** una rama permite desarrollar cambios dentro del mismo repositorio, mientras que un Fork crea otro repositorio vinculado al original.

### 2. Pull Request (PR)

Un **Pull Request** es una solicitud para integrar los cambios de una rama en otra.

Permite que otros desarrolladores revisen el código, propongan modificaciones y aprueben los cambios antes de integrarlos.

#### Crear un Pull Request

1. Crea una rama para trabajar en una funcionalidad.
    
2. Realiza los cambios y crea los commits necesarios.
    
3. Envía tu rama a GitHub mediante `git push`.
    
4. Abre la sección **Pull requests** del repositorio.
    
5. Selecciona **New pull request**.
    
6. Selecciona las ramas de origen y destino.
    
7. Agrega un título y una descripción.
    
8. Selecciona **Create pull request**.
    

#### Estados y revisiones

- **Open:** el PR está abierto y pendiente de integración o cierre.
    
- **Draft:** el trabajo todavía está en desarrollo y no está listo para integrarse.
    
- **Approved:** un revisor ha aprobado los cambios.
    
- **Changes requested:** un revisor ha solicitado modificaciones.
    
- **Merged:** los cambios fueron integrados.
    
- **Closed:** el PR fue cerrado; puede haberse integrado o descartado.
    

Un PR puede recibir diferentes revisiones durante su desarrollo.

### 3. Convenciones de Pull Requests

Las convenciones permiten mantener un historial organizado y facilitar la revisión de los cambios.

#### Convenciones de nombres

Una práctica habitual es utilizar prefijos que indiquen el tipo de cambio:

|Prefijo|Uso|
|---|---|
|`feat:`|Nueva funcionalidad.|
|`fix:`|Corrección de errores.|
|`docs:`|Cambios en documentación.|
|`refactor:`|Reorganización de código sin cambiar su comportamiento previsto.|
|`test:`|Agregar o modificar pruebas.|
|`chore:`|Tareas de mantenimiento.|

Estas convenciones están inspiradas en _Conventional Commits_, aunque su aplicación a títulos de PR es una decisión del equipo.

Ejemplos:

```
feat: agregar formulario de registro
fix: corregir validación del correo
docs: actualizar instrucciones de instalación
```

#### Convenciones para describir cambios

Una buena descripción debe explicar qué se modificó, por qué y cómo se comprobó su funcionamiento.

Ejemplo de plantilla:

```
## Descripción

Agrega validación de campos al formulario de registro.

## Cambios realizados

- Validación del correo electrónico.
- Mensajes de error.
- Pruebas del formulario.

## Pruebas

- [x] Verificar campos vacíos.
- [x] Verificar correo inválido.
- [x] Probar registro exitoso.

## Referencias

Closes #25
```

La referencia `Closes #25` permite vincular el PR con un Issue y cerrarlo automáticamente cuando se integra en la rama predeterminada, si se cumplen las condiciones de GitHub.

### 4. Estrategias de integración

GitHub ofrece diferentes formas de integrar un Pull Request.

- **Merge commit:** combina las ramas creando un commit de fusión cuando corresponde. Conserva la estructura del historial.
    
- **Squash and merge:** combina los commits del PR en un único commit nuevo, facilitando un historial resumido.
    
- **Rebase and merge:** vuelve a aplicar los commits sobre la rama de destino sin crear un commit de fusión, manteniendo un historial lineal.
    

La estrategia elegida depende de las convenciones del equipo y de la configuración del repositorio.

### 5. Permisos y roles

GitHub permite asignar diferentes niveles de acceso para controlar quién puede consultar, modificar o administrar un repositorio.

En los repositorios de organizaciones existen cinco roles principales:

|Rol|Permisos principales|
|---|---|
|**Read**|Consultar el repositorio, participar en discusiones y proponer cambios mediante PR.|
|**Triage**|Administrar Issues y Pull Requests sin modificar directamente el código.|
|**Write**|Enviar cambios y colaborar directamente en el código.|
|**Maintain**|Administrar el repositorio y sus tareas de mantenimiento sin acceso administrativo completo.|
|**Admin**|Control total, incluyendo permisos, configuraciones sensibles y eliminación del repositorio.|

Los permisos concretos pueden depender de las reglas del repositorio y de la configuración de la organización.

### 6. Participantes de un Pull Request

Además de los roles de acceso, existen diferentes funciones dentro del proceso de revisión.

- **Author:** persona que crea el Pull Request y propone los cambios.
    
- **Reviewer:** persona encargada de revisar el código y proporcionar comentarios o una evaluación.
    
- **Assignee:** persona responsable de dar seguimiento al PR.
    
- **Maintainer:** persona encargada de mantener el proyecto y coordinar las contribuciones.
    
- **Code Owner:** persona o equipo definido como responsable de determinados archivos o directorios.
    

Estas funciones no equivalen necesariamente a permisos de acceso. Por ejemplo, ser Reviewer no significa ser administrador.

Los Code Owners pueden definirse mediante un archivo `CODEOWNERS`, permitiendo solicitar automáticamente revisiones cuando se modifican archivos bajo su responsabilidad.

### 7. Protección de ramas

Para evitar modificaciones accidentales, GitHub permite establecer reglas sobre ramas importantes, como `main`.

Dependiendo de la configuración, podemos exigir:

- Crear un Pull Request antes de integrar cambios.
    
- Obtener una o varias aprobaciones.
    
- Superar pruebas automáticas.
    
- Resolver conversaciones de revisión.
    
- Evitar modificaciones directas o eliminaciones de ramas protegidas.
    

Estas reglas ayudan a mantener la calidad del código y evitar que los cambios lleguen a la rama principal sin revisión.

### 8. Flujo básico de colaboración

Un flujo sencillo para trabajar en equipo consiste en crear una rama por funcionalidad y utilizar Pull Requests para integrar los cambios.

```
# Actualizar la rama principal
git switch main
git pull

# Crear una rama de trabajo
git switch -c feat/formulario

# Preparar y registrar cambios
git add .
git commit -m "feat: agregar formulario"

# Enviar la rama a GitHub
git push -u origin feat/formulario
```

Después de enviar la rama, creamos un Pull Request en GitHub.

El proceso habitual es:

1. El desarrollador crea una rama y realiza los cambios.
    
2. Abre un Pull Request hacia `main`.
    
3. Los reviewers revisan el código.
    
4. El autor corrige los problemas encontrados.
    
5. Los revisores autorizados aprueban los cambios.
    
6. Una persona con permisos suficientes integra el PR.
    
7. La rama de trabajo puede eliminarse una vez completada la integración.
    

Este flujo permite que varios desarrolladores trabajen en paralelo manteniendo un control sobre los cambios incorporados al proyecto.