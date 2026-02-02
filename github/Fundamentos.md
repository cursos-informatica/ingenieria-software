# Fundamentos

## Ejecutores

### 1. Eventos de Código (Git)
Son los más comunes para CI/CD (Integración y Despliegue Continuo):

push: Se activa cuando subes código a una rama o etiquetas (tags). Es el estándar para correr tests automáticamente.

pull_request: Se activa cuando se abre, actualiza o cierra un PR. Ideal para validar código antes de mezclarlo.

create / delete: Se activan al crear o eliminar ramas o etiquetas.

### 2. Eventos Manuales
Útiles cuando quieres controlar exactamente cuándo ocurre una acción (como un despliegue a producción):

workflow_dispatch: Permite ejecutar el workflow manualmente desde la pestaña "Actions" en GitHub. Incluso puedes definir un formulario con parámetros de entrada.

repository_dispatch: Permite activar un workflow desde fuera de GitHub (por ejemplo, desde un servidor externo o una aplicación propia) enviando una petición HTTP a la API de GitHub.

### 3. Eventos Programados
schedule: Permite ejecutar tareas de forma periódica usando la sintaxis de cron.

Ejemplo: cron: '0 0 * * *' para ejecutarlo todas las noches a medianoche.

### 4. Eventos de Orquestación (Workflows encadenados)
workflow_run: Se activa cuando otro workflow termina (ya sea que haya tenido éxito o fallado). Útil para separar el proceso de "Build" del de "Deploy".

workflow_call: Se usa en workflows reutilizables. Permite que un workflow sea llamado por otros como si fuera una función.

### 5. Eventos de Gestión del Repositorio
GitHub permite automatizar casi cualquier interacción en la plataforma:

issues: Cuando se abre, edita o cierra un issue.

issue_comment: Cuando alguien comenta en un issue o pull request.

release: Cuando publicas una nueva versión (release) de tu software.

watch: Se activa cuando alguien le da a "Star" al repositorio.


## Variables