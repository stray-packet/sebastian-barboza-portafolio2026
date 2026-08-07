# Sebastian Barboza — Portafolio 2026

Portafolio personal de Sebastian Barboza, Product Designer enfocado en diseño de
producto y desarrollo asistido por IA.

Es un sitio estático de un solo archivo: todo el HTML, CSS y JS viven en
`portfolio/public/index.html`. No hay build step, no hay dependencias, no hay
`node_modules`.

## Ver en local

Cualquier servidor estático sirve. Por ejemplo:

```bash
npx serve portfolio/public
# o
python -m http.server 8000 --directory portfolio/public
```

Abrir el archivo con `file://` también funciona, pero conviene usar un servidor
para que las fuentes y los vídeos carguen igual que en producción.

## Deploy en Vercel

`vercel.json` ya deja configurado lo necesario:

- `outputDirectory: portfolio/public` — Vercel publica esa carpeta tal cual.
- Sin build command: es un sitio estático puro.
- Cache largo e inmutable para imágenes y fuentes; `index.html` siempre revalida.
- Headers básicos de seguridad.

Para publicar: importar el repo en Vercel y desplegar. No hace falta tocar los
ajustes del proyecto en el dashboard.

**Pendiente tras el primer deploy:** en `portfolio/public/index.html` hay un
bloque comentado en el `<head>` con `canonical` y `og:url`. Descomentarlo y poner
el dominio real para que las previsualizaciones al compartir en redes funcionen.

## Idiomas (i18n)

El sitio es bilingüe español / inglés y funciona así:

- **El HTML estático se escribe en español.** Es lo que ve alguien con JS
  desactivado, y es lo que coincide con `<html lang="es">`.
- **`I18N`** — diccionario de strings de interfaz. Cada elemento traducible lleva
  `data-i18n` (texto plano), `data-i18n-html` (contenido con markup) o
  `data-i18n-aria` (etiqueta accesible). La clave apunta a una entrada con `en` y `es`.
- **`P`** — datos de los casos de estudio, **escritos en inglés** (idioma base).
- **`PT.es`** — overrides en español de `P`, por proyecto. `fill()` hace
  `Object.assign({}, P[k], PT[LANG][k])`, así que cualquier campo ausente en el
  override cae al inglés.

### Añadir texto nuevo

1. Escribir el HTML en español.
2. Añadir `data-i18n="mi.clave"` al elemento.
3. Añadir `"mi.clave": {"t":0,"en":"...","es":"..."}` a `I18N`
   (`t:1` si el valor contiene markup y se inyecta con `data-i18n-html`).

### Añadir un proyecto nuevo

1. Añadir la entrada en `P` **en inglés**, con `custom:'<slug>'`.
2. Añadir el override español en `PT.es` — incluyendo `title` e `impact`, que no
   se heredan bien si faltan.
3. Crear `#<slug>Lead` y `#<slug>Gallery` en el HTML.
4. Añadir la tarjeta con `data-project="<slug>"`.
5. Añadir el slug a `order` para que entre en la navegación "siguiente proyecto".

Los proyectos que existen en `P` pero no tienen tarjeta ni están en `order`
quedan ocultos a propósito (hoy: `transmi` y `book`, trabajo editorial antiguo).

## Estructura

```
portfolio/public/
├── index.html                  # el sitio entero
├── assets/fonts/               # Zalando Sans SemiExpanded, Playfair Display
└── images/
    ├── about/                  # fotos de la sección "Sobre mí"
    ├── project-thumbnails/     # portadas de las tarjetas
    ├── project-mockups/        # capturas y vídeos por proyecto
    └── archive-editorial/      # assets de los dos proyectos ocultos
```
