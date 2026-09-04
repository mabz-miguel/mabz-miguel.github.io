# 02 — Accesibilidad y responsive

## Problemas confirmados de accesibilidad

### P0 — “Capabilities” es inaccesible por teclado

Cada cabecera es un `div.cap` con `cursor:pointer`, pero no tiene `tabindex`, rol ni control nativo (`index.html:549-585`). El JS solo registra `click` (`index.html:873-884`). Una persona que navega con teclado no puede expandir o contraer estas cuatro secciones.

**Recomendación:** convertir cada cabecera en `button`, mantener el panel fuera del botón y sincronizar `aria-expanded`, `aria-controls`, `id` y `hidden`. Soportar Enter/Espacio mediante semántica nativa.

### P1 — Acordeón de proyectos con semántica y estado incompletos

El script añade `tabindex="0"` al `.pr` completo y replica Enter/Espacio (`index.html:899-909`), pero no expone nombre/rol de botón, `aria-expanded` o relación con el panel. El listener de ratón está en `.pr-head` y el foco en `.pr`, una incongruencia de objetivo. Los paneles se ocultan visualmente con altura y overflow, no con `hidden`, así que lectores de pantalla pueden anunciar los siete casos aunque estén cerrados.

**Recomendación:** patrón de acordeón WAI-ARIA con un `h3 > button` por proyecto y un panel etiquetado. Decidir y documentar si Escape debe cerrar; no es sustituto de estado accesible.

### P1 — Menú móvil invisible pero presente en el orden de tabulación

En móvil `.nav-mobile` siempre es `display:flex`; cerrado solo aplica `opacity:0` y `pointer-events:none` (`index.html:407-413`). `pointer-events` no elimina sus cinco enlaces del teclado. El menú tampoco tiene `hidden`, `inert`, nombre de navegación ni `aria-labelledby`. No atrapa el foco, no lo mueve al abrir y no lo devuelve al botón al cerrar (`index.html:917-935`).

**Recomendación:** ocultar semánticamente el contenido cerrado (`hidden`/`inert`), asociar el botón con `aria-controls`, actualizar el nombre accesible y gestionar entrada/salida de foco. Si se comporta como overlay modal, implementar sus expectativas de diálogo; si es navegación expandible, mantener un patrón simple y no modal.

### P1 — No existe indicador de foco explícito

No hay selectores `:focus` ni `:focus-visible`. Los enlaces y el botón dependen del outline por defecto, cuya visibilidad puede ser irregular sobre superficies oscuras y con estilos de navegador.

**Recomendación:** definir un anillo de foco global de alto contraste, con offset, y verificarlo en todos los componentes y estados.

### P1 — La regla de movimiento reducido no detiene animaciones infinitas

`@media(prefers-reduced-motion:reduce)` reduce toda duración a `.01ms`, pero no cambia `animation-iteration-count` ni desactiva `scroll-behavior:smooth` (`index.html:25-26`). El marquee, pulse, blink y scroll line son infinitos; reducir la duración puede hacer que se repitan frenéticamente. `scrollIntoView({behavior:'smooth'})` tampoco consulta la preferencia (`index.html:892-894`).

**Recomendación:** desactivar animaciones decorativas y smooth scroll bajo `reduce`; mostrar logos estáticos o permitir scroll. Probar con la preferencia del sistema activa.

### P1 — Falta landmark principal y enlace de salto

La página pasa de `nav` a varias `section` y `footer`, pero no incluye `<main>` ni un “Skip to content”. Un usuario de teclado debe recorrer navegación repetida para llegar al contenido.

**Recomendación:** envolver el contenido central en `main` con destino enfocable y añadir skip link visible al foco.

### P2 — Botón de menú con nombre desactualizado

El botón conserva `aria-label="Open menu"` incluso cuando `aria-expanded="true"` (`index.html:444`, `index.html:922-928`). No tiene `aria-controls="navMobile"`. Los tres spans decorativos no están marcados individualmente, aunque no aportan texto accesible.

**Recomendación:** nombre dinámico “Open/Close menu”, `aria-controls` y SVG/icono decorativo oculto.

### P2 — Logos duplicados pueden anunciarse dos veces

Los nueve logos del carrusel se repiten con el mismo `alt` (`index.html:789`). Un lector de pantalla puede oír 18 nombres. Son prueba visual de clientes, por lo que una sola lista semántica con nombres es suficiente; la copia para animación debe quedar oculta.

### P2 — SVG decorativos sin ocultación consistente

Las flechas de proyecto tienen `aria-hidden="true"`, pero los “+” de capacidades y el icono de descarga no. Los SVG sin título suelen no aportar nombre, pero conviene aplicar `aria-hidden="true" focusable="false"` de forma uniforme.

### P2 — Anclas pueden quedar ocultas por navegación fija

La navegación es fija y las secciones no declaran `scroll-margin-top`. Al usar enlaces internos, el inicio/título de sección puede quedar bajo la barra.

### P3 — Idioma coherente pero no localizado

`lang="en"` es correcto porque el portfolio está en inglés. Si se introduce contenido español, habrá que marcar cambios de idioma o crear una versión localizada con `hreflang`.

## Semántica, headings, imágenes y contacto

**Confirmado positivo:** existe un único `h1`; las secciones About, Capabilities, Projects, Education y Contact tienen `h2`; proyectos y tarjetas de formación emplean `h3`. Las 26 imágenes tienen `alt`. Los enlaces `mailto:` y `tel:` son nativos, no hay formulario con errores de etiqueta/validación, y LinkedIn abierto en nueva pestaña incluye `rel="noopener"`.

**Matiz:** los `alt` de las siete imágenes de proyecto repiten exactamente el título. Es aceptable si la imagen identifica el caso, pero puede ser redundante junto al heading; si comunica resultados o interfaz, el texto actual no transmite esa información. El retrato tiene un alt adecuado. Los logos deben evaluarse como lista de clientes, no como decoración aislada.

## Contraste objetivo

Se calcularon ratios sRGB para tokens sólidos frente a fondos declarados:

| Color | `#030507` | `#07090d` | `#111820` | Resultado |
|---|---:|---:|---:|---|
| `--muted #6b7f91` | 4,93:1 | 4,81:1 | 4,31:1 | Falla AA de texto normal sobre `#111820`; pasa sobre los dos fondos más oscuros |
| `--dim #8ea3b4` | 7,82:1 | 7,64:1 | 6,85:1 | Pasa AA/AAA normal |
| `--wht2 #ccd8e2` | 14,08:1 | 13,75:1 | 12,33:1 | Pasa AAA |
| `--lime #38bdf8` | 9,53:1 | 9,30:1 | 8,34:1 | Pasa AAA |

Esto no valida composiciones con opacidad, filtros, gradientes, imágenes o estados hover. Los logos usan `opacity:.4`; textos muy pequeños de 0,60–0,78 rem exigen comprobación visual adicional aunque su token base pase.

## Responsive: problemas confirmados

### P1 — Reflow frágil por alturas máximas

En móvil el contenido de cada proyecto pasa a una columna, aumentando su altura, pero el panel sigue limitado a 1.300 px. Zoom al 200/400 %, fuentes mayores o texto localizado pueden recortarlo. Las capacidades comparten un límite de 200 px.

### P2 — Ocultar overflow horizontal puede esconder fallos

`body{overflow-x:hidden}` (`index.html:28`) elimina la posibilidad de acceder a contenido que desborde. La órbita de 900 px justifica contener decoración, pero debería hacerse en su componente, no globalmente.

### P2 — Breakpoints mínimos y sin estados intermedios específicos

Solo hay `1100px` y `768px`. La formación de tres columnas permanece hasta 768 px y la cabecera desktop hasta ese mismo umbral. En tablets estrechas, zoom o textos largos, estos layouts pueden quedar densos antes del salto.

### P2 — Imágenes sin dimensiones intrínsecas declaradas

Las etiquetas `img` no incluyen `width`/`height`; dependen de contenedores y estilos. Aunque varios contenedores fijan altura/min-height, declarar proporción evita inestabilidad y mejora robustez responsive.

### P3 — Tipografía extrema del hero

El desktop usa `clamp(5rem,14vw,14rem)` y móvil `clamp(2.9rem,14vw,4.9rem)`. El clamp protege extremos, pero el nombre en tres líneas, la barra fija y `min-height:100vh` deben probarse en pantallas de poca altura y con zoom.

## Validación visual/manual requerida

- Teclado completo a 320, 768, 1024 y 1440 px; foco visible, orden lógico, Escape y retorno de foco.
- VoiceOver/Safari y NVDA/Firefox: landmarks, nombres, estados de ambos acordeones y duplicación del carrusel.
- Reflow WCAG a 320 CSS px y zoom 200/400 %, incluyendo proyectos más largos.
- Preferencia de movimiento reducido real; confirmar ausencia de marquee acelerado y scroll suave.
- Contraste con captura/píxel en textos con opacidad, imágenes, filtros, hover y focus.
- Orientación landscape de móvil y viewport de baja altura; comprobar que menú y CTA siguen accesibles.
- Touch targets: medir enlaces pequeños de navegación y elementos de carrusel en dispositivos reales.
