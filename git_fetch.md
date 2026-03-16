El comando `git fetch` se utiliza para descargar objetos y referencias desde un repositorio remoto al repositorio local. A diferencia de git pull, git fetch no fusiona automáticamente los cambios en la rama actual; simplemente actualiza las referencias remotas en tu repositorio local. Aquí te dejo una descripción detallada de los usos más comunes del comando git fetch.

- **git fetch < remote >** Descarga todos los cambios del repositorio remoto especificado (normalmente origin), actualizando las referencias remotas locales.
```Bash
git fetch origin
```
- **git fetch** Descarga todos los cambios de todos los repositorios remotos configurados.
```Bash
git fetch
```
- **git fetch < remote > < branch >** Descarga solo la rama especificada desde el remoto.
```Bash
git fetch origin main
```
- **git fetch < remote >** Descarga todos los cambios del repositorio remoto especificado (normalmente origin), actualizando las referencias remotas locales.
```Bash
git fetch origin
```
- **git fetch --all** Descarga todas las ramas y etiquetas de todos los remotos configurados en el repositorio local.
```Bash
git fetch --all
```
- **git fetch --prune** Elimina las referencias remotas que han sido eliminadas en el repositorio remoto.
```Bash
git fetch --prune
```
- **git fetch --tags** Descarga todas las etiquetas (tags) del repositorio remoto.
```Bash
git fetch --tags
```
- **git fetch < remote > --depth=< n >** Descarga una cantidad limitada de commits más recientes, útil para trabajar con historiales grandes.
```Bash
git fetch origin --depth=1
```
- **git fetch < remote > < branch >: < new_branch_local >** Descarga una rama específica del remoto y crea una nueva rama local a partir de ella.
```Bash
git fetch origin feature-branch:new-local-branch
```
- **git fetch < remote > --no-tags** Evita descargar las etiquetas (tags) del remoto.
```Bash
git fetch origin --no-tags
```
- **git fetch < remote > --dry-run** Muestra lo que se descargaría sin realizar realmente la descarga.
```Bash
git fetch origin --dry-run
```