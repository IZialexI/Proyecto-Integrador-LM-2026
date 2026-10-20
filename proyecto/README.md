# Batman: Arkham

- **Nombre:** David Cabrera González
- **Usuario de GitHub:** IZialexI
- **Tema elegido:** la saga de videojuegos Batman: Arkham

## Por qué he elegido este tema

Tenía que ser una web tematizada, así que pensé en una de las sagas de videojuegos que más me gustan, habría otras, pero conociéndome, me extendería demasiado

## Qué he hecho en esta entrega

- **1.ª entrega:** una web estática (aún sin CSS) y un .xml con algunos datos referentes a los juegos.
- **UD3:** estructura HTML completa en todas las páginas, mapa del sitio y una página nueva (`juegos.html`) con los datos del XML.

## Palabra del día

- **1.ª entrega:** anticristo
- **UD3:** contexto

## UD3 · Estructura HTML

### Punto de partida

- **`document.compatMode` (antes):** `CSS1Compat`
- **Qué significa:** el navegador renderiza la página en **modo estándar** (no en *quirks mode*, que devolvería `BackCompat`). Es así porque `index.html` ya empieza con `<!DOCTYPE html>` en la primera línea.

### Lo que le falta a `index.html`

1. **Metadatos incompletos:** no tiene `description`, `keywords` ni `author`, y el `title` no sigue el formato `Inicio | Nombre del proyecto`.
2. **Jerarquía de títulos pobre:** solo hay `h1` y `h2`, sin ningún `h3`, y además el `h2` justo debajo del `h1` se usa como subtítulo en vez de como sección.
3. **Sin bloques ni comentarios de estructura:** todo el contenido va suelto en el `body`, sin `div` que agrupen las secciones, sin comentarios por bloque, sin `hr`, sin pie de página y sin el comentario del menú de navegación.

### Resultado final

- **`document.compatMode` (después):** `CSS1Compat`. Sigue en modo estándar, porque todas las páginas empiezan con `<!DOCTYPE html>` en la primera línea.
- **Validador W3C (validator.w3.org):** 0 errores y 0 avisos en las 6 páginas (`index`, `asylum`, `city`, `origins`, `knight` y `juegos`).

### Errores corregidos

| Página | Problema | Corrección |
|---|---|---|
| Todas | `title` con formato `Juego · David Cabrera` | Formato `Sección \| Batman: Arkham`, distinto en cada página |
| Todas | Faltaban `description`, `keywords` y `author` | Añadidos en el `head` después del `title` |
| `index.html` | Un `h2` usado como subtítulo justo bajo el `h1` | Pasado a párrafo dentro del `div` de cabecera |
| `index.html` | Ningún `h3` | Sección «Las entregas principales» con dos `h3` |
| Todas | Contenido suelto en el `body`, sin bloques | Cada sección en un `div` con su comentario y `div` anidados |
| Todas | Sin comentario de menú ni pie de página | Comentario `NAV` al principio y pie con `&copy;`, año y nombre |
| `index.html` | Sin `hr`, cita, ficha ni entidades | Añadidos `hr`, `blockquote`, `pre` y entidades (`&amp;`, `&lt;`, `&gt;`, `&#33;`...) |

### Resumen

He reorganizado la portada sin perder nada de la 1.ª entrega (imagen, listas, enlaces y comentario con mi nombre), le he dado una jerarquía de títulos sin saltos y bloques `div` comentados, y he añadido una cita, una ficha en columnas, entidades y un pie. Después he diseñado el mapa del sitio, he aplicado la misma estructura a las cuatro páginas de juegos y he creado `juegos.html` con todos los datos de `datos.xml`.

## Mapa del sitio

| Fichero | title | Qué contiene |
|---|---|---|
| `index.html` | `Inicio \| Batman: Arkham` | Portada: presentación de la saga, listado de entregas, ficha resumen, cita y enlaces. |
| `asylum.html` | `Arkham Asylum \| Batman: Arkham` | Primer juego (2009): sinopsis, datos destacados y enlaces. |
| `city.html` | `Arkham City \| Batman: Arkham` | Segundo juego (2011): sinopsis, mundo abierto, villanos y enlaces. |
| `origins.html` | `Arkham Origins \| Batman: Arkham` | Precuela de WB Games Montreal (2013): sinopsis, diferencias y enlaces. |
| `knight.html` | `Arkham Knight \| Batman: Arkham` | Cierre de la saga (2015): sinopsis, Batmóvil, DLC y enlaces. |
| `juegos.html` | `Juegos \| Batman: Arkham` | Todos los juegos de `datos.xml` (título, estudio, año, nota, destacado y DLC), un bloque por juego. |
