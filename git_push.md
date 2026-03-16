El comando `git push` se utiliza para subir los cambios confirmados (commits) desde tu repositorio local al repositorio remoto. Aquí te dejo una descripción detallada de los usos más comunes del comando git push:
-  **git push < romete > < branch >** Sube los cambios de la rama especificada al repositorio remoto
```Bash
git push origin main
```
-  **git push -u < romete > < branch >** Sube los cambios de la rama especificada y establece la rama en el remoto como la rama predeterminada para futuras operaciones
```Bash
git push -u origin main
```
-  **git push** Si ya has establecido un repositorio remoto y una rama predeterminada, simplemente puedes ejecutar git push sin argumentos para subir los cambios.
```Bash
git push
```
-  **git push --forcer/-f** Fuerza la subida de cambios al repositorio remoto. Este comando es peligroso porque puede sobrescribir cambios en el remoto, por lo que debe usarse con precaución.
```Bash
git push --force
git push -f
```
-  **git push --forcer-with-lease** Es una alternativa más segura a --force, ya que solo sobrescribirá los cambios en el remoto si no ha habido actualizaciones en la rama remota desde la última vez que la descargaste.
```Bash
git push --force-with-lease
```
-  **git push -u < romete >** Sube todas las ramas locales al repositorio remoto.
```Bash
git push --all origin
```
-  **git push -u < romete > --tags** Sube todas las etiquetas (tags) locales al repositorio remoto.
```Bash
git push origin --tags
```
-  **git push -u < romete > :< branch >** Elimina una rama en el repositorio remoto
```Bash
git push origin :nombre_de_la_rama
```
-  **git push -u < romete > < local > :< remote >** Sube una rama local a una rama remota con un nombre diferente.
```Bash
git push origin local-branch:remote-branch
```
-  **git push --set-upstream  < romete > < branch >** Establece la rama especificada como la rama upstream, lo que permite que futuros git pull y git push se realicen automáticamente en esta rama.
```Bash
git push --set-upstream origin nueva-rama
```