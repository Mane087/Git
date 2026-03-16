El comando git commit se utiliza para guardar los cambios en la área de preparación (staging area) en el historial del repositorio de Git. Cuando realizas un commit, estás creando una instantánea de los cambios en ese momento, que luego puedes revertir o fusionar si es necesario. dentro de este mismo comando se le pueden agregar otras instrucciones:

```Bash
git commit
```

- **git commit -m "mensaje"** Realiza un commit con un mensaje específico sin abrir un editor de texto. El mensaje de confirmación se proporciona directamente en la línea de comandos.
```Bash
git commit -m "Agrega nueva función de autenticación"
```
- **git commit -a** Realiza un commit que incluye todos los cambios en los archivos rastreados (tracked), es decir, modifica y confirma automáticamente todos los archivos que han sido modificados o eliminados, pero no nuevos archivos.
```Bash
git commit -a -m "Corrige errores en el sistema de autenticación"
```
- **git commit --amend** Modifica el último commit. Permite cambiar el mensaje de confirmación o agregar más cambios al último commit sin crear uno nuevo.
```Bash
git commit --amend -m "Mensaje corregido del último commit"
```
- **git commit --no-edit** Realiza un commit sin modificar el mensaje del commit anterior cuando se usa junto con --amend.
```Bash
git commit --amend --no-edit
```
- **git commit --author="Nombre < email@example.com >"** Realiza un commit con un autor específico diferente del autor predeterminado configurado en Git.
```Bash
git commit --author="Juan Pérez <juan@example.com>" -m "Mensaje de commit con autor específico"
```
- **git commit --dry-run** Muestra qué archivos serían incluidos en el commit sin realizar realmente el commit.
```Bash
git commit --dry-run
```
- **git commit --squash < commit >** Combina (squash) los cambios del commit especificado con el siguiente commit.
```Bash
git commit --squash HEAD~1 -m "Combina los cambios con el último commit"
```
- **git commit --allow-empty** Realiza un commit incluso si no hay cambios en la área de preparación. Esto es útil para crear commits que solo contienen un mensaje (por ejemplo, para marcar un punto en el historial).
```Bash
git commit --allow-empty -m "Marcador de hitos sin cambios"
```
- **git commit --signoff** Añade una línea de sign-off en el final del mensaje del commit, mostrando quién realizó el commit, como una especie de firma.
```Bash
git commit --signoff -m "Mensaje de commit con sign-off"
```