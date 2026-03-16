Para inicializar un repositorio usando git se usa el sigueinte comando:

```Bash
git init
```
## Agregar cambios(Git add)
```Bash
git add
```
Este comando nos permite agregar los ultimos cambios de nuestros archivos al stage de git, dentro de este mismo comando se le pueden agregar otras instrucciones:

- **git add .** Agrega todos los cambios nuevos.
```Bash
git add .
```
- **git add < name_file >** Agrega los cambios del archivo especificado.
```Bash
git add archivo.txt
```
- **git add -A o --all**  Agrega todos los cambios en el repositorio, incluyendo archivos modificados, nuevos y eliminados.
```Bash
git add -A
git add --all
```
- **git add -u**  Agrega los archivos modificados y eliminados al stage, pero no los nuevos archivos.
```Bash
git add -u
```
- **git add -p < name_file >**  Agrega los archivos modificados y eliminados al stage, pero no los nuevos archivos. Permite agregar cambios parciales de un archivo a la área de preparación. Esto es útil si deseas agregar solo ciertas líneas o secciones de un archivo.
```Bash
git add -p archivo.txt
```
- **git add --patch < name_file >** Similar a git add -p, este comando te permite revisar y agregar cambios de manera interactiva, división por división (hunk).
```Bash
git add --patch archivo.txt
```
- **git add --f < archivo_ignorado >** Fuerza la adición de archivos ignorados por .gitignore.
```Bash
git add -f archivo_ignorado.txt
```
- **git add < directorio >** Agrega todos los archivos en un directorio específico.
```Bash
git add src/
```
- **git add < .extension >** Agrega todos los archivos que coincidan con un patrón específico.
```Bash
git add "*.txt" 
```