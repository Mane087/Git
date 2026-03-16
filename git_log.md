`git log` sirve para **ver el historial de commits** del repositorio.

Dicho sin maquillaje:

> te muestra quién cambió qué, cuándo lo hizo y con qué mensaje.

Es básicamente la bitácora de Git.
Si no usas `log`, trabajas a ciegas y luego todo mundo finge que entiende de dónde salió un bug ancestral.

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

### Qué muestra

Cada commit trae normalmente:

* **hash**
* **autor**
* **fecha**
* **mensaje**

### Problema del `git log` normal

El formato completo sirve, pero a veces es demasiado largo y tedioso.

Por eso casi siempre se usa con opciones.


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


### Ver commits de una rama específica

```bash
git log nombre-rama
```

Ejemplo:

```bash
git log feature/login --oneline
```

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

### Ver un número limitado de commits

```bash
git log -n 5
```

o

```bash
git log --oneline -5
```

Eso muestra solo los últimos 5 commits.

### Ver commits de una persona

```bash
git log --author="Marco"
```

O con correo:

```bash
git log --author="correo@ejemplo.com"
```

### Buscar commits por mensaje

```bash
git log --grep="login"
```

Eso busca commits cuyo mensaje contenga “login”.

Sirve si el equipo al menos escribe mensajes decentes.
Si los commits se llaman `fix`, `cambios`, `ahora si`, entonces Git no puede rescatarte de decisiones cuestionables.

### Ver commits desde cierta fecha

```bash
git log --since="7 days ago"
```

O:

```bash
git log --since="2026-03-01" --until="2026-03-14"
```

Muy útil para revisar actividad reciente.

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

### Diferencia entre `log` y `show`

#### `git log`

Muestra una **lista de commits**

#### `git show <hash>`

Muestra el detalle de **un commit específico**

Ejemplo:

```bash
git show a1b2c3d
```

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

### Regla práctica

Para trabajo diario, estos dos te cubren muchísimo:

```bash
git log --oneline
git log --oneline --graph --all
```

Con eso ya entiendes bastante del estado histórico del repo sin tragarte una muralla de texto.

### Truco útil

Si quieres salir del visor de `git log`, presiona:

```text
q
```