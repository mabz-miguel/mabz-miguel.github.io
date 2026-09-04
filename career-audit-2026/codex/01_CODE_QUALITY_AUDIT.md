# 01 — Calidad del código y mantenibilidad

## Diagnóstico

El producto es una única página estática con una dependencia remota de fuentes. Esa simplicidad reduce superficie de despliegue, pero el archivo monolítico mezcla contenido, presentación, imágenes, logos, CV e interacción. Con 611.948 bytes y líneas extremadamente largas por Base64, una modificación editorial sencilla puede producir diffs difíciles de revisar, conflictos y regresiones no localizadas.

## Problemas confirmados

### P1 — Documento monolítico y binarios dentro del HTML

`index.html` reúne 433 líneas aproximadas de CSS, todo el markup, 95 líneas aproximadas de JS y 27 recursos embebidos. Los `data:` representan 412.191 bytes binarios decodificados; su codificación Base64 añade alrededor de un tercio de sobrecoste sobre el binario. Incluyen retrato, siete imágenes de proyectos, dos copias del conjunto de nueve logos y un PDF.

Impacto: revisión y cacheo deficientes, imposibilidad de actualizar un asset sin invalidar todo el documento, ausencia de optimización por recurso y alto coste de merge. La línea del carrusel (`index.html:789`) y la del CV (`index.html:835`) son especialmente inmanejables.

**Recomendación:** extraer CSS, JS, imágenes y PDF a ficheros versionados; usar nombres con hash para cache largo. Dividir el HTML por componentes solo si existe un build estático que mantenga una salida simple.

### P1 — Controles construidos sobre elementos no interactivos

Las capacidades son `.cap` sobre `div` (`index.html:549-585`) y el listener solo escucha `click` (`index.html:873-884`). Los proyectos son `.pr`/`.pr-head` sobre `div`; el foco se añade al contenedor exterior después de cargar (`index.html:899-909`) mientras el clic se registra en el hijo. Esta semántica artesanal exige recrear comportamiento que ya ofrece un `button`.

**Recomendación:** usar botones reales como cabeceras del acordeón y paneles con identificadores estables; centralizar la lógica en un componente reutilizable.

### P2 — Duplicación de contenido y de patrones

- Los nueve logos están duplicados para el marquee, por lo que se envían dos veces en Base64 (`index.html:789`).
- Navegación desktop y móvil duplican manualmente los mismos destinos (`index.html:437-445`, `index.html:449-456`).
- Capacidades y siete proyectos repiten estructuras extensas sin fuente de datos común.
- Dos `IntersectionObserver` tienen callbacks idénticos y solo cambia el umbral (`index.html:847-857`).
- Los estilos y scripts de ambos acordeones implementan conceptos equivalentes por separado.

Impacto: deriva entre copias, errores al añadir una sección y coste de mantenimiento.

**Recomendación:** generar listas repetitivas desde datos en build time y compartir pequeñas utilidades de interacción, sin convertir necesariamente el portfolio en una SPA.

### P2 — CSS residual e incoherencias nominales

Existen selectores aparentemente huérfanos de una versión previa: `.proj-wrap.dr-open .proj-list`, `.dr-wrap`, `.dr-grid` y `.dr-inner` (`index.html:352-354`, `index.html:373-380`). `.about-photo-ph` tampoco tiene instancia en el markup actual (`index.html:132-133`). El nombre `--lime` contiene azul `#38bdf8`, y el comentario “impact moved to About” permanece como rastro de refactor.

**Recomendación:** eliminar selectores muertos tras comprobar cobertura, renombrar tokens por función (`--accent`, `--surface`) y activar lint de CSS.

### P2 — Estado inicial dividido entre HTML y JavaScript

La tercera capacidad llega con `cap-on` en el HTML (`index.html:567`) y JavaScript asume `active=2` (`index.html:876`). Cualquier reordenación rompe esa sincronía. En proyectos, `openIdx` y las clases pueden divergir si el DOM cambia externamente.

**Recomendación:** derivar el estado inicial del DOM o declararlo en un solo lugar y actualizar estado visual y accesible mediante una única función.

### P2 — Límites de altura codificados

El contenido abierto depende de `max-height:200px` y `max-height:1300px` (`index.html:156-157`, `index.html:249-257`). La longitud futura, traducciones o zoom pueden superar esos valores y cortar información.

**Recomendación:** usar una técnica de expansión sin límites mágicos (por ejemplo, grid rows o medición controlada) y comprobar zoom/reflow.

### P2 — Estilos inline mezclados con clases

Retrato, todas las imágenes de proyecto, 18 logos y el botón del CV contienen estilos inline (`index.html:534`, `index.html:612-769`, `index.html:789`, `index.html:835`). Esto dificulta CSP estricta, consistencia y overrides responsive.

**Recomendación:** trasladar reglas repetidas a clases y evitar `style` salvo valores realmente dinámicos.

### P3 — Comparación no estricta y compatibilidad innecesariamente antigua

La navegación usa `==` (`index.html:866`) y el script combina `var`/IIFE con `Array.from`. No es un fallo de ejecución, pero un estándar moderno consistente (`const`, `let`, `===`, módulos o script `defer`) facilita lint y mantenimiento.

## Aspectos positivos confirmados

- Documento corto en profundidad de dependencias: no hay framework ni librerías de terceros de ejecución.
- JavaScript organizado por bloques funcionales e IIFE; no contamina el ámbito global.
- Sintaxis del script inline validada correctamente con Node.
- Variables CSS concentran paleta, radios y curvas de movimiento.
- Los breakpoints están agrupados al final y el HTML mantiene un orden de lectura razonable.

## Riesgos probables

- **P1:** diffs, revisiones y resolución de conflictos pueden volverse poco fiables por las líneas Base64 gigantes.
- **P2:** el CSS muerto puede ocultar una refactorización incompleta y reglas responsive sin efecto.
- **P2:** sin formatter/linter, la mezcla de reglas minificadas, multilínea e inline favorece inconsistencias.
- **P3:** nombres de clases abreviados (`W`, `pr`, `fc`, `sr`) reducen descubribilidad para futuros mantenedores.

## Validación pendiente

- Cobertura CSS real mediante DevTools en todos los breakpoints antes de borrar reglas.
- Perfil de complejidad y listeners en navegador.
- Confirmar si el HTML es artefacto generado. Si lo es, la fuente y pipeline no están en este repositorio y deben incorporarse a la auditoría de mantenibilidad.
