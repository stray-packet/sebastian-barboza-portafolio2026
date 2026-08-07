# Estructura del Proyecto — sebastian-barboza-portafolio2026

## Descripción General

Portafolio web personal de Sebastian Barboza. Es un **sitio estático de un solo
archivo**: todo el HTML, CSS y JavaScript están dentro de
`portfolio/public/index.html`. No hay framework, no hay build step y no hay
dependencias de npm.

## Estructura de Carpetas

```
sebastian-barboza-portafolio2026/
├── README.md                       # Cómo correrlo, desplegarlo y editar i18n
├── vercel.json                     # Configuración de deploy (output dir, cache, headers)
├── .gitignore
├── CV.md                           # Privado, ignorado por Git
├── docs/
│   └── PROJECT_STRUCTURE.md        # Este archivo
├── portfolio/
│   └── public/                     # Todo lo que se publica en Vercel
│       ├── index.html              # El sitio completo (HTML + CSS + JS)
│       ├── assets/
│       │   └── fonts/              # ZalandoSansSemiExpanded, PlayfairDisplay-Italic
│       └── images/
│           ├── favicon-portafolio.png
│           ├── about/              # Fotos de la sección "Sobre mí"
│           ├── project-thumbnails/ # Portadas de las tarjetas de proyecto
│           ├── project-mockups/    # Capturas y vídeos, una carpeta por proyecto
│           └── archive-editorial/  # Assets de los dos proyectos ocultos
└── references/
    └── fonts/                      # Fuentes originales (.ttf) antes de convertir
```

## Los proyectos

Seis proyectos visibles, cada uno con su tarjeta en la sección Trabajo:

| Slug         | Título                | Contexto                          |
| ------------ | --------------------- | --------------------------------- |
| `coply`      | Coply Manager         | SaaS propio, cliente real pagando |
| `tyc`        | De 2 días a 2 horas   | Olimpo.bet — automatización legal |
| `gamestudio` | Olimpo Game Studio    | Olimpo.bet — marketing gamificado |
| `leon`       | León Security         | Landing Figma → Claude Code       |
| `kambi`      | Kambi Knowledge Base  | Olimpo.bet — crawler de docs      |
| `modulos`    | Módulos Olimpo.bet    | Olimpo.bet — web y mobile         |

Además hay tres entradas que **existen en los datos pero están ocultas** (no
tienen tarjeta ni aparecen en `order`):

- `uxwriter` — Olimpo UX Writer (tiene contenido, le faltan capturas reales)
- `transmi` — fanzine sobre TransMilenio (trabajo editorial antiguo)
- `book` — "Desde que llegaste" (tesis de grado)

Se dejan a propósito: el contenido está listo, solo no se muestran.

## Cómo se organiza `index.html`

De arriba abajo:

1. `<head>` — meta tags, Open Graph, favicon
2. `<style>` — todo el CSS, con variables de tema en `:root`
3. Markup de las secciones — hero, trabajo, sobre mí, servicios, contacto
4. Markup del modal de caso de estudio — bloques `#<slug>Lead` y `#<slug>Gallery`
5. `<script>` — animaciones, apertura de casos, y al final el bloque i18n
   (`I18N`, `ROT`, `P`, `PT`, `applyI18n()`, `setLang()`)

## Convenciones

- **El HTML estático se escribe en español**, que es lo que declara `<html lang="es">`.
- **Los datos de proyectos (`P`) se escriben en inglés**; el español va en `PT.es`.
- Los slugs de proyecto describen el proyecto real (`coply`, `leon`, `kambi`…).
  No usar nombres genéricos ni heredados de plantillas.
- Las imágenes van en `project-mockups/<slug-legible>/`.

Los detalles de cómo añadir strings o proyectos nuevos están en el
[README](../README.md).
