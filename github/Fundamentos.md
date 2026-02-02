# Fundamentos

## Activador (Eventos)

### 1. Eventos de Código (Git)
Son los más comunes para CI/CD (Integración y Despliegue Continuo):

__push:__ 

Se activa cuando subes código a una rama o etiquetas (tags). Es el estándar para correr tests automáticamente.

__pull_request:__ 

Se activa cuando se abre, actualiza o cierra un PR. Ideal para validar código antes de mezclarlo.

Es el evento más versátil para flujos de trabajo en equipo.

- __labeled:__ Se dispara justo cuando añades una etiqueta (label) al PR.

- __unlabeled:__ Cuando quitas una etiqueta.

- __opened:__ Cuando se crea el PR por primera vez.

- __synchronize:__ Cuando subes nuevos commits a la rama del PR (muy usado para re-ejecutar tests).

closed: Cuando se cierra el PR (puedes verificar si fue por un merge o simplemente cerrado).

converted_to_draft: Cuando un PR pasa de normal a borrador.

__create / delete:__ 

Se activan al crear o eliminar ramas o etiquetas.

### 2. Eventos Manuales
Útiles cuando quieres controlar exactamente cuándo ocurre una acción (como un despliegue a producción):

__workflow_dispatch:__ 

Permite ejecutar el workflow manualmente desde la pestaña "Actions" en GitHub. Incluso puedes definir un formulario con parámetros de entrada.

__repository_dispatch:__ 

Permite activar un workflow desde fuera de GitHub (por ejemplo, desde un servidor externo o una aplicación propia) enviando una petición HTTP a la API de GitHub.

### 3. Eventos Programados

__schedule:__ 

Permite ejecutar tareas de forma periódica usando la sintaxis de cron.

Ejemplo: cron: '0 0 * * *' para ejecutarlo todas las noches a medianoche.

### 4. Eventos de Orquestación (Workflows encadenados)

__workflow_run:__

Se activa cuando otro workflow termina (ya sea que haya tenido éxito o fallado). Útil para separar el proceso de "Build" del de "Deploy".

__workflow_call:__ 

Se usa en workflows reutilizables. Permite que un workflow sea llamado por otros como si fuera una función.

### 5. Eventos de Gestión del Repositorio
GitHub permite automatizar casi cualquier interacción en la plataforma:

__issues:__ 

Cuando se abre, edita o cierra un issue.

Ideal para automatizar la gestión de proyectos y bots.

- __opened:__ Cuando un usuario reporta un bug o sugiere algo.

- __labeled:__ Cuando etiquetas un issue (ej. para moverlo automáticamente en un tablero).

- __assigned / unassigned:__ Cuando asignas a alguien para resolverlo.

- __deleted:__ Si un administrador borra el issue.

__issue_comment:__ 

Cuando alguien comenta en un issue o pull request.

__release:__ 

Cuando publicas una nueva versión (release) de tu software.

Se usa para la etapa final del despliegue.

- __published:__ Cuando la versión es pública (ideal para subir el código a producción).

- __created:__ Cuando se guarda el borrador del release.

- __prereleased:__ Cuando marcas una versión como "Beta" o "Alpha".

__watch:__ 

Se activa cuando alguien le da a "Star" al repositorio.

__registry_package__

Relacionado con GitHub Packages (Docker, npm, etc.).

- __published:__ Cuando una nueva versión de un paquete o imagen de Docker se sube con éxito.

- __updated:__ Cuando se actualiza una versión existente.

## Variables