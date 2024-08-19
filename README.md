# Git ![icon-git](data:image/svg+xml;base64,PHN2ZyB4bWxucz0iaHR0cDovL3d3dy53My5vcmcvMjAwMC9zdmciIHdpZHRoPSIyNCIgaGVpZ2h0PSIyNCIgdmlld0JveD0iMCAwIDI1NiAyNTYiPjxnIGZpbGw9Im5vbmUiPjxyZWN0IHdpZHRoPSIyNTYiIGhlaWdodD0iMjU2IiBmaWxsPSIjRjAzQzJFIiByeD0iNjAiLz48ZyBjbGlwLXBhdGg9InVybCgjSWNvbmlmeUlkMTkxNmIzMmFiMTYzMDg5YTUwKSI+PHBhdGggZmlsbD0iI2ZmZiIgZD0ibTIyNC4yMjUgMTE5LjA5NGwtODcuMzE5LTg3LjMxOWExMi44NyAxMi44NyAwIDAgMC0xNC4wMzUtMi43OTNhMTIuOSAxMi45IDAgMCAwLTQuMTc3IDIuNzkzTDEwMC41NjkgNDkuOWwyMyAyM2M1LjM1LTEuODc1IDExLjQ3NS0uNTk0IDE1LjczNyAzLjY2OWExNS4zMSAxNS4zMSAwIDAgMSAzLjYzMSAxNS44MzFsMjIuMTY5IDIyLjE2OWM1LjM2My0xLjg1IDExLjU1LS42NTcgMTUuODMxIDMuNjM3YTE1LjMyIDE1LjMyIDAgMCAxIDMuMzIxIDE2LjcwNmExNS4zMzMgMTUuMzMzIDAgMCAxLTIwLjAyOSA4LjI5M2MtMS44Ni0uNzcxLTMuNTUtMS45LTQuOTczLTMuMzI0Yy00LjUtNC41LTUuNjEyLTExLjEyNS0zLjMzNy0xNi42NjlsLTIwLjY3NS0yMC42NzV2NTQuNDA3YTE1LjYgMTUuNiAwIDAgMSA0LjA2MiAyLjlhMTUuMzI2IDE1LjMyNiAwIDAgMS0yMS42NzUgMjEuNjc1YTE1LjMyIDE1LjMyIDAgMCAxLTMuMzI2LTE2LjcwNGExNS4zIDE1LjMgMCAwIDEgMy4zMjYtNC45NzFjMS40ODEtMS40NzUgMy4xMjUtMi41OTQgNS4wMTktMy4zNDR2LTU0LjkxM2ExNS4yIDE1LjIgMCAwIDEtNS4wMTktMy4zNDNhMTUuMzE1IDE1LjMxNSAwIDAgMS0zLjMtMTYuNzU3TDkxLjY0NCA1OC44MTRsLTU5Ljg3NSA1OS44MTJhMTIuODggMTIuODggMCAwIDAtMi43OTUgMTQuMDRhMTIuOSAxMi45IDAgMCAwIDIuNzk1IDQuMTc5bDg3LjMyNSA4Ny4zMTJhMTIuOSAxMi45IDAgMCAwIDQuMTc3IDIuNzkzYTEyLjkgMTIuOSAwIDAgMCA5Ljg1OCAwYTEyLjkgMTIuOSAwIDAgMCA0LjE3Ny0yLjc5M2w4Ni45MTktODYuNzgxYTEyLjg4IDEyLjg4IDAgMCAwIDMuNzc2LTkuMTA5YTEyLjg4IDEyLjg4IDAgMCAwLTMuNzc2LTkuMTEiLz48L2c+PGRlZnM+PGNsaXBQYXRoIGlkPSJJY29uaWZ5SWQxOTE2YjMyYWIxNjMwODlhNTAiPjxwYXRoIGZpbGw9IiNmZmYiIGQ9Ik0yOCAyOGgyMDB2MjAwSDI4eiIvPjwvY2xpcFBhdGg+PC9kZWZzPjwvZz48L3N2Zz4=)

[¿Qué es Git?](https://www.atlassian.com/es/git/tutorials/what-is-git) Git es un software de control de versiones diseñado por Linus Torvalds, pensando en la eficiencia, la confiabilidad y compatibilidad del mantenimiento de versiones de aplicaciones cuando estas tienen un gran número de archivos de código fuente.

## Inicializar un repo
Para inicializar un repositorio usando git se usa el sigueinte comando:

```Bash
git init
```
## Agregar cambios(Git add)
```Bash
git add
```
Este comando nos permite agregar los ultimos cambios de nuestros archivos al stage de git, dentro de este mismo comando se le pueden agregar otras instrucciones:

- **git add .** Agrega todos los cambios nuevos.
```Bash
git add .
```
- **git add < name_file >** Agrega los cambios del archivo especificado.
```Bash
git add archivo.txt
```
- **git add -A o --all**  Agrega todos los cambios en el repositorio, incluyendo archivos modificados, nuevos y eliminados.
```Bash
git add -A
git add --all
```
- **git add -u**  Agrega los archivos modificados y eliminados al stage, pero no los nuevos archivos.
```Bash
git add -u
```
- **git add -p < name_file >**  Agrega los archivos modificados y eliminados al stage, pero no los nuevos archivos. Permite agregar cambios parciales de un archivo a la área de preparación. Esto es útil si deseas agregar solo ciertas líneas o secciones de un archivo.
```Bash
git add -p archivo.txt
```
- **git add --patch < name_file >** Similar a git add -p, este comando te permite revisar y agregar cambios de manera interactiva, división por división (hunk).
```Bash
git add --patch archivo.txt
```
- **git add --f < archivo_ignorado >** Fuerza la adición de archivos ignorados por .gitignore.
```Bash
git add -f archivo_ignorado.txt
```
- **git add < directorio >** Agrega todos los archivos en un directorio específico.
```Bash
git add src/
```
- **git add < .extension >** Agrega todos los archivos que coincidan con un patrón específico.
```Bash
git add "*.txt" 
```


## Guardar cambios(Git commit)
```Bash
git commit
```

El comando git commit se utiliza para guardar los cambios en la área de preparación (staging area) en el historial del repositorio de Git. Cuando realizas un commit, estás creando una instantánea de los cambios en ese momento, que luego puedes revertir o fusionar si es necesario. dentro de este mismo comando se le pueden agregar otras instrucciones:

- **git commit -m "mensaje"** Realiza un commit con un mensaje específico sin abrir un editor de texto. El mensaje de confirmación se proporciona directamente en la línea de comandos.
```Bash
git commit -m "Agrega nueva función de autenticación"
```
- **git commit -a** Realiza un commit que incluye todos los cambios en los archivos rastreados (tracked), es decir, modifica y confirma automáticamente todos los archivos que han sido modificados o eliminados, pero no nuevos archivos.
```Bash
git commit -a -m "Corrige errores en el sistema de autenticación"
```
- **git commit --amend** Modifica el último commit. Permite cambiar el mensaje de confirmación o agregar más cambios al último commit sin crear uno nuevo.
```Bash
git commit --amend -m "Mensaje corregido del último commit"
```
- **git commit --no-edit** Realiza un commit sin modificar el mensaje del commit anterior cuando se usa junto con --amend.
```Bash
git commit --amend --no-edit
```
- **git commit --author="Nombre < email@example.com >"** Realiza un commit con un autor específico diferente del autor predeterminado configurado en Git.
```Bash
git commit --author="Juan Pérez <juan@example.com>" -m "Mensaje de commit con autor específico"
```
- **git commit --dry-run** Muestra qué archivos serían incluidos en el commit sin realizar realmente el commit.
```Bash
git commit --dry-run
```
- **git commit --squash < commit >** Combina (squash) los cambios del commit especificado con el siguiente commit.
```Bash
git commit --squash HEAD~1 -m "Combina los cambios con el último commit"
```
- **git commit --allow-empty** Realiza un commit incluso si no hay cambios en la área de preparación. Esto es útil para crear commits que solo contienen un mensaje (por ejemplo, para marcar un punto en el historial).
```Bash
git commit --allow-empty -m "Marcador de hitos sin cambios"
```
- **git commit --signoff** Añade una línea de sign-off en el final del mensaje del commit, mostrando quién realizó el commit, como una especie de firma.
```Bash
git commit --signoff -m "Mensaje de commit con sign-off"
```

## Cambiar de rama(Git checkout/switch)
En Git, cambiar de ramas es una operación común que se realiza utilizando el comando `git checkout` o, en versiones más recientes de Git, `git switch`. 
- **git checkout/switch name_branch** Puedes cambiar a una rama existente utilizando este comando
```Bash
git checkout nombre_de_la_rama
git switch nombre_de_la_rama
```
- **git checkout -b/switch -c name_new_branch** Puedes cambiar a una rama existente utilizando este comando
```Bash
git checkout -b nombre_de_la_nueva_rama
git switch -c nombre_de_la_nueva_rama
```
- **git branch** Para ver una lista de todas las ramas en tu repositorio
```Bash
git branch
```
-  **git branch -a** Para ver todas las ramas, incluidas las remotas
```Bash
git branch -a
```
-  **git checkout/switch -** Si deseas cambiar a la rama en la que estabas anteriormente
```Bash
git checkout -
git switch -
```
-  **git checkout/switch -f name_branch** Si tienes cambios no confirmados que no deseas perder al cambiar de rama, puedes forzar el cambio de rama (esto sobrescribirá tus cambios no confirmados)
```Bash
git checkout -f nombre_de_la_rama
git switch -f nombre_de_la_rama
```
-  **git merge name_branch** Una vez que hayas cambiado de rama, puedes fusionar cambios desde otra rama
```Bash
git merge nombre_de_otra_rama
```
-  **git branch -d name_branch** Para eliminar una rama local (después de cambiar a otra rama)
```Bash
git branch -d nombre_de_la_rama
```
-  **git branch -D name_branch** Si la rama no está completamente fusionada, y deseas forzar la eliminación
```Bash
git branch -D nombre_de_la_rama
```
-  **git checkout/switch name_branch_remote** Si deseas cambiar a una rama remota que aún no existe localmente, debes hacer lo siguiente
```Bash
git checkout nombre_de_la_rama_remota
git switch --track origen/nombre_de_la_rama_remota
```
## Subir cambios(Git push)
El comando `git push` se utiliza para subir los cambios confirmados (commits) desde tu repositorio local al repositorio remoto. Aquí te dejo una descripción detallada de los usos más comunes del comando git push:
-  **git push < romete > < branch >** Sube los cambios de la rama especificada al repositorio remoto
```Bash
git push origin main
```
-  **git push -u < romete > < branch >** Sube los cambios de la rama especificada y establece la rama en el remoto como la rama predeterminada para futuras operaciones
```Bash
git push -u origin main
```
-  **git push** Si ya has establecido un repositorio remoto y una rama predeterminada, simplemente puedes ejecutar git push sin argumentos para subir los cambios.
```Bash
git push
```
-  **git push --forcer/-f** Fuerza la subida de cambios al repositorio remoto. Este comando es peligroso porque puede sobrescribir cambios en el remoto, por lo que debe usarse con precaución.
```Bash
git push --force
git push -f
```
-  **git push --forcer-with-lease** Es una alternativa más segura a --force, ya que solo sobrescribirá los cambios en el remoto si no ha habido actualizaciones en la rama remota desde la última vez que la descargaste.
```Bash
git push --force-with-lease
```
-  **git push -u < romete >** Sube todas las ramas locales al repositorio remoto.
```Bash
git push --all origin
```
-  **git push -u < romete > --tags** Sube todas las etiquetas (tags) locales al repositorio remoto.
```Bash
git push origin --tags
```
-  **git push -u < romete > :< branch >** Elimina una rama en el repositorio remoto
```Bash
git push origin :nombre_de_la_rama
```
-  **git push -u < romete > < local > :< remote >** Sube una rama local a una rama remota con un nombre diferente.
```Bash
git push origin local-branch:remote-branch
```
-  **git push --set-upstream  < romete > < branch >** Establece la rama especificada como la rama upstream, lo que permite que futuros git pull y git push se realicen automáticamente en esta rama.
```Bash
git push --set-upstream origin nueva-rama
```

## Buscar cambios(Git fetch)
El comando `git fetch` se utiliza para descargar objetos y referencias desde un repositorio remoto al repositorio local. A diferencia de git pull, git fetch no fusiona automáticamente los cambios en la rama actual; simplemente actualiza las referencias remotas en tu repositorio local. Aquí te dejo una descripción detallada de los usos más comunes del comando git fetch.

- **git fetch < remote >** Descarga todos los cambios del repositorio remoto especificado (normalmente origin), actualizando las referencias remotas locales.
```Bash
git fetch origin
```
- **git fetch** Descarga todos los cambios de todos los repositorios remotos configurados.
```Bash
git fetch
```
- **git fetch < remote > < branch >** Descarga solo la rama especificada desde el remoto.
```Bash
git fetch origin main
```
- **git fetch < remote >** Descarga todos los cambios del repositorio remoto especificado (normalmente origin), actualizando las referencias remotas locales.
```Bash
git fetch origin
```
- **git fetch --all** Descarga todas las ramas y etiquetas de todos los remotos configurados en el repositorio local.
```Bash
git fetch --all
```
- **git fetch --prune** Elimina las referencias remotas que han sido eliminadas en el repositorio remoto.
```Bash
git fetch --prune
```
- **git fetch --tags** Descarga todas las etiquetas (tags) del repositorio remoto.
```Bash
git fetch --tags
```
- **git fetch < remote > --depth=< n >** Descarga una cantidad limitada de commits más recientes, útil para trabajar con historiales grandes.
```Bash
git fetch origin --depth=1
```
- **git fetch < remote > < branch >: < new_branch_local >** Descarga una rama específica del remoto y crea una nueva rama local a partir de ella.
```Bash
git fetch origin feature-branch:new-local-branch
```
- **git fetch < remote > --no-tags** Evita descargar las etiquetas (tags) del remoto.
```Bash
git fetch origin --no-tags
```
- **git fetch < remote > --dry-run** Muestra lo que se descargaría sin realizar realmente la descarga.
```Bash
git fetch origin --dry-run
```

## Traer cambios(Git pull)
- **git pull < remote > < branch >** Descarga los cambios de la rama especificada en el repositorio remoto y los fusiona con la rama actual.
```Bash
git pull origin main
```
- **git pull** Si ya tienes una rama predeterminada configurada con un repositorio remoto (por ejemplo, después de git clone), puedes simplemente ejecutar git pull para descargar y fusionar los cambios.
```Bash
git pull
```
- **git pull --rebase** En lugar de fusionar los cambios, git pull --rebase aplica tus commits locales en la parte superior de los cambios descargados. Esto mantiene un historial más limpio sin merges adicionales.
```Bash
git pull --rebase origin main
```
- **git pull --no-commit** Descarga los cambios y realiza la fusión, pero no hace un commit automático. Esto te permite revisar los cambios antes de hacer el commit.
```Bash
git pull --no-commit origin main
```
- **git pull --no-rebase** Fuerza una fusión en lugar de un rebase cuando la configuración predeterminada es hacer rebase.
```Bash
git pull --no-rebase origin main
```
- **git pull --ff-only** Realiza un pull solo si puede hacer un "fast-forward" sin necesidad de una fusión. Si no es posible, el pull falla.
```Bash
git pull --ff-only origin main
```
- **git pull --depth=< n >** Realiza un pull con una profundidad específica, útil para obtener solo los últimos commits.
```Bash
git pull origin main --depth=1
```
- **git pull --allow-unrelated-histories** Permite la fusión de dos ramas sin un historial común, útil cuando se están combinando dos repositorios diferentes..
```Bash
git pull origin main --allow-unrelated-histories
```
- **git pull --quiet** Suprime la salida de mensajes informativos durante el pull.
```Bash
git pull --quiet origin main
```
- **git pull --verbose** Muestra mensajes adicionales para un pull más detallado.
```Bash
git pull --verbose origin main
```

## Revertir(Git revert)
El comando git revert se utiliza para deshacer de manera segura un cambio específico en el historial de Git creando un nuevo commit que revierte los cambios introducidos por un commit anterior. A diferencia de git reset, que elimina los commits, git revert preserva el historial de cambios al agregar un nuevo commit que invierte los efectos de un commit anterior.
- **git revert < commit-hash >** Para revertir un commit específico, debes identificar el hash del commit (los primeros 7 caracteres suelen ser suficientes)
```Bash
git revert 1234abc
```
- **git revert < commit-hash 1 >..< commit-hash 2 >** Puedes revertir varios commits especificando un rango de commits
```Bash
git revert 1234abc..7890def
```
- O puedes revertir varios commits individualmente
```Bash
git revert 1234abc 5678def
```
- **git revert -m 1 < merge-commit-hash >** Revertir un commit de fusión (merge commit) puede ser un poco más complicado porque involucra múltiples ramas. Necesitas especificar el parent (padre) del merge que quieres conservar.
```Bash
git revert -m 1 1234abc
```
- **git revert -m** Si deseas proporcionar un mensaje personalizado para el commit de revert, puedes usar la opción -m o editar el mensaje durante el proceso.
```Bash
git revert -m "Revirtiendo commit X por razones Y"
```
- **git revert --no-commit < commit-hash >** Si prefieres no hacer el commit inmediatamente, puedes utilizar la opción --no-commit (o -n) para revertir los cambios y mantenerlos en la área de preparación (staging area) para que los puedas revisar antes de confirmar.
```Bash
git revert --no-commit 1234abc
```
- **git revert --no-edit < commit-hash >** Usa --no-edit si deseas revertir un commit sin abrir el editor de texto para modificar el mensaje del commit.
```Bash
git revert --no-edit 1234abc
```

## Reescribir el historial(Git rebase)
El comando git rebase es una poderosa herramienta en Git que te permite reescribir el historial de commits de una rama. En lugar de fusionar (merge) una rama en otra, git rebase toma los commits de la rama actual y los aplica sobre otra base (es decir, sobre otro commit o rama), creando un historial de commits más lineal y limpio.)

## Seleccionar commits(Git cherry-pick)

## Clonar(Git clone)

## Guarda temporalmente los cambios(Git stash)

## Deshacer commits(Git reset)

## Diferencias entre commits(Git diff)

## Historial de commits(Git log)

## Marcar(Git tag)

## Combinar ramas(Git merge)

## Eliminar archivos untracked(Git clean)

## Conexiones a repositorios(Git remote)

## Encontrar commits especificos(Git bisect)
