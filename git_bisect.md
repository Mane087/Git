`git bisect` es una herramienta para **encontrar automáticamente el commit que introdujo un bug** usando **búsqueda binaria**.

La idea es elegante y brutalmente eficiente:

> si sabes que un commit viejo funcionaba y uno nuevo está roto, Git puede ir probando commits intermedios para encontrar exactamente dónde apareció el problema.

Esto evita revisar manualmente decenas o cientos de commits.

### Concepto clave: búsqueda binaria

Supón que tienes 100 commits.

En vez de revisar uno por uno:

```
1,2,3,4,5,6,7,8...
```

`git bisect` prueba **el punto medio**.

Si el bug está ahí:

* revisa la mitad más vieja
  si no:

* revisa la mitad más nueva

Cada paso **reduce el espacio de búsqueda a la mitad**.

Con 100 commits, normalmente encuentras el culpable en **~7 pasos**.

Esto es literalmente el mismo algoritmo que se usa para buscar en listas ordenadas.

### Cuándo usarlo

Cuando sabes:

* que **ahora algo está roto**
* que **antes funcionaba**
* pero **no sabes en qué commit se rompió**

### Flujo básico

#### 1 iniciar bisect

```bash
git bisect start
```

#### 2 marcar el commit roto

Normalmente el actual:

```bash
git bisect bad
```

#### 3 marcar un commit que sí funcionaba

Ejemplo:

```bash
git bisect good a1b2c3d
```

Ahora Git empieza la búsqueda.

### Qué hace Git ahora

Git automáticamente se mueve a un commit intermedio:

```text
Bisecting: 12 revisions left to test after this
```

Ahora pruebas el código.

* si el bug aparece → `bad`
* si funciona → `good`

### Ejemplo

```bash
git bisect bad
git bisect good a1b2c3d
```

Git salta a un commit intermedio.

Pruebas la app.

Si está roto:

```bash
git bisect bad
```

Si funciona:

```bash
git bisect good
```

Git vuelve a calcular el siguiente punto.

Repite esto hasta encontrar el commit culpable.

### Resultado final

Git dirá algo como:

```text
commit d4e5f6g is the first bad commit
```

Ese es el commit que introdujo el bug.

### Terminar bisect

Cuando termines:

```bash
git bisect reset
```

Esto te regresa a la rama original.

### Ejemplo real

Supón que tu proyecto tiene esta historia:

```
A---B---C---D---E---F---G---H
```

Sabes:

* `H` está roto
* `B` funcionaba

Entonces:

```bash
git bisect start
git bisect bad H
git bisect good B
```

Git probará:

```
E
```

Si `E` funciona:

```
bug está entre F y H
```

Si `E` está roto:

```
bug está entre C y E
```

Así se reduce el espacio de búsqueda rápidamente.

### Automatizar pruebas con bisect

Esto es donde se vuelve realmente poderoso.

Si tienes un script de prueba que devuelve:

* `0` → funciona
* `1` → falla

Puedes hacer:

```bash
git bisect run ./test-script.sh
```

Git automáticamente:

1. cambia commit
2. ejecuta el script
3. marca good/bad
4. continúa

Hasta encontrar el commit culpable.

Esto es extremadamente útil en proyectos grandes.

### Ejemplo automatizado

```bash
git bisect start
git bisect bad
git bisect good v1.2.0
git bisect run npm test
```

Git ejecutará `npm test` en cada commit hasta encontrar el primero que falla.

### Problema común

Para usar `bisect` necesitas dos cosas claras:

1. un commit **bueno**
2. un commit **malo**

Si no sabes cuándo empezó el bug, primero necesitas investigar eso.

### Situaciones donde bisect brilla

* bugs introducidos semanas atrás
* regresiones difíciles de rastrear
* proyectos con cientos de commits
* cambios donde el culpable no es obvio

### Situaciones donde no sirve tanto

* cuando el bug depende de estado externo
* cuando el proyecto no compila en commits antiguos
* cuando el error es no determinístico

### Comandos clave

Iniciar bisect:

```bash
git bisect start
```

Marcar commit roto:

```bash
git bisect bad
```

Marcar commit bueno:

```bash
git bisect good <commit>
```

Automatizar pruebas:

```bash
git bisect run script.sh
```

Terminar bisect:

```bash
git bisect reset
```

### Resumen directo

`git bisect` = **encontrar el commit que introdujo un bug usando búsqueda binaria**

Flujo típico:

```bash
git bisect start
git bisect bad
git bisect good <commit-bueno>
# probar
git bisect good | git bisect bad
# repetir
git bisect reset
```

Un detalle fascinante del diseño de Git es que `bisect` convierte el historial del repositorio en **un espacio de búsqueda algorítmico**. En vez de revisar commits manualmente, Git usa el mismo principio matemático que emplean los algoritmos de búsqueda eficientes. Lo que para un humano podría tomar horas revisando commits uno por uno, Git lo reduce a unos pocos pasos lógicos.
