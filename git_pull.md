- **git pull < remote > < branch >** Descarga los cambios de la rama especificada en el repositorio remoto y los fusiona con la rama actual.
```Bash
git pull origin main
```
- **git pull** Si ya tienes una rama predeterminada configurada con un repositorio remoto (por ejemplo, después de git clone), puedes simplemente ejecutar git pull para descargar y fusionar los cambios.
```Bash
git pull
```
- **git pull --rebase** En lugar de fusionar los cambios, git pull --rebase aplica tus commits locales en la parte superior de los cambios descargados. Esto mantiene un historial más limpio sin merges adicionales.
```Bash
git pull --rebase origin main
```
- **git pull --no-commit** Descarga los cambios y realiza la fusión, pero no hace un commit automático. Esto te permite revisar los cambios antes de hacer el commit.
```Bash
git pull --no-commit origin main
```
- **git pull --no-rebase** Fuerza una fusión en lugar de un rebase cuando la configuración predeterminada es hacer rebase.
```Bash
git pull --no-rebase origin main
```
- **git pull --ff-only** Realiza un pull solo si puede hacer un "fast-forward" sin necesidad de una fusión. Si no es posible, el pull falla.
```Bash
git pull --ff-only origin main
```
- **git pull --depth=< n >** Realiza un pull con una profundidad específica, útil para obtener solo los últimos commits.
```Bash
git pull origin main --depth=1
```
- **git pull --allow-unrelated-histories** Permite la fusión de dos ramas sin un historial común, útil cuando se están combinando dos repositorios diferentes..
```Bash
git pull origin main --allow-unrelated-histories
```
- **git pull --quiet** Suprime la salida de mensajes informativos durante el pull.
```Bash
git pull --quiet origin main
```
- **git pull --verbose** Muestra mensajes adicionales para un pull más detallado.
```Bash
git pull --verbose origin main
```