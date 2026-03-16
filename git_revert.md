El comando git revert se utiliza para deshacer de manera segura un cambio específico en el historial de Git creando un nuevo commit que revierte los cambios introducidos por un commit anterior. A diferencia de git reset, que elimina los commits, git revert preserva el historial de cambios al agregar un nuevo commit que invierte los efectos de un commit anterior.
- **git revert < commit-hash >** Para revertir un commit específico, debes identificar el hash del commit (los primeros 7 caracteres suelen ser suficientes)
```Bash
git revert 1234abc
```
- **git revert < commit-hash 1 >..< commit-hash 2 >** Puedes revertir varios commits especificando un rango de commits
```Bash
git revert 1234abc..7890def
```
- O puedes revertir varios commits individualmente
```Bash
git revert 1234abc 5678def
```
- **git revert -m 1 < merge-commit-hash >** Revertir un commit de fusión (merge commit) puede ser un poco más complicado porque involucra múltiples ramas. Necesitas especificar el parent (padre) del merge que quieres conservar.
```Bash
git revert -m 1 1234abc
```
- **git revert -m** Si deseas proporcionar un mensaje personalizado para el commit de revert, puedes usar la opción -m o editar el mensaje durante el proceso.
```Bash
git revert -m "Revirtiendo commit X por razones Y"
```
- **git revert --no-commit < commit-hash >** Si prefieres no hacer el commit inmediatamente, puedes utilizar la opción --no-commit (o -n) para revertir los cambios y mantenerlos en la área de preparación (staging area) para que los puedas revisar antes de confirmar.
```Bash
git revert --no-commit 1234abc
```
- **git revert --no-edit < commit-hash >** Usa --no-edit si deseas revertir un commit sin abrir el editor de texto para modificar el mensaje del commit.
```Bash
git revert --no-edit 1234abc
```