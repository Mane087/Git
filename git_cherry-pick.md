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

### Cuándo se usa

#### 1. Pasar una corrección puntual

Ejemplo clásico:

* hiciste un hotfix en una rama
* también lo necesitas en otra rama

En vez de mergear todo, haces:

```bash
git cherry-pick <commit>
```

#### 2. Recuperar un commit útil de otra rama

Supón que en una rama experimental hiciste 10 commits, pero solo 1 realmente sirve.

No quieres arrastrar toda la basura cósmica.
Solo extraes el commit bueno.


#### 3. Aplicar un fix a release/main

Muy común:

* el fix se hizo en `develop`
* también debe entrar a `release` o `main`


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