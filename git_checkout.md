En Git, cambiar de ramas es una operación común que se realiza utilizando el comando `git checkout` o, en versiones más recientes de Git, `git switch`. 
- **git checkout/switch name_branch** Puedes cambiar a una rama existente utilizando este comando
```Bash
git checkout nombre_de_la_rama
git switch nombre_de_la_rama
```
- **git checkout -b/switch -c name_new_branch** Puedes cambiar a una rama existente utilizando este comando
```Bash
git checkout -b nombre_de_la_nueva_rama
git switch -c nombre_de_la_nueva_rama
```
- **git branch** Para ver una lista de todas las ramas en tu repositorio
```Bash
git branch
```
-  **git branch -a** Para ver todas las ramas, incluidas las remotas
```Bash
git branch -a
```
-  **git checkout/switch -** Si deseas cambiar a la rama en la que estabas anteriormente
```Bash
git checkout -
git switch -
```
-  **git checkout/switch -f name_branch** Si tienes cambios no confirmados que no deseas perder al cambiar de rama, puedes forzar el cambio de rama (esto sobrescribirá tus cambios no confirmados)
```Bash
git checkout -f nombre_de_la_rama
git switch -f nombre_de_la_rama
```
-  **git merge name_branch** Una vez que hayas cambiado de rama, puedes fusionar cambios desde otra rama
```Bash
git merge nombre_de_otra_rama
```
-  **git branch -d name_branch** Para eliminar una rama local (después de cambiar a otra rama)
```Bash
git branch -d nombre_de_la_rama
```
-  **git branch -D name_branch** Si la rama no está completamente fusionada, y deseas forzar la eliminación
```Bash
git branch -D nombre_de_la_rama
```
-  **git checkout/switch name_branch_remote** Si deseas cambiar a una rama remota que aún no existe localmente, debes hacer lo siguiente
```Bash
git checkout nombre_de_la_rama_remota
git switch --track origen/nombre_de_la_rama_remota
```