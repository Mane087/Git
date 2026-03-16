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

### Crear un tag simple

```bash
git tag v1.0.0
```

Eso crea un **tag ligero** (*lightweight tag*).

Apunta al commit actual.

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

### Cuál deberías usar

Para versiones formales, usa **annotated tags**.

```bash
git tag -a v1.0.0 -m "Initial stable release"
```

Porque deja más contexto y es más serio para automatización y auditoría.

El lightweight tag sirve más para algo rápido o local.

### Ver información de un tag

```bash
git show v1.0.0
```

Si es annotated, verás mensaje y metadata.
Si es lightweight, verás solo el commit.

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

### Recomendación práctica

Si estás marcando una versión real del proyecto, usa esto:

```bash
git tag -a v1.0.0 -m "Release v1.0.0"
git push origin v1.0.0
```

No uses tags como si fueran ramas decorativas.
Un tag debería significar algo concreto: una versión desplegable, estable o trazable. Si empiezas a crear `prueba1`, `ahorasi`, `final-final`, ya no estás versionando; estás dejando evidencia.

