# Batman: Arkham

- **Nombre:** David Cabrera González
- **Usuario de GitHub:** IZialexI
- **Tema elegido:** la saga de videojuegos Batman: Arkham

## Por qué he elegido este tema

Tenía que ser una web tematizada, así que pensé en una de las sagas de videojuegos que más me gustan, habría otras, pero conociéndome, me extendería demasiado

## Qué he hecho en esta entrega

- **1.ª entrega:** una web estática (aún sin CSS) y un .xml con algunos datos referentes a los juegos.
- **UD3:** estructura HTML completa en todas las páginas, mapa del sitio y una página nueva (`juegos.html`) con los datos del XML.
- **UD5:** una tabla de datos de la saga en `juegos.html` y una página nueva (`contacto.html`) con un formulario para apuntarse al club de fans.

## Palabra del día

- **1.ª entrega:** anticristo
- **UD3:** contexto
- **UD5:** día

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

## UD5 · Tablas y formularios

La tabla irá en `juegos.html` y recogerá los juegos de la saga agrupados por estudio, con su año de lanzamiento, el tipo de entrega y la nota de la crítica (más la nota media en el pie). El formulario estará en una página nueva, `contacto.html`, para que los fans se apunten al club de la web y nos cuenten su juego favorito, sus villanos preferidos y su opinión sobre la saga.

### Por qué `post` y no `get`

Uso `method="post"` porque el formulario envía datos personales (nombre, correo y teléfono) y un mensaje largo: con `post` viajan en el cuerpo de la petición y no quedan a la vista en la URL, en el historial ni en los marcadores, y no hay límite práctico de longitud.

### Prueba con `get`

Cambiando temporalmente a `method="get"`, rellenando el formulario y pulsando «Enviar inscripción», la barra del navegador mostró:

```
file:///mnt/Data/zialex/DAM/LenguajesDeMarcas/proyecto/contacto.html?nombre=Caballero+Oscuro&email=fan%40ejemplo.com&telefono=600+123+456&plataforma=pc&juego=city&villanos=joker&villanos=enigma&mensaje=%C2%A1Arkham+City+es+el+mejor+juego+de+la+saga%21&enviar=Enviar+inscripci%C3%B3n#
```

Se ve cada `name=value` separado por `&`, los espacios como `+`, los caracteres especiales codificados (`@` → `%40`, `¡` → `%C2%A1`, `ó` → `%C3%B3`) y el `name="villanos"` repetido una vez por cada casilla marcada. Después volví a dejar `method="post"`.

### Validación W3C

| Página | Errores | Avisos | Corrección |
|---|---|---|---|
| `juegos.html` | 0 | 0 | No hizo falta ninguna |
| `contacto.html` | 0 | 0 | No hizo falta ninguna |
| `index.html` (nuevo enlace) | 0 | 0 | No hizo falta ninguna |

El validador (validator.w3.org) no dio ningún error ni aviso, así que no hubo commits `fix(...)` en esta unidad.

### Resumen

En `juegos.html` he añadido una tabla de datos con `caption`, `colgroup`, `thead`, `tbody` y `tfoot`: cinco juegos agrupados por estudio, con un `rowspan` para las cuatro filas de Rocksteady Studios, un `colspan` en la cabecera «Lanzamiento» (que agrupa año y tipo) y otro en el pie con la nota media, y cabeceras `th` con `scope="col"`, `scope="colgroup"` y `scope="row"`. Después he creado `contacto.html` con la misma estructura que el resto de páginas y un formulario `post` con dos `fieldset` («Tus datos» y «Tu opinión sobre la saga»): campos de texto, correo y teléfono, un grupo de `radio` para la plataforma, un `select` con el juego favorito, `checkbox` para los villanos, un `textarea` y los botones de enviar y borrar, todos con su `label for`, `name` e `id` únicos, y los atributos `required`, `maxlength`/`minlength`, `placeholder`, `autofocus`, `selected` y `checked`. Por último he enlazado la página desde la portada, la he añadido al mapa del sitio y he pasado las páginas por el validador del W3C.

## Mapa del sitio

| Fichero | title | Qué contiene |
|---|---|---|
| `index.html` | `Inicio \| Batman: Arkham` | Portada: presentación de la saga, listado de entregas, ficha resumen, cita y enlaces. |
| `asylum.html` | `Arkham Asylum \| Batman: Arkham` | Primer juego (2009): sinopsis, datos destacados y enlaces. |
| `city.html` | `Arkham City \| Batman: Arkham` | Segundo juego (2011): sinopsis, mundo abierto, villanos y enlaces. |
| `origins.html` | `Arkham Origins \| Batman: Arkham` | Precuela de WB Games Montreal (2013): sinopsis, diferencias y enlaces. |
| `knight.html` | `Arkham Knight \| Batman: Arkham` | Cierre de la saga (2015): sinopsis, Batmóvil, DLC y enlaces. |
| `juegos.html` | `Juegos \| Batman: Arkham` | Todos los juegos de `datos.xml` (título, estudio, año, nota, destacado y DLC), un bloque por juego, y una tabla de la saga por estudio. |
| `contacto.html` | `Contacto \| Batman: Arkham` | Formulario para apuntarse al club de fans: datos personales, plataforma, juego favorito, villanos preferidos y mensaje. |
