# 04 — Riesgos técnicos, robustez y testing

## Robustez: problemas confirmados

### P1 — Degradación sin JavaScript incompleta

Sin JS, la tercera capacidad aparece abierta porque `cap-on` está en HTML, pero las demás no pueden abrirse. Todos los proyectos permanecen visualmente cerrados porque `pr-active` solo lo añade JS. El contenido existe en el DOM y puede ser extraído por lectores/crawlers, pero una persona visual sin JS no puede acceder a la mayor parte del detalle.

**Recomendación:** progressive enhancement con `details/summary` o HTML inicialmente legible que JS convierta en acordeón; probar con scripts bloqueados y con fallo temprano.

### P1 — Uso de APIs sin guardas

Los dos primeros bloques construyen `IntersectionObserver` sin comprobar soporte (`index.html:847-869`). Un navegador/webview incompatible lanzaría al inicio del script. Las IIFE posteriores seguirían ejecutándose normalmente porque cada bloque es una sentencia posterior, pero el fallo queda en consola y se pierde la mejora observada.

**Recomendación:** feature detection y fallback que deje todo visible/usable. La clase `.sr` ya es visible por defecto, lo cual es una buena base.

### P1 — Dependencia externa visual rota parcialmente

Google Fonts responde, pero omite `Clash Display`. La web sigue funcionando por `sans-serif`, aunque el resultado no coincide con el diseño previsto. Si Google Fonts falla por red, CSP o bloqueo de privacidad, también cae `DM Sans`.

### P1 — URL OpenGraph no resoluble

El único asset social remoto comprobado no resuelve DNS. No afecta la página visible, pero sí la candidatura cuando el enlace se comparte.

### P2 — Estados edge-case de menú

El menú se activa solo por media query. Si se abre en móvil y el viewport cambia a desktop, las clases y `body.style.overflow='hidden'` permanecen; CSS oculta el overlay, pero el body puede seguir sin scroll hasta volver a accionar/cargar. Tampoco se cierra explícitamente en `resize` ni al perder contexto.

### P2 — Alturas fijas pueden truncar cambios futuros

Los límites 200/1300 px hacen que un caso más largo, una traducción o zoom sea un estado no soportado. No se detecta automáticamente el overflow truncado.

### P2 — El CV como `data:` reduce interoperabilidad

El enlace `download` a PDF embebido suele funcionar en navegadores modernos, pero no aporta URL compartible/indexable, caché independiente ni fallback. Políticas CSP que prohíban `data:` o ciertos webviews pueden impedirlo.

### P2 — No existe manejo explícito de foco al mutar UI

Al cerrar un proyecto con Escape el foco queda en el contenedor, razonable; al cerrar menú por enlace/Escape no se devuelve al disparador. No hay bloqueo de interacción con el fondo del overlay.

### P3 — Navegación activa puede oscilar

Cada entrada intersectada actualiza todos los links con threshold 0,4 (`index.html:860-869`). Dos secciones pueden cruzar el umbral durante el mismo callback y gana el orden de entradas, no una regla de “sección más visible”. `hero`, `clients` y `contact` tampoco tienen link equivalente en la lista desktop, dejando potencialmente ninguno activo.

## Enlaces y rutas

**Confirmado localmente:** todos los hashes usados (`hero`, `about`, `capabilities`, `projects`, `formation`, `contact`) tienen un ID correspondiente. No hay rutas relativas a assets que puedan producir 404 porque los assets visibles y el PDF están embebidos. `mailto:` y `tel:` son sintácticamente plausibles. Los enlaces externos incluyen únicamente LinkedIn, Google Fonts y el OG image.

**Confirmado por red:** el OG image no resuelve DNS; Google Fonts responde HTTP 200 y sirve DM Sans, no Clash Display.

**No confirmado:** disponibilidad de LinkedIn, entrega de email/teléfono, URL pública final, redirects y recursos que pueda añadir el hosting. Deben probarse desde la URL desplegada; LinkedIn puede bloquear clientes automatizados sin que eso implique enlace roto para una persona.

## Seguridad y privacidad frontend

### P2 — CSP estricta será difícil con inline y `data:`

CSS, JS, estilos inline, imágenes/PDF `data:` y fuentes Google obligan a una política permisiva, hashes/nonces numerosos o refactor. El repositorio no contiene configuración de cabeceras para confirmar la política desplegada.

### P2 — Google Fonts es una dependencia de tercero

Supone una petición externa y disponibilidad ajena. Deben evaluarse requisitos de privacidad/consentimiento aplicables y valorar self-hosting con licencia.

### P3 — Superficie de XSS actualmente baja

No hay inputs, `innerHTML`, parámetros URL procesados, eval dinámico, dependencias JS ni contenido remoto insertado. `new Function` solo se usó como comprobación local de auditoría, no existe en producción. Los enlaces con `target="_blank"` incluyen `rel="noopener"`.

## Plan de pruebas automatizadas antes de publicar

### Gate mínimo por pull request

1. **HTML — P1:** Nu HTML Checker (`vnu.jar`) sobre el artefacto final. Fallar ante IDs duplicados, atributos inválidos, nesting erróneo y ampersands sin escapar.
2. **Accesibilidad — P0:** Playwright + axe-core en 375×812, 768×1024 y 1440×900. Cero violaciones critical/serious; incluir estado inicial y cada acordeón/menú abierto.
3. **Teclado — P0:** pruebas Playwright que recorran Tab, activen Capabilities y Projects con Enter/Espacio, cierren con Escape, verifiquen `aria-expanded`, `hidden`, foco visible y retorno del foco del menú.
4. **JavaScript — P1:** ESLint y test de consola sin errores. Ejecutar caso con `IntersectionObserver` ausente y caso sin JS.
5. **Enlaces — P1:** link checker sobre URL desplegada, hashes, LinkedIn, OG image, canonical, sitemap y assets. Permitir reglas específicas para anti-bot sin silenciar fallos DNS/404.
6. **Responsive — P1:** assertions de ausencia de overflow horizontal y contenido recortado a 320, 375, 768, 1024 y 1440 px; repetir con zoom/text scaling.
7. **Performance — P1:** Lighthouse CI móvil con presupuestos iniciales: HTML comprimido y total transferido definidos tras baseline, LCP ≤2,5 s, CLS ≤0,1 e INP/TBT proxy bajo umbral. Registrar mediana para evitar ruido.
8. **Regresión visual — P2:** screenshots de hero, About, cada tipo de acordeón, menú abierto y Contact en móvil/tablet/desktop, con fuentes cargadas y fallback simulado.

### Casos funcionales concretos

- Solo una capacidad/proyecto abierto a la vez; segundo accionamiento cierra.
- Escape no cambia componentes no relacionados.
- Abrir menú, tabular dentro, cerrar por Escape/enlace y recuperar foco; resize abierto no bloquea scroll desktop.
- Hash directo a cada sección no queda bajo la navegación fija.
- Descarga del CV devuelve un PDF válido con nombre correcto.
- `prefers-reduced-motion: reduce` elimina marquee, parpadeo y desplazamiento suave.
- Fuentes bloqueadas: contenido legible, sin solapamiento ni salto grave.
- Imágenes bloqueadas: alt útil, layout estable, CTA y casos siguen comprensibles.
- Texto al 200 % y viewport equivalente a 320 CSS px: no hay pérdida de contenido ni scroll bidimensional.

### Pruebas periódicas o de despliegue

- Lighthouse/PSI contra producción y alerta de regresión de peso.
- Validadores OG/Twitter/LinkedIn y comprobación HTTP de imagen social.
- Search Console: indexación, canonical seleccionada, sitemap y rich results.
- Matriz BrowserStack/Sauce o dispositivos reales: Safari iOS, Chrome Android, Safari macOS, Chrome/Firefox/Edge desktop.
- Auditoría manual trimestral con VoiceOver y NVDA; axe no sustituye semántica, orden, nombres comprensibles ni experiencia real.

## Qué se comprobó y qué sigue siendo hipótesis

### Comprobado en esta auditoría

- Rama y worktree correctos; inventario permitido de producción.
- Sintaxis del JS inline correcta.
- IDs de hashes locales existentes.
- Ausencia de `loading`, canonical, datos estructurados, robots/sitemap y estilos de foco.
- Elementos/atributos exactos de interacciones y comportamiento derivable del código.
- Tamaños de HTML y recursos embebidos.
- Ratios de contraste de tokens sólidos.
- DNS fallido del OG image y respuesta parcial de familias en Google Fonts.

### Requiere validación; no debe presentarse como resultado medido

- LCP, CLS, INP, TBT y puntuación Lighthouse.
- Recorte/overflow efectivo en cada dispositivo, zoom y fuente.
- Contraste compuesto sobre imágenes/opacidades.
- Anuncio exacto en cada combinación lector de pantalla/navegador.
- Cabeceras, compresión, caché, CSP, robots o sitemap añadidos por hosting.
- Indexación real y apariencia de previews después de publicación.

## Orden recomendado de resolución futura

1. **P0/P1 accesibilidad:** controles nativos, ARIA/hidden, menú y foco, reduced motion.
2. **P1 distribución:** extraer assets, lazy loading, dimensiones, fuente real y OG image.
3. **P1 robustez/SEO:** progressive enhancement, guardas, canonical, social metadata, robots/sitemap según URL final.
4. **P1 CI:** HTML, axe, teclado, enlaces, responsive y Lighthouse budgets.
5. **P2/P3 mantenimiento:** limpiar CSS muerto, deduplicar componentes/datos y endurecer CSP.
