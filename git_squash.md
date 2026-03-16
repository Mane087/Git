En Git, **squash** significa **combinar varios commits en uno solo**.

La idea es esta:

> “Tengo varios commits pequeños, desordenados o de corrección, y quiero dejarlos como un solo commit limpio.”

### Para qué sirve

Sirve mucho cuando hiciste algo así:

```bash
git commit -m "add login form"
git commit -m "fix login form"
git commit -m "fix typo"
git commit -m "adjust validation"
```

Eso funciona, pero el historial queda medio parchado.

Con squash, puedes convertir eso en algo como:

```bash
git commit -m "Add login form with validation"
```

Mucho más limpio.

### Cuándo se usa

Se usa mucho en estos casos:

* antes de abrir un PR
* antes de hacer merge a `main`
* para agrupar commits de corrección
* para dejar una historia más clara y legible

No se usa para “hacer magia”; se usa para **limpiar historial**.

### Ejemplo

Tienes esta rama:

```text
A---B---C---D
```

Donde:

* `B` = add feature
* `C` = fix bug
* `D` = typo / ajuste menor

Si haces squash de `B`, `C` y `D`, queda algo así:

```text
A---E
```

Donde `E` contiene el resultado final de esos tres commits.

### Cómo se hace

La forma más común es con **rebase interactivo**:

```bash
git rebase -i HEAD~3
```

Eso abre algo así:

```text
pick a1b2c3 add login form
pick d4e5f6 fix login validation
pick g7h8i9 fix typo
```

Y lo cambias a:

```text
pick a1b2c3 add login form
squash d4e5f6 fix login validation
squash g7h8i9 fix typo
```

Git entonces:

1. toma el primer commit
2. une los otros commits con ese
3. te deja editar el mensaje final

Resultado: **un solo commit**

### Diferencia entre `squash` y `fixup`

En rebase interactivo hay dos opciones muy parecidas.

#### `squash`

Une commits **y te deja combinar/editar mensajes**.

```text
pick a1b2c3 add login form
squash d4e5f6 fix validation
```

#### `fixup`

Une commits pero **descarta el mensaje del commit secundario**.

```text
pick a1b2c3 add login form
fixup d4e5f6 fix validation
```

Si ya sabes que el segundo mensaje no importa, `fixup` es más limpio.

### Ejemplo real

Supón que hiciste estos commits:

```bash
git log --oneline
```

```text
c3f1111 adjust button spacing
b2e2222 fix validation
a1d3333 add user form
```

Quieres dejar eso en uno solo:

```bash
git rebase -i HEAD~3
```

Y en el editor:

```text
pick a1d3333 add user form
squash b2e2222 fix validation
squash c3f1111 adjust button spacing
```

Git te pedirá el mensaje final, por ejemplo:

```text
Add user form with validation and UI adjustments
```

---

### `Squash and merge`

GitHub también usa este concepto.

Cuando haces un PR, a veces aparece la opción:

```text
Squash and merge
```

Eso significa:

* toma todos los commits del PR
* los combina en uno solo
* mete ese único commit a la rama destino

Muy útil cuando una rama tiene 12 commits de trabajo incremental, pero en `main` quieres dejar solo uno limpio.

### Ventajas

#### Historial más limpio

En vez de esto:

```text
add form
fix form
fix form again
now yes
final
final-final
```

quedas con:

```text
Add user form with validation
```

#### Más fácil de leer

Al revisar historial, cada commit representa una unidad lógica real.

#### Mejor para auditoría

Especialmente si en tu equipo quieren commits claros y trazables.

### Desventajas o cuidado

#### Reescribe historia

Hacer squash cambia hashes de commits.

Por eso, si esos commits ya fueron publicados y otros ya trabajan sobre ellos, puedes causar problemas.

#### Puede ocultar proceso intermedio útil

A veces el detalle de cómo evolucionó algo sí importa.
No siempre conviene aplastar todo.

Si squash-eas demasiado, el historial queda limpio, sí, pero también pierde contexto.

### Cuándo conviene y cuándo no

#### Conviene

* commits locales
* commits de corrección pequeña
* ramas de feature antes de merge
* PRs con mucho ruido

#### No conviene tanto

* ramas compartidas activamente
* commits ya usados por otros
* cuando cada commit tiene valor histórico propio

### Diferencia con merge

Esto se confunde bastante.

#### Merge normal

Conserva todos los commits y la historia de ramas.

#### Squash

No conserva esa secuencia tal cual; la compacta en un commit.

### Resumen directo

**Squash = unir varios commits en uno solo**

Formas comunes:

#### Con rebase interactivo

```bash
git rebase -i HEAD~3
```

y cambiar:

```text
pick
squash
squash
```

#### En GitHub

usar **Squash and merge** en el PR

### Regla práctica

Si tu rama tiene commits tipo:

* `fix`
* `typo`
* `ahora si`
* `ajuste`
* `cambio 2`

eso pide squash a gritos.
No por estética solamente, sino porque ese historial no comunica intención técnica; comunica improvisación.
