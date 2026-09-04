# Auditoría técnica independiente — Portfolio 2026

Fecha de revisión: 4 de septiembre de 2026

Rama revisada: `codex/career-audit-2026`

Objeto técnico: `index.html` en la raíz del repositorio

## Alcance e independencia

Esta revisión cubre calidad y mantenibilidad del código, accesibilidad, responsive, rendimiento, SEO técnico, robustez y estrategia de pruebas. Se realizó leyendo únicamente `career-audit-2026/00_CONTEXT.md` y el archivo de producción `index.html`. No se leyó `career-audit-2026/CLAUDE_MASTER_PROMPT.md` ni ningún contenido de `career-audit-2026/chatgpt/` o `career-audit-2026/claude/`.

No se modificó ningún archivo de producción. Estos documentos son exclusivamente de análisis y recomendaciones.

## Resumen ejecutivo

El portfolio funciona como una página estática autocontenida y su JavaScript inline tiene sintaxis válida. La estructura visual es coherente y existen bases positivas: `lang`, viewport, un único `h1`, títulos de sección, textos alternativos, `rel="noopener"`, una regla de movimiento reducido y enlaces de contacto nativos.

Sin embargo, la implementación presenta cuatro problemas prioritarios:

1. **P0 — Las capacidades no son operables por teclado.** Son `div` con listener de clic, sin botón, foco, estado ni relación ARIA (`index.html:549-585`, `index.html:873-884`). Una parte relevante del contenido queda inaccesible para usuarios de teclado.
2. **P1 — Los dos acordeones no exponen correctamente su estado.** Los proyectos simulan interacción mediante `div` y `tabindex`, pero carecen de `button`, `aria-expanded`, `aria-controls` y regiones asociadas; el contenido colapsado sigue en el árbol de accesibilidad (`index.html:599-784`, `index.html:887-914`).
3. **P1 — El menú móvil cerrado contiene enlaces invisibles enfocables.** Se oculta solo con opacidad y `pointer-events`; no usa `hidden`/`inert`, no gestiona foco ni actúa como diálogo (`index.html:407-426`, `index.html:449-456`, `index.html:917-935`).
4. **P1 — La entrega y las previews están degradadas.** El HTML pesa 611.948 bytes, contiene 27 recursos `data:` (412.191 bytes binarios decodificados), ninguna de sus 26 imágenes usa carga diferida y el `og:image` apunta a un host que no resolvió DNS durante la comprobación. Además, Google Fonts no sirve la familia solicitada `Clash Display`, así que los titulares usan fallback.

No se han identificado hallazgos P0 de ejecución general, pérdida de datos o seguridad. El único P0 es la barrera confirmada de acceso por teclado a contenido principal.

## Mapa de entregables

- [01_CODE_QUALITY_AUDIT.md](01_CODE_QUALITY_AUDIT.md): estructura, CSS, JavaScript, duplicación y mantenibilidad.
- [02_ACCESSIBILITY_RESPONSIVE_AUDIT.md](02_ACCESSIBILITY_RESPONSIVE_AUDIT.md): semántica, teclado, ARIA, foco, contraste, movimiento y layouts.
- [03_PERFORMANCE_SEO_AUDIT.md](03_PERFORMANCE_SEO_AUDIT.md): peso, recursos, fuentes, Core Web Vitals, metadatos e indexabilidad.
- [04_TECHNICAL_RISKS_AND_TESTING.md](04_TECHNICAL_RISKS_AND_TESTING.md): robustez, enlaces, degradación sin JS, seguridad básica y propuesta de CI.

## Convención de evidencia y prioridad

- **Confirmado:** deriva directamente del código, de una comprobación local reproducible o de una petición de red ejecutada.
- **Riesgo probable:** consecuencia técnicamente plausible que requiere un navegador, dispositivo, hosting o datos de campo para confirmarse.
- **Recomendación:** acción propuesta; no implementada.
- **Validación manual:** comprobación visual o asistiva pendiente.

Prioridades: **P0** perjuicio serio; **P1** importante; **P2** mejora recomendable; **P3** refinamiento.

## Comprobaciones realizadas

- Inventario de archivos permitido y estado de Git.
- Tamaño y líneas con `wc`: 611.948 bytes y 942 líneas para `index.html`.
- Inventario por patrones de elementos, enlaces, ARIA, CSS y JavaScript con `rg`.
- Parseo de los `data:` mediante Node: 27 recursos y 412.191 bytes decodificados; 26 etiquetas `img`; cero atributos `loading`.
- Compilación del JavaScript inline con `new Function`: sintaxis correcta.
- Cálculo WCAG de colores sólidos declarados frente a los fondos usados.
- `tidy -errors -quiet`: ejecutado, pero sus avisos de codificación sobre líneas con `data:` no son evidencia fiable debido a su parser/compatibilidad; sí señaló los ampersands sin escapar del URL de Google Fonts.
- Petición de red al `og:image`: `curl` no pudo resolver `mabz.miguel.com`.
- Petición de red a Google Fonts: HTTP 200; la respuesta contenía cuatro variantes de `DM Sans` y ninguna declaración de `Clash Display`.

No se ejecutaron Lighthouse, axe, lector de pantalla, matriz real de navegadores, regresión visual ni pruebas de hosting porque el repositorio no incluye infraestructura de pruebas o servidor y no se instalaron dependencias. Sus conclusiones quedan identificadas como pendientes, no como resultados.
