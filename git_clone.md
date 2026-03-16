`git clone` sirve para **copiar un repositorio remoto completo a tu máquina local**.

En otras palabras:

> crea una carpeta con el proyecto, su historial de commits, sus ramas remotas y la configuración básica para trabajar con ese repo.

No solo baja archivos.
También baja **la metadata de Git**.

### Sintaxis básica

```bash
git clone <url-del-repositorio>
```

Ejemplo:

```bash
git clone https://github.com/usuario/proyecto.git
```

Eso crea una carpeta llamada `proyecto`.

### Qué hace exactamente

Cuando ejecutas `git clone`:

1. descarga el contenido del repositorio
2. descarga el historial de commits
3. crea la carpeta `.git`
4. configura el remoto `origin`
5. deja una rama local lista para trabajar

### Ejemplo real

```bash
git clone https://github.com/lynxworxs/lynxwebex.git
```

Luego:

```bash
cd lynxwebex
git remote -v
```

Verás algo como:

```bash
origin  https://github.com/lynxworxs/lynxwebex.git (fetch)
origin  https://github.com/lynxworxs/lynxwebex.git (push)
```