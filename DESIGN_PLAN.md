# Revolución Solar — Plan de diseño (v1)

## Concepto
Entrar en un mapa personal y descubrir progresivamente las fuerzas que operan. Arco visual: oscuridad → aparición → relación → tensión → comprensión → integración.
Traducción al Design System: los capítulos 00–04 viven en `--ink-900` (profundidad); tras un silencio vacío, la página cambia de iluminación a `--paper-050/000` para 05–06 (claridad). No hay gradientes decorativos: el cambio es de luz de fondo, con transición de 900ms.

## Lectura de las referencias (principio → traducción)
- Hero XAstrology: titular serif enorme a la izquierda, objeto circular suspendido a la derecha que sale del eje. → Carta como objeto de gran escala que desborda el viewport; frase del informe como protagonista.
- "Two ways to read the sky": titular centrado + objetos lineales finos. → Diagramas de hairline, sin cards.
- "Time architecture": texto sticky a un lado, sistema orbital al otro. → Capítulo 03 (fuerzas) y 04 (circuito) con columnas sticky.
- Cards redondeadas, dorado y morado → descartados (DS: flat-first, sin negro+dorado).

## Mapa de secciones
00 Umbral — nombre, ciclo, frase ingreso; carta placeholder a gran escala; datos como micro labels.
01 El movimiento central — pregunta display; diagrama Protección ↕ Contacto con tercera coordenada fuera del eje; viewport de silencio ("Estas no son cinco historias"); pull quote.
02 Tu voz y la respuesta — tres decisiones progresivas; contraste de dos preguntas; Arquitectura astrológica como ledger técnico.
03 Tres fuerzas — cada fuerza es un capítulo: número/nombre sticky + frase, interpretación, ledger, tercera fuerza.
04 El circuito — sección sticky conducida por scroll (11 pasos).
— Silencio (cambio de luz).
05 Tu brújula — lista editorial desplegable, primera abierta.
06 Cerrar el ciclo — cinco pasos marcables (guardados sólo en este navegador) + campo para la pregunta del paso 3; tres acuerdos; afirmación final; firma Cruz Andina.

## Sistema de fuerzas (color no es la única señal)
- Fuerza activa / polo A: `--red-100` · punto sólido
- Fuerza pasiva / polo B: `--blue-100` · punto sólido
- Tercera fuerza: `--green-100` (sobre paper `--green-900`) · punto con anillo, SIEMPRE fuera del eje entre A y B, unido a ambos por líneas. Es el patrón reutilizable (componente ThirdForce): no es punto medio, es una nueva coordenada.

## EL CIRCUITO
Anillo de 6 nodos que se enciende nodo a nodo mientras avanza el scroll (el trazo del anillo se dibuja con stroke-dashoffset). Paso 7: lectura ("cada paso intenta proteger algo"). Paso 8: los 4 puntos de intervención de la conciencia se marcan con anillo verde. Paso 9: los mismos nodos se desplazan desde el anillo hacia una espiral abierta que sale del círculo (nueva organización); el anillo original permanece como huella. El primero se cierra sobre sí mismo; el segundo avanza. Ninguno se marca como "malo". Lista oculta accesible con ambos circuitos.

## Grid / responsive
Contenedor máx. 1480px, padding `clamp(1.25rem,5vw,5rem)`. Grid 12 col en desktop para asimetrías; `repeat(auto-fit,minmax(min(100%,Xrem),1fr))` para colapsar. Móvil (<760px): sticky desactivado en fuerzas, circuito con diagrama arriba y narración abajo, navegación reducida a un botón de capítulo.

## Tipografía
Ivy Ora Display (display/pull quotes/diagram labels grandes), Urbanist (body, micro labels, UI). Escalas fluidas según brief, cuerpo 55–70ch, interlineado 1.6–1.7, sin justificar.

## Motion
Microinteracción 180ms · UI 300ms · reveals 800ms · ease `cubic-bezier(.4,0,.2,1)`. Reveals por IntersectionObserver (opacity + 14px). Carta: escala sutil 1→1.06 con scroll. `prefers-reduced-motion`: todo instantáneo.

## Navegación
Desktop: índice vertical fijo a la izquierda (números, etiqueta sólo del capítulo activo, línea de progreso). Móvil: botón "03 · Tres fuerzas" que abre la lista de capítulos.

## Privacidad
`noindex, nofollow`; título genérico sin nombre. Sin contraseña JS: la autenticación irá en infraestructura. Los datos de la práctica (paso 06) quedan en localStorage del dispositivo.

## Contenido reutilizable
v1: el texto editorial vive en la plantilla (editable en el editor); los datos estructurados (ledgers astrológicos, circuito, brújula, pasos, acuerdos) viven en un objeto `REPORT` en la lógica con forma de `report.json`. Siguiente paso: extraer `REPORT` + textos a `content/report.json` cuando exista build.

## Assets faltantes
- Carta de Revolución Solar real (placeholder circular identificado; arrastrar imagen).
- Opcional: fotografía/ilustración según Art Direction para el cierre.

## Decisiones técnicas
Un único Design Component, sin librerías de motion; CSS transitions + un listener de scroll con rAF. Sin WebGL.
