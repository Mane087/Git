`git remote` sirve para **gestionar los repositorios remotos asociados a tu repositorio local**.

Un *remote* es simplemente una **referencia con nombre a otro repositorio Git**, normalmente en:

* GitHub
* GitLab
* Bitbucket
* servidor interno
* otro repositorio local

El nombre más común es **`origin`**, pero es solo una convención, no una regla mágica.

### Idea central

Cuando clonas un repo:

```bash
git clone https://github.com/org/proyecto.git
```

Git crea automáticamente:

```text
remote: origin
```

Eso significa:

```text
origin → https://github.com/org/proyecto.git
```

Tu repo local ahora sabe **de dónde puede traer cambios y a dónde puede enviar commits**.

### Ver los remotes

```bash
git remote
```

Salida típica:

```text
origin
```

### Ver las URLs de los remotes

```bash
git remote -v
```

Ejemplo:

```text
origin  https://github.com/org/proyecto.git (fetch)
origin  https://github.com/org/proyecto.git (push)
```

Esto muestra:

* URL para **traer cambios**
* URL para **enviar cambios**

### Agregar un remote

Si tienes un repo local sin remoto:

```bash
git remote add origin https://github.com/org/proyecto.git
```

Ahora puedes hacer:

```bash
git push origin main
```

### Cambiar la URL de un remote

A veces cambias de HTTPS a SSH.

```bash
git remote set-url origin git@github.com:org/proyecto.git
```

Ahora `origin` apunta a esa nueva dirección.

### Eliminar un remote

```bash
git remote remove origin
```

Esto solo elimina la referencia.
No borra el repositorio remoto real.

### Renombrar un remote

```bash
git remote rename origin upstream
```

Ahora el nombre cambia.

### Uso típico en proyectos con fork

En flujos de trabajo con **fork**, suele haber dos remotes:

```text
origin
upstream
```

Ejemplo:

```text
origin   → tu fork
upstream → repo original
```

Verías algo como:

```bash
git remote -v
```

```text
origin   https://github.com/tuusuario/proyecto.git
upstream https://github.com/org/proyecto.git
```

### Flujo típico con upstream

Traer cambios del repo original:

```bash
git fetch upstream
git merge upstream/main
```

O con rebase:

```bash
git fetch upstream
git rebase upstream/main
```

### Ver información de un remote

```bash
git remote show origin
```

Esto muestra:

* URL
* ramas rastreadas
* configuración de fetch
* ramas que se sincronizan

Ejemplo:

```text
Fetch URL: https://github.com/org/proyecto.git
Push URL: https://github.com/org/proyecto.git
HEAD branch: main
```

### Ver ramas remotas

```bash
git branch -r
```

Ejemplo:

```text
origin/main
origin/dev
origin/feature-login
```

### Relación con otros comandos

`git remote` solo **configura repositorios externos**.

Los comandos que trabajan con esos remotes son:

| comando     | función        |
| ----------- | -------------- |
| `git fetch` | traer cambios  |
| `git pull`  | fetch + merge  |
| `git push`  | enviar commits |

Ejemplo:

```bash
git fetch origin
git push origin main
```

### Ejemplo completo real

Supón que creaste un repo local:

```bash
git init
```

Luego lo conectas a GitHub:

```bash
git remote add origin https://github.com/usuario/proyecto.git
```

Verificas:

```bash
git remote -v
```

Luego subes tu código:

```bash
git push -u origin main
```

Ahora tu repo local y remoto están conectados.

### Problema común

Mucha gente cree que `origin` es especial.

No lo es.

Podrías llamar a tu remoto:

```text
server
production
banana
```

Git funcionaría igual.

`origin` solo es el nombre que `git clone` usa por defecto.

### Resumen claro

`git remote` = **gestionar repositorios remotos**

Comandos importantes:

Ver remotes:

```bash
git remote -v
```

Agregar remote:

```bash
git remote add origin <url>
```

Cambiar URL:

```bash
git remote set-url origin <url>
```

Eliminar remote:

```bash
git remote remove origin
```

Ver detalles:

```bash
git remote show origin
```

Un detalle interesante del diseño de Git: los *remotes* no son realmente servidores especiales ni conexiones activas. Son simplemente **alias almacenados en `.git/config` que apuntan a otra ubicación Git**. Todo el sistema distribuido de Git funciona porque cada repositorio puede tratar a cualquier otro como remoto, sin jerarquías obligatorias ni servidor central real.
