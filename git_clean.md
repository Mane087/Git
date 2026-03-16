`git clean` sirve para **eliminar archivos que Git no está rastreando** (*untracked files*) del directorio de trabajo.

En términos claros:

> borra archivos que existen en tu carpeta pero **no están en el repositorio ni en staging**.

Se usa para **limpiar el workspace** cuando quedó lleno de archivos generados, temporales o basura de compilación.

### Qué elimina

`git clean` elimina:

* archivos **untracked**
* carpetas **untracked**

Pero **no toca**:

* archivos ya committeados
* archivos en staging
* archivos modificados bajo control de Git

### Ejemplo

Supón que tienes esto:

```text
repo/
 ├── src/
 │    └── app.js
 ├── build/
 │    └── app.bundle.js
 └── temp.txt
```

Si `build/` y `temp.txt` no están versionados, `git status` mostrará:

```text
Untracked files:
  build/
  temp.txt
```

Ahora ejecutas:

```bash
git clean -f
```

Resultado:

```text
repo/
 └── src/
      └── app.js
```

Los archivos no rastreados desaparecen.

### Por qué Git exige `-f`

Si ejecutas:

```bash
git clean
```

Git responde algo como:

```text
fatal: clean.requireForce defaults to true
```

Esto es deliberado.

Git exige `-f` (*force*) porque el comando **borra archivos físicamente**, no van al staging ni a ningún lugar recuperable.

### Ver qué se borrará antes

Muy recomendable usar:

```bash
git clean -n
```

(`n` de *dry run*)

Ejemplo:

```text
Would remove temp.txt
Would remove build/
```

No elimina nada. Solo muestra lo que pasaría.

### Borrar archivos no rastreados

```bash
git clean -f
```

### Borrar carpetas también

Por defecto `git clean` **no borra directorios**.

Para eso:

```bash
git clean -fd
```

* `f` = force
* `d` = directories

### Borrar archivos ignorados (`.gitignore`)

A veces quieres eliminar **todo lo generado** (build, cache, etc.).

Para eso:

```bash
git clean -fx
```

Opciones:

* `x` = incluye archivos ignorados
* `d` = incluye carpetas

Común en builds:

```bash
git clean -fdx
```

Esto deja el repo **exactamente como recién clonado**.

### Ejemplo real en desarrollo

Supón que tienes:

```text
node_modules/
dist/
.cache/
temp.log
```

Si todo está ignorado en `.gitignore`, puedes limpiar así:

```bash
git clean -fdx
```

Esto elimina:

* `node_modules`
* `dist`
* `.cache`
* `temp.log`

Es útil cuando un build está corrupto o el entorno quedó inconsistente.

### Flujo típico de limpieza completa

Muchos desarrolladores hacen esto:

```bash
git reset --hard
git clean -fd
```

Eso deja el repo en estado limpio respecto al último commit.

Pero cuidado: si había archivos importantes no versionados, desaparecen.

### Ver qué archivos están ignorados

Antes de limpiar con `-x`, conviene ver:

```bash
git status --ignored
```

Así sabes exactamente qué Git considera ignorado.

### Diferencia con `git reset`

Esto se confunde mucho.

| Comando     | Qué afecta                  |
| ----------- | --------------------------- |
| `git reset` | archivos versionados        |
| `git clean` | archivos **no versionados** |

Ejemplo:

* modificaste `app.js` → `reset` puede revertirlo
* creaste `temp.txt` → solo `clean` lo elimina

### Comandos más usados

Ver qué se eliminará:

```bash
git clean -n
```

Eliminar archivos no rastreados:

```bash
git clean -f
```

Eliminar archivos y carpetas:

```bash
git clean -fd
```

Eliminar incluso archivos ignorados:

```bash
git clean -fdx
```

### Ejemplo práctico

Imagina que un build dejó el repo sucio.

Puedes limpiar completamente así:

```bash
git reset --hard
git clean -fdx
```

Después el repositorio queda exactamente como en el último commit.

Muchos scripts de CI hacen algo equivalente antes de compilar.

### Advertencia importante

`git clean` **no usa papelera**.

Lo que borra **no se recupera con Git**.

Por eso es buena práctica correr primero:

```bash
git clean -n
```

para ver qué se va a eliminar.

### Resumen claro

`git clean` = **eliminar archivos que Git no rastrea**

Comandos clave:

```bash
git clean -n     # simulación
git clean -f     # borrar archivos
git clean -fd    # borrar archivos y carpetas
git clean -fdx   # borrar incluso archivos ignorados
```

Un detalle curioso del diseño de Git: el comando existe porque Git asume que el **working directory puede ensuciarse con artefactos externos** (builds, compilaciones, logs, dependencias). En lugar de intentar rastrear todo, Git separa el mundo en dos: lo que controla y lo que no. `git clean` es la escoba que barre ese segundo universo cuando empieza a acumular polvo digital.
