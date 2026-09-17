# RPC Website V2 — handoff de diseño y desarrollo

Actualizado: 19 de agosto de 2026  
Archivo activo: `rpc-web-v2.html`  
Archivo que debe conservarse intacto: `rpc-web-maqueta.html` (V1)

## Objetivo

Sitio oficial de RPC / Rave Parties Corp para presentar sus fiestas, concentrar material gráfico, comunicar fechas y vender entradas sin intermediarios. La V2 debe sentirse como un flyer digital vivo: nocturno, intenso, editorial y ligado a la cultura electrónica de Buenos Aires.

## Identidad visual V2

Nombre interno de la dirección: **Chrome Ritual**.

- Base casi negra: `#02040A`.
- Superficies azul-negro: `#07101D` y `#0A1726`.
- Acento principal azul eléctrico: `#168BFF`.
- Acento secundario verde ácido: `#9DFF00`.
- Texto principal: `#F7FBFF`.
- Texto secundario: `#7E97AF`.
- Grilla técnica de 48 px y ruido/grano ambiental.
- Bordes finos, geometría dura y esquinas sin redondear.
- Composición editorial asimétrica, tipografía monumental y sensación de flyer físico suspendido.
- Cromado/alien RPC como firma institucional, sin reemplazar los logos oficiales por reinterpretaciones.

### Tipografía

La familia oficial de marca es **Gotham**.

La variable actual es:

```css
--display: "Gotham", "Gotham SSm", "Montserrat", system-ui, sans-serif;
```

IBM Plex Mono se usa para datos, fechas, precios, etiquetas y microcopy.

Pendiente: si se agregan archivos Gotham `.woff2`, declararlos con `@font-face` para pesos Book, Medium, Bold y Black. Hasta entonces Montserrat funciona como fallback.

## Logo RPC

El usuario exige usar el logo exacto `assets/RPC LOGO BLANCO.png` en el hero.

- No sustituirlo por `RPC.png`: no es la misma variante.
- El archivo blanco solo mide 220 × 118 px.
- Se muestra a resolución nativa para evitar pixelación.
- Si se necesita más tamaño, pedir exactamente el mismo logo en SVG, PDF o PNG de mayor resolución.

## Hero

- RPC blanco oficial como firma principal.
- “30 años de futuro” es una línea conceptual secundaria, no el titular dominante.
- Flyer vertical de Ace Ventura actualmente visible como pieza suspendida.
- Fondo técnico azul, grilla, brillo y marquee inclinado.
- Manifiesto posterior: “No seguimos la escena. La hacemos.”

## Agenda activa

Hay cuatro fechas y ninguna debe eliminarse al incorporar otra:

1. **Infected Mushroom — Live Band & DJ Set**
   - Sábado 22 de agosto, 23:59–07:00.
   - Groove, Av. Santa Fe 4389.
   - General: $55.000.
   - All Access: $75.000.
   - INA warm up; NAX closing.

2. **Trance Resistance — Emiliano Pavón & Korrosiv All Night Long**
   - Sábado 29 de agosto, 23:59–06:00.
   - Uniclub, Guardia Vieja 3360.
   - Free hasta las 02:00.
   - General: $10.000.
   - VIP: $15.000.

3. **Javier Bússola Open to Close Birthday Party — Boiler Edition**
   - Sábado 5 de septiembre, 23:59–07:00.
   - Groove.
   - General: $20.000.
   - All Access: $30.000.
   - Stage/Boiler: $40.000.
   - General 4×3: $60.000.
   - All Access 4×3: $90.000.
   - Beneficio: con ticket de Indecent Noise del 1.º de agosto se ingresa sin cargo.

4. **Ace Ventura Open to Close**
   - Sábado 3 de octubre, 23:59–07:00.
   - Psychedelic Temple / Groove.
   - General: $45.000.
   - All Access: $60.000.
   - Stage/Boiler: $70.000.
   - Preventa agotada: $35.000 / $50.000 / $60.000.

## Paneles de fechas

Este es el componente que más le gustó al usuario. Nació con el panel rojo de Trance Resistance y se extendió a las cuatro fechas.

- Diseño horizontal.
- Flyer completo en proporción 4:5 a la izquierda.
- Información, descripción, precios y venue a la derecha.
- No recortar los flyers: mantener `aspect-ratio: 4/5` y `object-fit: contain`.
- El panel completo **no** debe convertirse en tarjeta vertical 4:5. Se probó y el usuario pidió volver atrás.
- Colores por fecha:
  - Infected: azul eléctrico.
  - Trance Resistance: rojo.
  - Javier: magenta/violeta.
  - Ace: púrpura digital.
- Los cuatro paneles se mueven mediante JavaScript a `#featuredDates`, inmediatamente debajo del encabezado “Próximas fechas”.

## Agenda rápida

Los cajones compactos de fecha/precio no deben competir con los paneles grandes.

- Se mueven mediante JavaScript a `#compactDates`.
- Aparecen más abajo bajo el título “Agenda rápida”.
- Los enlaces internos usan `data-scroll`.

## Sección Javier Bússola

- Video vertical `Javi-1.mp4` con controles y poster `javi.jpg`.
- `paño javi.mp4` funciona como retrato en movimiento, muted/loop.
- Logo `JBwhite.png` sobre el retrato.
- Panel principal de Birthday Party con flyer, precios y promoción.
- Se eliminaron las cinco miniaturas inferiores de campaña porque el usuario las consideró malas/redundantes.
- No reintroducir una tira de flyers debajo del panel.

Los videos pesan aproximadamente 436 MB y 110 MB. Para producción deben comprimirse o servirse mediante streaming/CDN.

## Checkout Ace Ventura

Ace es actualmente la fecha configurada para compra.

- Tres tandas agotadas visibles.
- Tres categorías activas: General, All Access y Stage/Boiler.
- Flyer cuadrado `ace800x800.jpg` arriba del resumen.
- Selector de cuatro artes debajo del flyer principal.
- Al tocar una miniatura cambia el arte grande.
- El total, cantidad, entrada emitida y terminal de puerta están sincronizados con Ace.

## Recursos gráficos usados

- `INFECTED 2026.png`
- `trance resistance emi korro FEED.png`
- `Ace26Posteo.jpg`
- `ace800x800.jpg`
- `ace800passline.jpg`
- `ace261580.jpg`
- `javicumple26-posteo.jpg`
- `javi.jpg`
- `Javi-1.mp4`
- `paño javi.mp4`
- `JBwhite.png`
- `psychedelic temple.png`
- `groove logo.png`
- `RPC LOGO BLANCO.png`
- `LOGO RPC.png`, `RPC.png` e `IconoPrue1bAsset 1s.png` en elementos secundarios/decorativos.

Hay otras variantes de flyers de Javier en `assets`, pero no deben mostrarse como galería inferior.

## Secciones eliminadas o rechazadas

- “Archivo visual”: eliminado por pedido explícito; no restaurar.
- Tira de cinco imágenes debajo de Javier: eliminada; no restaurar.
- Paneles completos verticales 4:5 en grilla de dos columnas: rechazados; conservar panel horizontal.
- Sustituir el logo blanco exacto por otra variante de RPC: rechazado.
- Ampliar el PNG blanco de 220 × 118: se ve pixelado; no hacerlo.

## RRPP oficiales

- Dey: 11 2673-5220
- Flor: 11 3799-3567
- Mica: 11 3695-2929
- Mica Godoy: 11 6647-4073
- Max: 11 4448-9969
- Agustina: 11 7015-8239
- Sabrina: 11 2508-2508

Los enlaces actuales usan `wa.me` con formato internacional argentino.

## Comportamiento técnico

- Todo está contenido en un único HTML con CSS y JavaScript inline.
- No hay build system ni dependencias locales.
- Google Fonts carga Montserrat e IBM Plex Mono.
- Navegación interna por vistas: Inicio, Perfil de fiesta, Comprar y Puerta.
- Los paneles y la agenda se reordenan al cargar mediante JavaScript.
- Respetar `prefers-reduced-motion`.
- V1 y V2 son archivos independientes; nunca sobrescribir V1.

## Preferencias observadas del usuario

- Prefiere módulos fuertes y claros antes que galerías decorativas.
- Rechaza rápidamente recursos repetidos o composiciones que parezcan “archivo”.
- Le gustó especialmente el contraste de flyer + panel de información de Trance Resistance.
- Quiere que se use el material gráfico oficial, pero cada pieza debe tener una función.
- Priorizar identidad RPC, flyers completos, precios legibles y fechas accionables.
- No inventar logos ni reemplazar variantes oficiales.

## Próxima sesión sugerida

1. Abrir `rpc-web-v2.html` y revisar visualmente la posición final de `#featuredDates` y `#compactDates`.
2. Confirmar si Ace debe seguir siendo la fecha inicial del hero y checkout o si se desea un selector de evento.
3. Incorporar Gotham real si aparecen archivos de fuente.
4. Comprimir los dos MP4 antes de publicar.
5. Reemplazar enlaces `#` por Instagram, SoundCloud, Passline y páginas reales.
6. Revisar el flujo responsive de los cuatro paneles en 390 px y 768 px.

