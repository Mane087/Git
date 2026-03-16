`git merge` sirve para **combinar el historial de dos ramas**.
Toma los cambios de una rama y los **integra en la rama actual**.

La idea esencial:

> “Trae los cambios de esa rama y júntalos con los míos.”

### Ejemplo conceptual

Supón esta historia:

```
main
A---B---C

feature
     \
      D---E
```

Quieres integrar `feature` en `main`.

Primero te mueves a `main`:

```bash
git checkout main
```

Luego haces:

```bash
git merge feature
```

Resultado:

```
A---B---C-------M
     \          /
      D--------E
```

`M` es un **merge commit**.

Ese commit une las dos historias.

### Qué hace realmente merge

Git busca:

1. **el ancestro común**
2. calcula diferencias
3. intenta combinar cambios automáticamente

Si no hay conflictos, el merge se completa solo.

### Caso sin conflicto

Si las ramas modificaron archivos distintos, Git fusiona todo sin drama.

Ejemplo:

```
feature cambia login.js
main cambia config.js
```

Merge limpio.

### Caso con conflicto

Si ambas ramas cambiaron la **misma parte del mismo archivo**, Git no puede decidir.

Entonces verás algo así:

```
CONFLICT (content): Merge conflict in auth.js
```

Y el archivo quedará así:

```text
<<<<<<< HEAD
codigo de main
=======
codigo de feature
>>>>>>> feature
```

Tú debes elegir qué versión queda.

Luego:

```bash
git add archivo.js
git commit
```

# Flujo típico

```bash
git checkout main
git pull origin main
git merge feature-login
```

Eso integra la rama de feature en `main`.

### Tipos de merge

#### 1. Fast-forward merge

Ocurre cuando `main` no avanzó desde que creaste la rama.

Historia:

```
A---B---C main
         \
          D---E feature
```

Si haces merge:

```bash
git merge feature
```

Git solo mueve el puntero:

```
A---B---C---D---E main
```

No hay merge commit.

#### 2. Merge commit (3-way merge)

Si ambas ramas avanzaron:

```
A---B---C main
     \
      D---E feature
```

Merge produce:

```
A---B---C-------M
     \          /
      D--------E
```

### Forzar merge commit

A veces quieres mantener la historia explícita.

```bash
git merge --no-ff feature
```

Eso crea siempre un merge commit.

Se usa mucho en equipos para mantener trazabilidad de features.

### Ver merges en historial

Con:

```bash
git log --graph --oneline --all
```

Puedes ver visualmente las uniones de ramas.

### Cancelar un merge

Si empiezas un merge y todo se vuelve caótico:

```bash
git merge --abort
```

Eso regresa el repo al estado anterior.

# Cuándo usar merge

Usa `merge` cuando:

* integras una feature terminada
* haces integración en `main`
* quieres preservar historia de ramas
* trabajas con ramas compartidas

# Flujo típico con PR

En muchos proyectos:

1. creas rama

```
feature/login
```

2. haces commits

3. abres Pull Request

4. GitHub hace:

```
merge
```

o

```
rebase and merge
```

### Comandos comunes

#### Merge de rama

```bash
git merge feature
```

#### Merge con commit explícito

```bash
git merge --no-ff feature
```

#### Cancelar merge

```bash
git merge --abort
```

#### Resolver conflicto

```bash
git add archivo
git commit
```

### Ejemplo real

Supón que trabajas en:

```
feature-criterios-productos
```

Cuando terminas:

```bash
git checkout main
git pull origin main
git merge feature-criterios-productos
git push origin main
```

Eso integra el trabajo al branch principal.

### Problema común

Muchos desarrolladores hacen esto:

```bash
git merge main
```

dentro de su feature cada cinco minutos.

Resultado: historia llena de merges innecesarios.

A veces es mejor:

```
git rebase main
```

para mantener la historia limpia.

### Resumen directo

`git merge` = **combinar dos ramas**

Comando básico:

```bash
git merge nombre-rama
```

Concepto clave:

* fast-forward si es posible
* merge commit si hay divergencia
* conflictos si ambos tocaron la misma parte
