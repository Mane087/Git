# Git 
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

## Reescribir el historial (Git rebase)
`git rebase` es una herramienta para **reescribir la historia de commits** moviendo una rama a otra base.
En términos simples: **toma tus commits y los vuelve a aplicar como si hubieran sido creados después de otro commit**.

No cambia el contenido de tu trabajo, cambia **la forma en que la historia del repositorio está organizada**.

### Ejemplo

Imagina esta historia de ramas:

```
main
A---B---C

feature
     \
      D---E
```

Mientras trabajabas en `feature`, alguien agregó `C` a `main`.

Si haces un **merge**:

```
git merge main
```

la historia queda así:

```
A---B---C
     \   \
      D---E---M
```

`M` es un **merge commit**.

---

### Con `git rebase`

En lugar de crear un merge commit, **rebase mueve tus commits encima de la rama actual**.

Comando:

```bash
git rebase main
```

Resultado:

```
A---B---C---D'---E'
```

Tus commits `D` y `E` se **recrean** como `D'` y `E'`.

Por eso se dice que **rebase reescribe la historia**.

---

### Uso más común (flujo real)

Caso típico en equipos:

Estás en tu rama:

```
feature-login
```

y `main` avanzó.

#### 1️⃣ Actualizas referencias

```bash
git fetch origin
```

#### 2️⃣ Rebase sobre main

```bash
git rebase origin/main
```

Esto hace:

```
feature-login commits
↓
se reaplican encima de main
```

---

### Ejemplo real paso a paso

Historial:

```
main
A---B---C

feature
     \
      D---E
```

Comando:

```bash
git checkout feature
git rebase main
```

Git hace internamente:

1. Guarda los commits `D` y `E`
2. Mueve la rama a `C`
3. Aplica `D`
4. Aplica `E`

Resultado:

```
A---B---C---D'---E'
```

---

### Conflictos en rebase

Si hay conflicto, Git se detiene.

Verás algo como:

```
CONFLICT (content): Merge conflict in file.txt
```

Proceso:

1️⃣ arreglas el archivo

2️⃣ agregas cambios

```bash
git add .
```

3️⃣ continúas

```bash
git rebase --continue
```

Opciones útiles:

```
git rebase --abort
```

Cancela el rebase.

```
git rebase --skip
```

Salta ese commit.

---

### Rebase interactivo (muy poderoso)

Permite **editar commits antes de subirlos**.

Comando:

```bash
git rebase -i HEAD~3
```

Esto abre:

```
pick a1b2c3 commit 1
pick d4e5f6 commit 2
pick g7h8i9 commit 3
```

Puedes cambiar:

| comando | efecto           |
| ------- | ---------------- |
| pick    | dejar commit     |
| squash  | unir commits     |
| edit    | modificar commit |
| drop    | eliminar commit  |

Ejemplo para unir commits:

```
pick a1b2c3 add login
squash d4e5f6 fix login
squash g7h8i9 fix typo
```

Resultado:

```
un solo commit limpio
```

---

### Regla importante (muy importante)

Nunca hagas rebase sobre commits que **ya fueron publicados**.

Porque cambia hashes.

Ejemplo peligroso:

```
git rebase main
git push --force
```

Eso puede romper el trabajo de otros.

Regla práctica:

| Situación         | Rebase         |
| ----------------- | -------------- |
| Antes de hacer PR | ✔ recomendable |
| Trabajo local     | ✔              |
| Rama compartida   | ❌ evitar       |
| Rama publicada    | ❌              |

---

### Cuándo usarlo

Se usa mucho para:

#### limpiar historia antes del PR

```
git rebase -i
```

#### actualizar tu rama

```
git fetch origin
git rebase origin/main
```

#### evitar commits de merge innecesarios

Historia más limpia:

```
A---B---C---D---E
```

en lugar de:

```
A---B---C
     \   \
      D---E---M
```

---

### Importante

`merge` **preserva historia real**
`rebase` **crea historia lineal**

Por eso algunos equipos prefieren:

```
rebase local
merge en main
```

GitHub incluso tiene botón:

```
Rebase and merge
```

---

### Resumen

**Merge**

```
git merge main
```

* conserva historia
* crea merge commit

**Rebase**

```
git rebase main
```

* reescribe historia
* deja línea limpia

## Seleccionar commits (Git cherry-pick)
`git cherry-pick` sirve para **traerte uno o varios commits específicos** de otra rama **sin mezclar toda la rama**.

Es como decirle a Git:

> “No quiero todo ese feature. Solo dame *ese commit exacto*.”

### Qué hace

Toma un commit existente y **lo aplica en tu rama actual** como un commit nuevo.

Ejemplo:

Tienes esto:

```text
main
A---B---C

feature-x
     \
      D---E---F
```

Estás en `main` y solo quieres el commit `E`.

```bash
git checkout main
git cherry-pick <hash-de-E>
```

Resultado:

```text
A---B---C---E'
```

Ese `E'` es una **copia lógica** del commit `E`, pero con **otro hash**.

No “mueve” el commit original.
Lo **reproduce** en otra rama.

---

### Cuándo se usa

#### 1. Pasar una corrección puntual

Ejemplo clásico:

* hiciste un hotfix en una rama
* también lo necesitas en otra rama

En vez de mergear todo, haces:

```bash
git cherry-pick <commit>
```

---

#### 2. Recuperar un commit útil de otra rama

Supón que en una rama experimental hiciste 10 commits, pero solo 1 realmente sirve.

No quieres arrastrar toda la basura cósmica.
Solo extraes el commit bueno.

---

#### 3. Aplicar un fix a release/main

Muy común:

* el fix se hizo en `develop`
* también debe entrar a `release` o `main`

---

### Uso básico

```bash
git cherry-pick <commit_hash>
```

Ejemplo:

```bash
git cherry-pick a1b2c3d
```

---

### Varios commits

Puedes aplicar varios:

```bash
git cherry-pick hash1 hash2 hash3
```

O un rango:

```bash
git cherry-pick A^..D
```

Eso aplica desde `A` hasta `D`.

Ese rango suele confundir gente. No es magia negra, pero casi.
Si no estás seguro, mejor pasa los hashes explícitos.

---

### Qué pasa internamente

Git toma el diff del commit original y trata de aplicarlo sobre tu rama actual.

Eso significa que puede haber:

* aplicación limpia
* conflictos
* imposibilidad si el contexto ya cambió mucho

---

### Conflictos

Si hay conflicto:

```bash
git cherry-pick <hash>
```

Git se detiene, tú corriges, luego:

```bash
git add .
git cherry-pick --continue
```

Para cancelar:

```bash
git cherry-pick --abort
```

---

### Ejemplo real

Supón que estás en `main`:

```bash
git checkout main
git log --oneline --all
```

Ves algo así:

```bash
f9e8d7c fix login bug
a1b2c3d add experimental panel
```

Quieres solo el fix:

```bash
git cherry-pick f9e8d7c
```

Listo.
No te traes el panel experimental.

---

### Diferencia contra merge

#### `merge`

Trae **todos los commits** de una rama y une historias.

```bash
git merge feature-x
```

#### `cherry-pick`

Trae **solo commits concretos**.

```bash
git cherry-pick a1b2c3d
```

---

### Diferencia contra rebase

#### `rebase`

Reubica una secuencia de commits sobre otra base.

#### `cherry-pick`

Copia commits específicos.

No es para “actualizar mi rama con main”.
Para eso normalmente usas `merge` o `rebase`.

## Clonar (Git clone)
`git clone` sirve para **copiar un repositorio remoto completo a tu máquina local**.

En otras palabras:

> crea una carpeta con el proyecto, su historial de commits, sus ramas remotas y la configuración básica para trabajar con ese repo.

No solo baja archivos.
También baja **la metadata de Git**.

---

### Sintaxis básica

```bash
git clone <url-del-repositorio>
```

Ejemplo:

```bash
git clone https://github.com/usuario/proyecto.git
```

Eso crea una carpeta llamada `proyecto`.

---

### Qué hace exactamente

Cuando ejecutas `git clone`:

1. descarga el contenido del repositorio
2. descarga el historial de commits
3. crea la carpeta `.git`
4. configura el remoto `origin`
5. deja una rama local lista para trabajar

---

### Ejemplo real

```bash
git clone https://github.com/lynxworxs/lynxwebex.git
```

Luego:

```bash
cd lynxwebex
git remote -v
```

Verás algo como:

```bash
origin  https://github.com/lynxworxs/lynxwebex.git (fetch)
origin  https://github.com/lynxworxs/lynxwebex.git (push)
```

## Guarda temporalmente los cambios (Git stash)
`git stash` sirve para **guardar temporalmente cambios no confirmados** sin hacer un commit.

Es como decirle a Git:

> “Guárdame este trabajo en un cajón porque necesito cambiar de rama o limpiar el working tree, pero todavía no quiero hacer commit.”

---

### Qué guarda

Normalmente guarda cambios en:

* archivos **modificados**
* archivos en **staging**
* opcionalmente archivos **no rastreados** (`untracked`)

Después de hacer `stash`, tu directorio queda más limpio, casi como si no hubieras tocado nada.

---

### Caso típico

Estás trabajando y tienes cambios así:

```bash
git status
```

```text
modified: app.js
modified: auth.js
```

Pero de pronto necesitas cambiarte a otra rama para revisar algo urgente.

En vez de hacer un commit mugroso tipo:

```bash
git commit -m "WIP no sirve aun no tocar"
```

haces:

```bash
git stash
```

Git guarda esos cambios y limpia tu rama actual.

---

### Flujo básico

#### Guardar cambios

```bash
git stash
```

#### Ver los stashes guardados

```bash
git stash list
```

Salida típica:

```text
stash@{0}: WIP on feature/login: a1b2c3d add validation
stash@{1}: WIP on main: d4e5f6 fix navbar
```

#### Recuperar el último stash

```bash
git stash apply
```

Esto lo reaplica, pero **no lo elimina** de la lista.

#### Recuperar y eliminar

```bash
git stash pop
```

Esto lo reaplica y luego lo quita del stash.

---

### Diferencia entre `apply` y `pop`

#### `apply`

* recupera cambios
* **conserva** el stash guardado

```bash
git stash apply
```

#### `pop`

* recupera cambios
* **elimina** el stash si todo sale bien

```bash
git stash pop
```

Prácticamente:

* si quieres jugar seguro, usa `apply`
* si ya vas decidido, usa `pop`

---

### Ponerle nombre

Puedes guardar un stash con mensaje:

```bash
git stash push -m "avance del formulario de login"
```

Eso ayuda bastante porque si haces 8 stashes seguidos, luego todos parecen restos arqueológicos de decisiones cuestionables.

---

### Ver qué hay dentro

```bash
git stash show
```

Más detalle:

```bash
git stash show -p
```

Eso muestra el diff guardado.

---

### Recuperar uno específico

Si tienes varios:

```bash
git stash list
```

Y quieres uno concreto:

```bash
git stash apply stash@{1}
```

o

```bash
git stash pop stash@{1}
```

---

### Eliminar stash

Uno específico:

```bash
git stash drop stash@{0}
```

Todos:

```bash
git stash clear
```

Ese `clear` sí es escoba brutal. No lo tires alegremente.

---

### Archivos no rastreados

Por defecto, `git stash` **no siempre incluye archivos nuevos** que aún no están tracked.

Si quieres guardarlos también:

```bash
git stash -u
```

o:

```bash
git stash --include-untracked
```

Si no haces eso, puedes pensar “ya guardé todo” y sorpresa: el archivo nuevo siguió ahí mirándote fijamente.

---

### Cuándo usarlo

#### Úsalo cuando:

* necesitas cambiar de rama rápido
* aún no quieres hacer commit
* tienes trabajo a medias
* quieres probar algo y luego volver

#### No lo uses como sistema de versionado paralelo

Si tienes cosas importantes durante días en stash, eso ya huele mal.
Para trabajo real y duradero, mejor usa commits en una rama.

---

### Ejemplo real

Tienes cambios locales:

```bash
git status
```

```text
modified: login.ts
modified: user.service.ts
```

Guardas:

```bash
git stash push -m "wip login validation"
```

Te cambias de rama:

```bash
git checkout main
```

Luego regresas:

```bash
git checkout feature/login
git stash pop
```

Y recuperas el trabajo.

---

### Problemas comunes

#### 1. Conflictos al hacer `pop` o `apply`

Sí, también puede haber conflictos.
Porque el mundo es absurdo y Git no regala paz interior.

Si cambió el mismo archivo entre el stash y la rama actual, tendrás que resolverlo manualmente.

---

#### 2. Creer que stash reemplaza commits

No.
`stash` es temporal.
No es historial formal del proyecto.

---

#### 3. Acumular stashes viejos

Muchos devs hacen esto:

```bash
git stash
git stash
git stash
git stash
```

Y luego no saben qué demonios guardaron en cada uno.

Si el cambio vale la pena, probablemente vale más un commit limpio en una rama.

---

### Resumen directo

`git stash` = **guardar cambios temporales sin commit**

Comandos más útiles:

```bash
git stash
git stash push -m "mensaje"
git stash list
git stash apply
git stash pop
git stash drop stash@{0}
git stash clear
git stash -u
```

---

### Regla práctica

Usa `stash` para trabajo:

* corto
* temporal
* interrumpido

No para esconder código durante una semana como si fuera debajo de la alfombra del repositorio.

La trampa mental más común con `stash` es esta: **si ese cambio importa de verdad, quizá no necesitas stash; necesitas una rama y un commit decente**.

## Deshacer commits(Git reset)
`git reset` es un comando que **mueve el puntero de una rama a otro commit** y opcionalmente **deshace cambios en staging o en el working directory**.

Dicho sin poesía:

> cambia el estado del repositorio como si ciertos commits o cambios nunca hubieran ocurrido.

Es un comando poderoso… y peligroso si no sabes exactamente qué estás moviendo.

---

### Ejemplo

Git tiene tres estados principales:

| Estado                   | Qué es                            |
| ------------------------ | --------------------------------- |
| **HEAD**                 | el commit actual                  |
| **Index (staging area)** | lo que está preparado para commit |
| **Working directory**    | archivos en tu carpeta            |

`git reset` puede afectar **uno, dos o los tres** dependiendo del modo.

---

### Sintaxis básica

```bash
git reset <modo> <commit>
```

Ejemplo:

```bash
git reset --soft HEAD~1
```

Eso mueve la rama **un commit atrás**.

---

### Los tres modos importantes

#### 1. `--soft`

Solo mueve el puntero de la rama.

No toca staging ni archivos.

```bash
git reset --soft HEAD~1
```

Ejemplo:

Antes:

```
A---B---C (HEAD)
```

Después:

```
A---B (HEAD)
     \
      C (cambios quedan en staging)
```

Uso típico:

> rehacer el último commit

---

#### 2. `--mixed` (modo por defecto)

Mueve la rama y limpia staging.

Pero **no toca los archivos**.

```bash
git reset HEAD~1
```

o

```bash
git reset --mixed HEAD~1
```

Resultado:

* commit desaparece
* archivos quedan modificados
* ya no están en staging

---

#### 3. `--hard`

El modo nuclear.

```bash
git reset --hard HEAD~1
```

Hace tres cosas:

* mueve la rama
* limpia staging
* **borra cambios del working directory**

Resultado:

El commit desaparece **y los cambios también**.

Si no están en otro commit o stash, adiós.

---

### Ejemplo práctico

Historial:

```
A---B---C (HEAD)
```

#### Soft

```bash
git reset --soft HEAD~1
```

Resultado:

```
A---B (HEAD)
```

Pero cambios de `C` siguen en staging.

---

#### Mixed

```bash
git reset HEAD~1
```

Resultado:

```
A---B (HEAD)
```

Cambios siguen en archivos, pero **no en staging**.

---

#### Hard

```bash
git reset --hard HEAD~1
```

Resultado:

```
A---B (HEAD)
```

Cambios de `C` **desaparecen completamente**.

---

### Reset a un commit específico

Primero ves commits:

```bash
git log --oneline
```

Ejemplo:

```
a1b2c3d fix login
d4e5f6 add validation
g7h8i9 initial commit
```

Luego:

```bash
git reset --hard d4e5f6
```

La rama vuelve a ese commit.

---

### Reset de staging (uso común)

Quitar un archivo del staging:

```bash
git reset archivo.txt
```

Esto hace:

```
git add archivo.txt
↓
git reset archivo.txt
```

El archivo queda modificado pero **no staged**.

---

### Diferencia con `git revert`

Esto es crítico.

#### `reset`

* **reescribe historia**
* mueve commits
* puede borrar cambios

#### `revert`

* crea **un commit nuevo que deshace otro**

Ejemplo:

```
A---B---C
```

Revert de C:

```
A---B---C---D
```

Donde `D` revierte `C`.

Por eso:

| Situación             | Usar     |
| --------------------- | -------- |
| commits locales       | `reset`  |
| commits ya publicados | `revert` |

---

### Error clásico

Hacer esto después de push:

```bash
git reset --hard HEAD~1
git push --force
```

Eso **reescribe historia remota**.

Si alguien ya basó trabajo en ese commit, acabas de crear caos.

---

### Uso típico en desarrollo

#### rehacer último commit

```bash
git reset --soft HEAD~1
```

---

#### deshacer commit pero conservar cambios

```bash
git reset HEAD~1
```

---

#### borrar todo lo que hiciste desde el último commit

```bash
git reset --hard HEAD
```

---

### Visualización mental

Repositorio limpio:

```
commit
 ↓
HEAD
 ↓
staging
 ↓
working directory
```

`reset` mueve esos estados hacia atrás según el modo.

---

### Resumen brutalmente práctico

| comando                   | efecto                               |
| ------------------------- | ------------------------------------ |
| `git reset --soft HEAD~1` | deshace commit pero mantiene staging |
| `git reset HEAD~1`        | deshace commit y limpia staging      |
| `git reset --hard HEAD~1` | borra commit y cambios               |
| `git reset archivo`       | saca archivo del staging             |

---

Un detalle curioso: muchos desarrolladores creen que `git reset` “borra commits”. En realidad no los destruye inmediatamente; solo mueve el puntero de la rama. Durante un tiempo todavía existen en el **reflog**, como fósiles digitales flotando en el repositorio. Esa es la razón por la que a veces puedes recuperar un desastre… incluso después de un `--hard`.


## Diferencias entre commits(Git diff)
`git diff` sirve para **ver diferencias entre estados del código**.

Dicho simple:

> te muestra qué cambió, línea por línea.

Es de los comandos más útiles de Git, porque antes de hacer `add`, `commit`, `stash` o cualquier otra travesura, necesitas ver **qué demonios cambiaste realmente**.

---

### Qué compara

`git diff` puede comparar varias cosas:

* cambios en tus archivos **sin stage**
* cambios que ya están en **staging**
* diferencias entre **commits**
* diferencias entre **ramas**
* diferencias de un archivo específico

---

### Caso más común

#### Ver cambios no staged

```bash
git diff
```

Esto compara:

* tu **working directory**
* contra el **staging area**

O sea, te muestra lo que cambiaste **pero todavía no has hecho `git add`**.

---

### Ejemplo

Supón que cambiaste esto:

Antes:

```js
const port = 3000;
```

Después:

```js
const port = 4000;
```

`git diff` mostrará algo así:

```diff
-const port = 3000;
+const port = 4000;
```

#### Cómo leerlo

* línea con `-` → lo que estaba antes
* línea con `+` → lo que está ahora

---

### Ver cambios ya staged

```bash
git diff --staged
```

o también:

```bash
git diff --cached
```

Esto compara:

* **staging**
* contra el **último commit**

Sirve para revisar exactamente qué va a entrar en el próximo commit.

Muchos hacen `git add .` como si fuera hechicería automática y ni revisan. Luego el commit trae medio proyecto, un archivo `.env`, tres logs y la dignidad hecha pedazos.

---

### Flujo típico útil

```bash
git diff
git add archivo.txt
git diff --staged
```

Primero ves lo no staged, luego ves lo staged.

---

### Comparar commits

```bash
git diff <commit1> <commit2>
```

Ejemplo:

```bash
git diff a1b2c3d d4e5f6g
```

Eso muestra la diferencia entre esos dos commits.

---

### Comparar ramas

```bash
git diff main feature/login
```

Te muestra qué cambia entre ambas ramas.

Muy útil para entender:

* qué trae una rama
* qué falta
* si realmente el PR hace lo que dice y no metió basura lateral

---

### Comparar solo un archivo

```bash
git diff archivo.txt
```

O staged:

```bash
git diff --staged archivo.txt
```

Eso limita la salida a un solo archivo.

---

### Ver solo nombres de archivos cambiados

```bash
git diff --name-only
```

Eso no muestra líneas, solo nombres.

Ejemplo:

```text
src/app.ts
src/auth.ts
README.md
```

Sirve cuando quieres panorama general sin tragarte el diff completo.

---

### Ver resumen de cambios

```bash
git diff --stat
```

Ejemplo:

```text
src/app.ts    | 10 +++++-----
src/auth.ts   |  5 +++--
README.md     |  2 +-
```

Eso da una vista compacta de cuánto cambió cada archivo.

---

### Comparar working tree contra un commit

```bash
git diff HEAD
```

Esto muestra todo lo distinto entre tu estado actual y el último commit, incluyendo cambios staged y no staged.

---

### Comparar staged y unstaged por separado

Esto suele confundir bastante:

#### No staged

```bash
git diff
```

#### Staged

```bash
git diff --staged
```

La diferencia importa mucho.
Porque un archivo puede estar cambiado en ambos niveles:

* una parte ya agregada al stage
* otra parte aún no staged

Git permite ese caos elegante.

---

### Comparar ramas con puntos `..` y `...`

Aquí muchos repiten comandos sin entenderlos.

#### Forma simple y clara

```bash
git diff main feature
```

Ya funciona.

#### Con tres puntos

```bash
git diff main...feature
```

Eso compara desde el ancestro común hasta `feature`.

Es útil para revisar qué introduce realmente la rama `feature` respecto a donde se separó de `main`.

Para PRs suele ser más representativo.

---

### Ver diff palabra por palabra

```bash
git diff --word-diff
```

Útil para texto, markdown o documentación.
Menos útil para código largo donde el ruido puede ser peor que el problema.

---

### Ejemplo práctico real

#### Ver qué cambiaste antes de commit

```bash
git status
git diff
git add .
git diff --staged
git commit -m "Fix validation logic"
```

Ese flujo evita commits ciegos.

---

### Cuándo usarlo

Usa `git diff` para:

* revisar cambios antes de `git add`
* revisar qué vas a commitear
* comparar ramas
* revisar un commit contra otro
* entender conflictos o regresiones

---

### Diferencia con `git status`

#### `git status`

Te dice **qué archivos** cambiaron.

#### `git diff`

Te dice **qué líneas** cambiaron.

Ejemplo:

`git status` dice:

```text
modified: user.service.ts
```

`git diff` te dice exactamente qué se tocó en ese archivo.

---

### Resumen brutalmente útil

#### Ver cambios no staged

```bash
git diff
```

#### Ver cambios staged

```bash
git diff --staged
```

#### Ver todo contra último commit

```bash
git diff HEAD
```

#### Comparar commits

```bash
git diff commit1 commit2
```

#### Comparar ramas

```bash
git diff main feature
```

#### Ver solo nombres

```bash
git diff --name-only
```

#### Ver resumen

```bash
git diff --stat
```

---

### Regla práctica

Antes de hacer commit, revisa siempre esto:

```bash
git diff --staged
```

## Historial de commits(Git log)
`git log` sirve para **ver el historial de commits** del repositorio.

Dicho sin maquillaje:

> te muestra quién cambió qué, cuándo lo hizo y con qué mensaje.

Es básicamente la bitácora de Git.
Si no usas `log`, trabajas a ciegas y luego todo mundo finge que entiende de dónde salió un bug ancestral.

---

### Uso básico

```bash
git log
```

Eso muestra commits del más reciente al más antiguo.

Ejemplo típico:

```text
commit a1b2c3d4e5f6...
Author: Marco <correo@ejemplo.com>
Date:   Fri Mar 14 10:20:00 2026 -0600

    Fix login validation
```

---

### Qué muestra

Cada commit trae normalmente:

* **hash**
* **autor**
* **fecha**
* **mensaje**

---

### Problema del `git log` normal

El formato completo sirve, pero a veces es demasiado largo y tedioso.

Por eso casi siempre se usa con opciones.

---

### El más útil para trabajo diario

```bash
git log --oneline
```

Ejemplo:

```text
a1b2c3d Fix login validation
d4e5f6g Add password reset flow
h7i8j9k Initial auth module
```

Esto muestra:

* hash corto
* mensaje del commit

Mucho más práctico.

---

### Ver gráfico de ramas

```bash
git log --oneline --graph --all
```

Ejemplo:

```text
* a1b2c3d Fix login validation
* d4e5f6g Add password reset flow
| * z9y8x7w Hotfix in main
|/
* h7i8j9k Initial auth module
```

Esto te deja ver bifurcaciones y merges.

Muy útil cuando quieres entender:

* de dónde salió una rama
* si hubo merge
* si estás en historia lineal o en selva tropical

---

### Ver commits de una rama específica

```bash
git log nombre-rama
```

Ejemplo:

```bash
git log feature/login --oneline
```

---

### Ver commits de un archivo

```bash
git log -- archivo.txt
```

Ejemplo:

```bash
git log -- src/auth.ts
```

Eso muestra solo commits que tocaron ese archivo.

Muy útil para rastrear quién rompió una pieza concreta del sistema.
O quién “refactorizó” algo que ya funcionaba.

---

### Ver cambios dentro de cada commit

```bash
git log -p
```

Eso muestra el historial **más el diff** de cada commit.

Es potente, pero puede ser mucho ruido.

Más realista usarlo así:

```bash
git log -p -- src/auth.ts
```

---

### Ver un número limitado de commits

```bash
git log -n 5
```

o

```bash
git log --oneline -5
```

Eso muestra solo los últimos 5 commits.

---

### Ver commits de una persona

```bash
git log --author="Marco"
```

O con correo:

```bash
git log --author="correo@ejemplo.com"
```

---

### Buscar commits por mensaje

```bash
git log --grep="login"
```

Eso busca commits cuyo mensaje contenga “login”.

Sirve si el equipo al menos escribe mensajes decentes.
Si los commits se llaman `fix`, `cambios`, `ahora si`, entonces Git no puede rescatarte de decisiones cuestionables.

---

### Ver commits desde cierta fecha

```bash
git log --since="7 days ago"
```

O:

```bash
git log --since="2026-03-01" --until="2026-03-14"
```

Muy útil para revisar actividad reciente.

---

### Ver formato personalizado

Ejemplo compacto y bueno:

```bash
git log --pretty=format:"%h - %an, %ar : %s"
```

Salida:

```text
a1b2c3d - Marco, 2 hours ago : Fix login validation
d4e5f6g - Ana, 1 day ago : Add reset password flow
```

---

### Diferencia entre `log` y `show`

#### `git log`

Muestra una **lista de commits**

#### `git show <hash>`

Muestra el detalle de **un commit específico**

Ejemplo:

```bash
git show a1b2c3d
```

---

### Casos de uso reales

#### Ver historial general

```bash
git log --oneline --graph --all
```

#### Ver qué pasó en un archivo

```bash
git log -- src/user.service.ts
```

#### Buscar un commit específico

```bash
git log --grep="fix session"
```

#### Ver actividad reciente

```bash
git log --since="3 days ago" --oneline
```

---

### Flujo práctico para investigar algo

Supón que algo se rompió en `auth.ts`.

Primero:

```bash
git log --oneline -- src/auth.ts
```

Luego eliges un commit sospechoso y haces:

```bash
git show <hash>
```

Así rastreas cuándo cambió y cómo.

Ese flujo vale más que adivinar culpables con fe mística.

---

### Opciones más útiles en resumen

#### historial compacto

```bash
git log --oneline
```

#### historial con gráfico

```bash
git log --oneline --graph --all
```

#### últimos 10 commits

```bash
git log --oneline -10
```

#### historial de archivo

```bash
git log -- archivo.txt
```

#### buscar por mensaje

```bash
git log --grep="bugfix"
```

#### buscar por autor

```bash
git log --author="Marco"
```

#### ver diff en commits

```bash
git log -p
```

---

### Regla práctica

Para trabajo diario, estos dos te cubren muchísimo:

```bash
git log --oneline
git log --oneline --graph --all
```

Con eso ya entiendes bastante del estado histórico del repo sin tragarte una muralla de texto.

---

### Truco útil

Si quieres salir del visor de `git log`, presiona:

```text
q
```

## Marcar(Git tag)
`git tag` sirve para **marcar un commit con un nombre fijo**, normalmente para identificar **versiones importantes** como:

* `v1.0.0`
* `v1.2.3`
* `release-2026-03`
* `backend-stable`

Piensa en un tag como una **etiqueta permanente sobre un commit específico**.

No crea una rama.
No mueve trabajo.
No sirve para desarrollar.
Sirve para **señalar un punto importante en la historia**.

---

### Para qué se usa realmente

Lo más común es usarlo para:

* marcar releases
* identificar versiones desplegadas
* volver fácilmente a una versión conocida
* automatizar pipelines de CI/CD al publicar una versión

Ejemplo:

```bash
git tag v1.0.0
```

Eso etiqueta el commit actual como `v1.0.0`.

---

### Diferencia entre tag y branch

Aquí mucha gente se confunde.

#### Branch

Una rama **se mueve** cuando haces nuevos commits.

#### Tag

Un tag es **fijo**.
Se queda apuntando al commit donde fue creado.

Ejemplo:

```text
A---B---C---D  main
        ^
      v1.0.0
```

Aunque `main` siga avanzando, `v1.0.0` sigue apuntando a `C`.

---

### Ver tags

```bash
git tag
```

Salida típica:

```text
v1.0.0
v1.1.0
v2.0.0
```

---

### Crear un tag simple

```bash
git tag v1.0.0
```

Eso crea un **tag ligero** (*lightweight tag*).

Apunta al commit actual.

---

### Crear un tag sobre un commit específico

Primero ves hashes:

```bash
git log --oneline
```

Luego:

```bash
git tag v1.0.0 a1b2c3d
```

Eso pone el tag `v1.0.0` sobre ese commit.

---

### Tipos de tags

Hay dos tipos principales.

#### 1. Lightweight tag

Solo es una referencia simple.

```bash
git tag v1.0.0
```

## 2. Annotated tag

Guarda metadata extra:

* nombre del autor
* fecha
* mensaje
* opcionalmente firma GPG

Se crea así:

```bash
git tag -a v1.0.0 -m "Release version 1.0.0"
```

Este suele ser el recomendable para releases reales.

---

### Cuál deberías usar

Para versiones formales, usa **annotated tags**.

```bash
git tag -a v1.0.0 -m "Initial stable release"
```

Porque deja más contexto y es más serio para automatización y auditoría.

El lightweight tag sirve más para algo rápido o local.

---

### Ver información de un tag

```bash
git show v1.0.0
```

Si es annotated, verás mensaje y metadata.
Si es lightweight, verás solo el commit.

---

### Subir tags al remoto

Esto es importante:
crear un tag local **no lo sube automáticamente**.

#### Subir uno específico

```bash
git push origin v1.0.0
```

#### Subir todos los tags

```bash
git push origin --tags
```

Muchos crean el tag y creen que GitHub “ya sabe”. No. Git no lee mentes ni corrige omisiones ceremoniales.

---

### Borrar tags

#### Borrar tag local

```bash
git tag -d v1.0.0
```

#### Borrar tag remoto

```bash
git push origin --delete v1.0.0
```

Ojo: si ya publicaste un tag usado por otros o por pipelines, borrarlo puede ser mala idea.

---

### Checkout de un tag

Puedes moverte a un tag:

```bash
git checkout v1.0.0
```

Pero eso te deja en **detached HEAD**.

Es decir, no estás en una rama normal.
Puedes inspeccionar el código, compilar, revisar, pero si empiezas a trabajar ahí sin entenderlo, luego aparecen commits huérfanos flotando en el vacío.

Si quieres trabajar desde ese punto, mejor crea una rama:

```bash
git checkout -b hotfix/v1.0.0 v1.0.0
```

---

### Convención común de nombres

Muy común usar **SemVer** (*Semantic Versioning*):

* `v1.0.0`
* `v1.0.1`
* `v1.1.0`
* `v2.0.0`

Regla general:

* **major**: cambios incompatibles
* **minor**: funcionalidad nueva compatible
* **patch**: correcciones sin romper compatibilidad

Ejemplo:

```text
v2.3.5
```

* `2` = major
* `3` = minor
* `5` = patch

---

### Casos de uso reales

#### Marcar un release

```bash
git tag -a v1.0.0 -m "Release v1.0.0"
git push origin v1.0.0
```

#### Ver todas las versiones publicadas

```bash
git tag
```

#### Crear hotfix desde una versión anterior

```bash
git checkout -b hotfix/v1.0.0 v1.0.0
```

---

### Diferencia con release en GitHub

Un **tag** en Git es la referencia técnica.
Un **release** en GitHub suele construirse encima de un tag y puede incluir:

* título
* notas de versión
* binarios
* changelog

O sea:

* `tag` = marca técnica del commit
* `release` = presentación/publicación de esa versión

---

### Resumen directo

`git tag` = **poner una etiqueta fija sobre un commit**

Comandos más útiles:

```bash
git tag
git tag v1.0.0
git tag -a v1.0.0 -m "Release v1.0.0"
git show v1.0.0
git push origin v1.0.0
git push origin --tags
git tag -d v1.0.0
git push origin --delete v1.0.0
```

---

### Recomendación práctica

Si estás marcando una versión real del proyecto, usa esto:

```bash
git tag -a v1.0.0 -m "Release v1.0.0"
git push origin v1.0.0
```

No uses tags como si fueran ramas decorativas.
Un tag debería significar algo concreto: una versión desplegable, estable o trazable. Si empiezas a crear `prueba1`, `ahorasi`, `final-final`, ya no estás versionando; estás dejando evidencia.


## Combinar ramas(Git merge)

## Eliminar archivos untracked(Git clean)

## Conexiones a repositorios(Git remote)

## Encontrar commits especificos(Git bisect)
