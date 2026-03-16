`git reset` es un comando que **mueve el puntero de una rama a otro commit** y opcionalmente **deshace cambios en staging o en el working directory**.

> cambia el estado del repositorio como si ciertos commits o cambios nunca hubieran ocurrido.

Es un comando poderoso… y peligroso si no sabes exactamente qué estás moviendo.

### Ejemplo

Git tiene tres estados principales:

| Estado                   | Qué es                            |
| ------------------------ | --------------------------------- |
| **HEAD**                 | el commit actual                  |
| **Index (staging area)** | lo que está preparado para commit |
| **Working directory**    | archivos en tu carpeta            |

`git reset` puede afectar **uno, dos o los tres** dependiendo del modo.

### Sintaxis básica

```bash
git reset <modo> <commit>
```

Ejemplo:

```bash
git reset --soft HEAD~1
```

Eso mueve la rama **un commit atrás**.

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

#### Mixed

```bash
git reset HEAD~1
```

Resultado:

```
A---B (HEAD)
```

Cambios siguen en archivos, pero **no en staging**.

#### Hard

```bash
git reset --hard HEAD~1
```

Resultado:

```
A---B (HEAD)
```

Cambios de `C` **desaparecen completamente**.

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

#### borrar todo lo que hiciste desde el último commit

```bash
git reset --hard HEAD
```

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


### Resumen brutalmente práctico

| comando                   | efecto                               |
| ------------------------- | ------------------------------------ |
| `git reset --soft HEAD~1` | deshace commit pero mantiene staging |
| `git reset HEAD~1`        | deshace commit y limpia staging      |
| `git reset --hard HEAD~1` | borra commit y cambios               |
| `git reset archivo`       | saca archivo del staging             |

Un detalle curioso: muchos desarrolladores creen que `git reset` “borra commits”. En realidad no los destruye inmediatamente; solo mueve el puntero de la rama. Durante un tiempo todavía existen en el **reflog**, como fósiles digitales flotando en el repositorio. Esa es la razón por la que a veces puedes recuperar un desastre… incluso después de un `--hard`.