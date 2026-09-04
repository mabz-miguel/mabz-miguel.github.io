# 03 — Performance y SEO técnico

## Performance: mediciones confirmadas

| Métrica estática | Resultado |
|---|---:|
| `index.html` | 611.948 bytes; 942 líneas |
| Recursos `data:` | 27 |
| Binario decodificado total de `data:` | 412.191 bytes |
| Imágenes `<img>` | 26 |
| Imágenes con `loading` | 0 |
| PDF embebido | 67.737 bytes decodificados |
| Retrato | 77.469 bytes decodificados |
| Siete imágenes de proyecto | 233.325 bytes decodificados |
| Logos, incluidas copias | 33.660 bytes decodificados |

Las cifras Base64 no incluyen el SVG de ruido percent-encoded en CSS. El tamaño de transferencia real dependerá de compresión HTTP, pero el navegador debe recibir y parsear el documento completo antes de disponer de todos estos recursos.

## Hallazgos de performance

### P1 — Todos los assets invalidan y bloquean junto con el HTML

Al estar embebidos, retrato, proyectos, logos y CV no tienen caché independiente, priorización por URL ni descarga diferida. Un cambio textual invalida todo. El Base64 incrementa el tamaño previo a compresión y crea líneas muy costosas para tooling.

**Recomendación:** servir assets separados con compresión y cache inmutable; mantener en línea solo un recurso crítico muy pequeño si una medición demuestra beneficio.

### P1 — Imágenes fuera de pantalla cargadas de forma eager

Ninguna imagen tiene `loading="lazy"` ni `decoding="async"`. Las siete imágenes de proyectos están incluso dentro de paneles cerrados, pero el Base64 ya forma parte del documento; los 18 logos duplicados también llegan siempre.

**Recomendación:** extraer, usar lazy loading para contenido bajo el fold, conservar eager/fetch priority solo para un LCP real, y evitar duplicar bytes para el marquee.

### P1 — `Clash Display` no se sirve

El CSS solicita `Clash Display` y `DM Sans` en Google Fonts (`index.html:15`). La respuesta comprobada el 4-09-2026 fue HTTP 200, pero contenía únicamente cuatro `@font-face` de `DM Sans`; no incluyó `Clash Display`. Todos los titulares con `font-family:'Clash Display',sans-serif` renderizan fallback. Esto altera métricas, jerarquía e identidad visual.

**Recomendación:** alojar una fuente con licencia adecuada o elegir una familia realmente disponible, definir fallback métrico y subconjuntos/formatos WOFF2. Verificar en Network y computed styles.

### P2 — Fuente remota render-blocking y múltiples ficheros

La hoja externa está en `<head>` y solicita cuatro variantes TTF de DM Sans. `display=swap` reduce texto invisible y los preconnect ayudan, pero aún hay dependencia externa, latencia y potencial CLS al intercambiar fuente.

### P2 — Animaciones permanentes y efectos de composición

Marquee, pulse, blink, scroll line, `position:fixed` con ruido, `backdrop-filter:blur(28px)` y varias transiciones pueden consumir CPU/GPU. El riesgo crece en móviles de gama baja; la regla reduced-motion actual no lo mitiga correctamente.

### P2 — Ausencia de dimensiones explícitas

Las 26 imágenes carecen de atributos `width` y `height`. Los contenedores reducen parte del riesgo, pero el navegador no recibe siempre una proporción intrínseca declarada de forma temprana.

### P3 — CSS y JS inline no cacheables por separado

Son pequeños frente a los assets, pero cualquier cambio obliga a volver a transferir todo y una CSP estricta exigiría hashes/nonces.

## Riesgos de Core Web Vitals

- **LCP, P1 probable:** TTF remotas, documento grande y decodificación del retrato pueden retrasar el elemento principal. El candidato LCP exacto requiere Lighthouse/CrUX.
- **CLS, P2 probable:** intercambio de `DM Sans` y fallback inesperado de `Clash Display`; imágenes sin dimensiones. Los contenedores definidos pueden limitar el desplazamiento.
- **INP, P2 probable:** JS es pequeño, pero efectos de composición, `scrollIntoView` suave y observers deben perfilarse en hardware lento. No hay evidencia de long tasks en análisis estático.

## SEO técnico: problemas confirmados

### P1 — Preview social rota

`og:image` apunta a `https://mabz.miguel.com/og-image.jpg` (`index.html:11`). Una petición con `curl` no pudo resolver el host DNS el 4-09-2026. Por tanto, los crawlers no pueden obtener esa imagen en el estado comprobado.

**Recomendación:** publicar una imagen absoluta estable (idealmente 1200×630, MIME y peso adecuados) y validarla con los depuradores de LinkedIn/Facebook/X tras despliegue.

### P1 — No hay canonical ni URL social

No existen `<link rel="canonical">` ni `og:url`. Sin URL pública canónica verificable en el repositorio, variantes de hosting/ruta pueden competir o compartir con URL incorrecta.

### P1 — No hay `robots.txt` ni sitemap en el repositorio

El inventario permitido solo contiene `index.html` como producción; no existen `robots.txt` o `sitemap.xml`. Esto no bloquea por sí solo la indexación de una página enlazada, pero elimina señales explícitas de descubrimiento y canonicalización.

### P2 — Twitter Card incompleta

Solo aparece `twitter:card=summary_large_image` (`index.html:12`). Faltan `twitter:title`, `twitter:description` y `twitter:image`; algunos crawlers pueden recurrir a OpenGraph, pero la imagen OG está rota.

### P2 — No hay datos estructurados

No existe JSON-LD. Un `Person` con nombre, URL, cargo/área profesional, `sameAs` y datos verificables ayudaría a resolver entidad; debe evitar afirmaciones no demostrables.

### P2 — Sin iconos ni manifest

No se declaran favicon, `apple-touch-icon` o manifest. Afecta reconocimiento de pestaña/marcador y acabado técnico, más que ranking directo.

### P3 — Ampersands sin escapar en atributo HTML

El `href` de Google Fonts incluye `&family` y `&display` en vez de `&amp;` (`index.html:15`). Los navegadores lo toleran, pero un validador HTML lo advierte y debe corregirse en fuente.

## SEO técnico: aspectos positivos

- `<!DOCTYPE html>`, `<html lang="en">`, UTF-8 y viewport están presentes.
- Title descriptivo de 68 caracteres aproximados y meta description específica de 154 caracteres aproximados.
- OpenGraph incluye title, description y type.
- Un único `h1` con nombre completo y jerarquía `h2`/`h3` coherente.
- No hay `noindex`, canonical contradictorio, enlaces hash rotos internos ni contenido generado exclusivamente por JS.
- Los datos de contacto son enlaces rastreables y LinkedIn usa URL HTTPS.

## Validación pendiente

- Lighthouse móvil/desktop sobre la URL desplegada, tres ejecuciones y mediana.
- PageSpeed Insights y CrUX si existe tráfico suficiente.
- Respuesta HTTP real: status, compresión Brotli/Gzip, caché, CSP, HSTS, `X-Content-Type-Options`, redirects y canonical final.
- Google Rich Results, Search Console URL Inspection, sitemap y robots desplegados (podrían existir fuera del worktree).
- LinkedIn Post Inspector, Facebook Sharing Debugger y X Card Validator tras reparar OG.
- Verificar tamaño renderizado/dimensiones naturales de cada imagen y convertir según transparencia/fotografía (AVIF/WebP/SVG).
