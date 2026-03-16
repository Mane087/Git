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


### Opciones útiles

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

### Importante

`merge` **preserva historia real**
`rebase` **crea historia lineal**

Por eso algunos equipos prefieren:

```
rebase local
merge en main
```