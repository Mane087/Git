`git stash` sirve para **guardar temporalmente cambios no confirmados** sin hacer un commit.

Es como decirle a Git:

> “Guárdame este trabajo en un cajón porque necesito cambiar de rama o limpiar el working tree, pero todavía no quiero hacer commit.”

### Qué guarda

Normalmente guarda cambios en:

* archivos **modificados**
* archivos en **staging**
* opcionalmente archivos **no rastreados** (`untracked`)

Después de hacer `stash`, tu directorio queda más limpio, casi como si no hubieras tocado nada.

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

### Ponerle nombre

Puedes guardar un stash con mensaje:

```bash
git stash push -m "avance del formulario de login"
```

Eso ayuda bastante porque si haces 8 stashes seguidos, luego todos parecen restos arqueológicos de decisiones cuestionables.


### Ver qué hay dentro

```bash
git stash show
```

Más detalle:

```bash
git stash show -p
```

Eso muestra el diff guardado.

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

### Cuándo usarlo

#### Úsalo cuando:

* necesitas cambiar de rama rápido
* aún no quieres hacer commit
* tienes trabajo a medias
* quieres probar algo y luego volver

#### No lo uses como sistema de versionado paralelo

Si tienes cosas importantes durante días en stash, eso ya huele mal.
Para trabajo real y duradero, mejor usa commits en una rama.

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

### Problemas comunes

#### 1. Conflictos al hacer `pop` o `apply`

Sí, también puede haber conflictos.
Porque el mundo es absurdo y Git no regala paz interior.

Si cambió el mismo archivo entre el stash y la rama actual, tendrás que resolverlo manualmente.

#### 2. Creer que stash reemplaza commits

No.
`stash` es temporal.
No es historial formal del proyecto.


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