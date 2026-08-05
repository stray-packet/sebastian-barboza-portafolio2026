# Estructura del Proyecto - sebastian-barboza-portafolio2026

## Descripción General
Este repositorio contiene el portafolio web personal de Sebastian Barboza, junto con documentación, referencias de diseño y otros recursos.

## Estructura de Carpetas

```
sebastian-barboza-portafolio2026/
├── README.md                      # Información principal del proyecto
├── .gitignore                     # Archivos a ignorar en Git
├── docs/                          # Documentación del proyecto
│   └── PROJECT_STRUCTURE.md       # Este archivo
├── portfolio/                     # Aplicación web del portafolio
│   ├── public/                    # Archivos estáticos públicos
│   │   ├── index.html             # Página principal
│   │   ├── images/                # Imágenes del portafolio
│   │   └── assets/                # Otros assets (favicons, etc)
│   ├── src/                       # Código fuente (componentes, lógica)
│   ├── styles/                    # Estilos CSS/SCSS
│   └── package.json               # Dependencias del proyecto (si aplica)
├── references/                    # Materiales de referencia
│   └── design-references/         # Referencias de diseño e inspiración
└── .claude/                       # Configuración de Claude Code
    └── settings.json
```

## Cómo Usar Cada Carpeta

### `/portfolio`
Contiene la aplicación web del portafolio.
- `public/`: Archivos que se sirven directamente (HTML, imágenes)
- `src/`: Código fuente si usas un framework (React, Vue, etc)
- `styles/`: Hoja de estilos CSS/SCSS

### `/docs`
Documentación del proyecto. Añade aquí:
- Guías de desarrollo
- Instrucciones de instalación
- Documentación de arquitectura

### `/references`
Materiales de inspiración y referencia para el diseño.
- Capturas de pantalla de referencia
- Diseños de otros portafolios
- Paletas de colores

## Próximos Pasos

1. Configurar dependencias en `portfolio/package.json`
2. Desarrollar componentes en `portfolio/src/`
3. Organizar estilos en `portfolio/styles/`
4. Documentar el proceso en `docs/`
