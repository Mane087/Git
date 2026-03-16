`git diff` sirve para **ver diferencias entre estados del código**.

Dicho simple:

> te muestra qué cambió, línea por línea.

Es de los comandos más útiles de Git, porque antes de hacer `add`, `commit`, `stash` o cualquier otra travesura, necesitas ver **qué demonios cambiaste realmente**.


### Qué compara

`git diff` puede comparar varias cosas:

* cambios en tus archivos **sin stage**
* cambios que ya están en **staging**
* diferencias entre **commits**
* diferencias entre **ramas**
* diferencias de un archivo específico

### Caso más común

#### Ver cambios no staged

```bash
git diff
```

Esto compara:

* tu **working directory**
* contra el **staging area**

O sea, te muestra lo que cambiaste **pero todavía no has hecho `git add`**.

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

### Flujo típico útil

```bash
git diff
git add archivo.txt
git diff --staged
```

Primero ves lo no staged, luego ves lo staged.

### Comparar commits

```bash
git diff <commit1> <commit2>
```

Ejemplo:

```bash
git diff a1b2c3d d4e5f6g
```

Eso muestra la diferencia entre esos dos commits.

### Comparar ramas

```bash
git diff main feature/login
```

Te muestra qué cambia entre ambas ramas.

Muy útil para entender:

* qué trae una rama
* qué falta
* si realmente el PR hace lo que dice y no metió basura lateral

### Comparar solo un archivo

```bash
git diff archivo.txt
```

O staged:

```bash
git diff --staged archivo.txt
```

Eso limita la salida a un solo archivo.

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

### Comparar working tree contra un commit

```bash
git diff HEAD
```

Esto muestra todo lo distinto entre tu estado actual y el último commit, incluyendo cambios staged y no staged.

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

### Ver diff palabra por palabra

```bash
git diff --word-diff
```

Útil para texto, markdown o documentación.
Menos útil para código largo donde el ruido puede ser peor que el problema.

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

### Cuándo usarlo

Usa `git diff` para:

* revisar cambios antes de `git add`
* revisar qué vas a commitear
* comparar ramas
* revisar un commit contra otro
* entender conflictos o regresiones

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

### Regla práctica

Antes de hacer commit, revisa siempre esto:

```bash
git diff --staged
```