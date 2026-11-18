# Videos de los casos

Los ocho casos visibles, salvo Módulos Olimpo.bet, muestran un demo debajo de rol, año, categoría y cliente. El reproductor usa controles nativos, carga el MP4 cuando se solicita y muestra antes una portada cuadrada centrada sobre negro.

| Caso | Video publicado | Miniatura publicada | Fuente original |
| --- | --- | --- | --- |
| Coply Manager | `coply-final.mp4` | `coply.webp` | `coply-manager.mp4` |
| De 2 días a 2 horas | `tyc-final.mp4` | `tyc.webp` | `pipeline-terminos.mp4` |
| Olimpo Game Studio | `gamestudio-final.mp4` | `gamestudio.webp` | `olimpo-gamestudio.mp4` |
| León Security | `leon-final.mp4` | `leon.webp` | `leon-security.mp4` |
| Descubre Olimpo | `descubre-final.mp4` | `descubre.webp` | `descubre-olimpo.mp4` |
| Agente de iconos | `iconos-final.mp4` | `iconos.webp` | `olimpo-icon-agents.mp4` |
| Agente de UX writing | `uxagent-final.mp4` | `uxagent.webp` | `olimpo-ux-writer.mp4` |
| Kambi Knowledge Base | `kambi-final.mp4` | `kambi.webp` | `kambi-knowledge-base.mp4` |

Los MP4 publicados están en `portfolio/public/videos/demos/` y las miniaturas optimizadas en `portfolio/public/images/video-posters/`. `DEMO_MEDIA` en `portfolio/public/index.html` conecta cada slug con esos nombres. Las portadas fuente permanecen en el proyecto del demo reel.

Los ocho MP4 fuente proceden de `stray-content-creation/videos/octubre-2026/demo-reel-proyectos-ia/exports/portafolio-ocho-videos-finales/` (01-11-2026). Son cortes preparados para el portafolio, sin apertura ni retorno al mosaico del tráiler. GameStudio no incluye audio en el fuente; los otros siete conservan su pista.

Las copias H.264 optimizadas suman 66,1 MB frente a unos 135,7 MB de las ocho exportaciones fuente. El README de la carpeta fuente marca estos cortes como pendientes de revisión editorial de Sebastián; la integración técnica no cambia ese estado.

Las ocho miniaturas WebP suman unos 885 KB; las copias PNG/JPG publicadas antes sumaban unos 10 MB. Se conservó el tamaño y el encuadre cuadrado de cada portada.

## Actualizar un demo

1. Exportar el video final a MP4 H.264, 1920 × 1080 y audio AAC si corresponde.
2. Optimizarlo con FFmpeg: `ffmpeg -i entrada.mp4 -c:v libx264 -preset medium -crf 22 -pix_fmt yuv420p -c:a aac -b:a 128k -movflags +faststart salida.mp4`.
3. Reemplazar el MP4 publicado del caso conservando su nombre. Cambiar el nombre en `DEMO_MEDIA` solo si se desea versionar la URL.
4. Si cambia la miniatura, exportar una copia WebP con un nombre nuevo (por ejemplo, `coply-v2.webp`) y actualizar `DEMO_MEDIA`. Vercel configura las imágenes como inmutables durante un año en el navegador; reemplazar una portada con el mismo nombre podría mostrar la versión anterior a visitantes recurrentes.

Los archivos fuente permanecen en el proyecto del demo reel. Ningún video anterior de las galerías del portafolio fue sustituido.

Se usan archivos locales para mantener control sobre las revisiones y evitar dependencias del reproductor de YouTube. La carga diferida evita descargar los demos mientras se navega por la página.

Antes de publicar, comprobar en la URL final que una solicitud `Range: bytes=0-1023` a un MP4 responda `206 Partial Content` con `Content-Range`, y probar reproducción y avance en un navegador móvil. El servidor simple de Python usado en local responde `200` y entrega el archivo completo; no representa la entrega de video de Vercel.
