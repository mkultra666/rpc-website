# RPC Website — Continuidad

Estado del proyecto, decisiones tomadas y cómo seguir. Este archivo se
actualiza cada vez que hay un cambio importante.

---

## Qué es

Sitio de **Rave Parties Corp**, productora de música electrónica de Buenos
Aires con 30 años de historia (1996–2026). No es solo un sitio para vender
entradas: tiene que mostrar bien las fiestas, los sets de los artistas, el
archivo fotográfico y la historia de la productora.

## Archivo activo

**`rpc-web-v4.html`** — un solo archivo HTML con todo adentro (CSS y JS
incluidos). No hay build, no hay dependencias que instalar, no hay backend.
`index.html` solo redirige a la versión activa.

Para abrirlo en local:

```bash
npx http-server -p 5500 -c-1
# después: http://localhost:5500/rpc-web-v4.html
```

Abrir el `.html` directo con doble click también funciona, salvo los
reproductores de SoundCloud, que necesitan servidor.

### Versiones anteriores

Todo se conserva, nada se borra:

| Archivo | Qué es |
|---|---|
| `rpc-web-v4.html` | **Activo.** Reestructuración completa, 6 secciones |
| `rpc-web-v3.html` | Anterior. De acá salieron el fondo WebGL y el cursor |
| `archive/rpc-web-v2.html` | V2, hecha con Codex |
| `archive/rpc-web-maqueta.html` | V1, la maqueta original |

---

## Estructura del V4

Seis secciones que se cambian sin recargar la página (View Transitions API):

1. **Inicio** — hero con el flyer de la próxima fecha, countdown en vivo,
   banda del manifiesto sobre foto, cifras, agenda, bento de marcas, banda
   de archivo con mosaico, portales a sets/archivo/historia, accesos, RRPP
2. **Agenda** — todas las fechas con panel horizontal (flyer + precios + info)
3. **Las fiestas** — conmutador de las 5 marcas; al elegir una, **toda la
   página se re-tematiza con su color**
4. **Sets** — reproductores de SoundCloud y YouTube con carga diferida
5. **Archivo** — galería con filtros y lightbox (flechas del teclado)
6. **30 años** — línea de tiempo horizontal + los videos de Javier Bússola

Más `entradas` (checkout demo) y `puerta` (terminal de escaneo, uso interno,
se entra desde el pie de página).

---

## Cómo actualizar el contenido

Todo el contenido variable vive en **arrays de JavaScript** al principio del
`<script>`, con comentarios. No hace falta tocar HTML para cargar una fecha.

| Array | Qué controla |
|---|---|
| `EVENTS` | Fechas: nombre, fecha ISO, venue, precios, flyer, color |
| `WORLDS` | Las 5 marcas: logo, descripción, ficha de datos, fotos |
| `SETS` | Sets de SoundCloud y YouTube |
| `GALLERY` | Archivo visual: imagen, epígrafe, año, tipo |
| `TIMELINE` | Hitos de la historia |

### El interruptor `MODO_DISENO`

```js
var MODO_DISENO = true;
```

- **`true`** — todas las fechas se muestran activas, sin importar si ya
  pasaron. Sirve para trabajar el diseño con el material que hay.
- **`false`** — el sitio mira la fecha real de cada evento y separa solo
  "próximas" de "ya pasaron".

**Pendiente:** pasarlo a `false` cuando estén cargadas las fechas reales.

### Agregar una fecha

Copiar un bloque de `EVENTS` y cambiar los datos. El `id` tiene que ser
único. `iso` define el orden. El flyer va en `assets/` y se referencia con
la ruta codificada (los espacios son `%20`).

---

## Decisiones técnicas

**Fondo WebGL y cursor: no se tocan.** El shader de la grilla cromada que
reacciona al mouse y el cursor a medida vienen del V3 y están copiados tal
cual, a pedido explícito. Si hay que refactorizar algo, que no sea eso.

**Sin librerías externas.** Solo Google Fonts. Todo el movimiento está
hecho a mano: WebGL puro, IntersectionObserver, animaciones CSS ligadas al
scroll (`animation-timeline`), View Transitions API, popover nativo para el
lightbox. El sitio funciona sin conexión salvo las fuentes y los embeds.

**Todo degrada.** Si no hay WebGL, no hay fondo pero el sitio funciona. Si
el navegador no soporta `popover`, el lightbox usa una clase. Si el usuario
tiene activado "reducir movimiento", todas las animaciones se apagan desde
JavaScript, no solo desde CSS.

**Proporción de los flyers: 1080×1350 (4:5).** Es el tamaño en el que se
exportan. Se usa `object-fit: contain` en todos lados para que nunca se
recorte un flyer.

---

## Videos

Los originales son másters de exportación, imposibles de usar en web:

| Original | Resolución | Bitrate | Peso |
|---|---|---|---|
| `Javi-1.mp4` | 1080×1920 | 50 Mbps | 436 MB |
| `paño javi.mp4` | 1080×1920 | 20 Mbps | 110 MB |
| `JAVIER2.mp4` | 1920×1080 | 20 Mbps | 102 MB |

Se generaron versiones web en `assets/web/` con ffmpeg (H.264, CRF 23,
`faststart`), que es lo que usa el sitio. Los originales quedan en
`assets/` pero **están excluidos del repositorio** por el límite de 100 MB
por archivo de GitHub.

Comando usado:

```bash
ffmpeg -i entrada.mp4 -c:v libx264 -preset slow -crf 23 \
  -profile:v high -pix_fmt yuv420p -c:a aac -b:a 128k \
  -movflags +faststart salida.mp4
```

Además, ningún video se carga hasta que se le da play: cada uno tiene una
portada y el `<video>` se crea recién al hacer click.

**Pendiente:** cuando los videos estén en YouTube, cambiar los reproductores
locales por embeds y sacar los `.mp4` del repositorio.

---

## Publicación

- **GitHub** (repo privado): respaldo y control de versiones, no hosting.
- **Hostinger**: el hosting elegido. Sirve HTML estático directo; se sube
  por el administrador de archivos o FTP. Sin límite de 100 MB por archivo.
- **Dominio**: se compra más adelante y se apunta a Hostinger.

Al subir: tienen que ir `index.html`, `rpc-web-v4.html` y la carpeta
`assets/` completa (con `assets/web/`). Respetar mayúsculas y minúsculas de
los nombres de archivo: los servidores Linux distinguen, Windows no.

---

## Pendientes

- [ ] Cargar las fechas reales y pasar `MODO_DISENO` a `false`
- [ ] Subir los videos a YouTube y cambiar a embeds
- [ ] Sumar más fotos de pista a `assets/` (ver `DISENO.md`)
- [ ] Sumar sets concretos al array `SETS` (hoy solo está el perfil de
      SoundCloud de Javier Bússola)
- [ ] Comprar el dominio y apuntarlo
