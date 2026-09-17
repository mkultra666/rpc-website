# RPC Website — Criterio de diseño

Lo que funciona y lo que no, confirmado trabajando sobre el sitio. Sirve
para no volver a proponer cosas ya descartadas ni romper lo que ya está bien.

---

## Intocable

**El fondo WebGL.** La grilla cromada que se deforma siguiendo el mouse.
Es lo que le da identidad al sitio. Se conserva idéntica desde el V3.

**El cursor a medida.** El punto blanco con el anillo que lo persigue con
retraso y se agranda sobre los elementos interactivos. También idéntico.

**El logo oficial.** `assets/RPC LOGO BLANCO.png` se usa tal cual, a su
resolución nativa de 220×118px. Ampliarlo lo pixela. No se reemplaza por
`RPC.png` ni `LOGO RPC.png` sin pedido explícito.

**La proporción de los flyers.** 1080×1350 (4:5). Nunca recortar un flyer:
siempre `object-fit: contain`. Un flyer cortado por la mitad se nota y
queda mal.

---

## Lo que funciona

**Paneles horizontales.** Para las fechas: flyer a la izquierda, info y
precios a la derecha. Es el formato preferido. Se probó en grilla vertical
de dos columnas y se pidió volver atrás.

**Todo tiene que ser visual.** Es lo más importante de todo. Las listas de
texto plano no sirven, por más ordenadas que estén. Cada bloque tiene que
apoyarse en una imagen: foto, flyer o logo. Si una sección se puede mirar
en vez de leer, mejor.

**Las fotos a pantalla completa.** Las bandas full-bleed con foto de fondo,
degradado oscuro encima y tipografía gigante arriba funcionan muy bien.
Con parallax al hacer scroll.

**El color por marca.** Que al elegir una fiesta cambie el color de acento
de toda la página es de las cosas más logradas del sitio. Cada marca tiene
el suyo:

| Marca | Color |
|---|---|
| Psychedelic Temple | `#00E5C4` |
| Magic | `#FFB627` |
| Get Out of the City | `#FF6B35` |
| Javier Bússola Open to Close | `#D9D4E8` |
| Trance Resistance | `#FF2D55` |

**Tipografía grande y en mayúsculas.** Titulares enormes, tracking cerrado,
peso 900. Datos y epígrafes en monoespaciada con mucho espaciado entre
letras. El contraste entre las dos es parte de la identidad.

**Paleta.** Fondo casi negro azulado (`#02040A`), azul eléctrico de acento
(`#168BFF`) y verde lima para los detalles (`#9DFF00`).

---

## Lo que no funciona

**Listas de texto sin imagen.** Fue el señalamiento más fuerte: de la
sección del manifiesto para abajo, el sitio era una pared de botones de
texto. Se reemplazó por bandas con foto, bento de marcas con imagen y
tarjetas grandes.

**Galerías decorativas.** Una tira de flyers repetidos que no aporta
información se rechazó. La diferencia está en la función: el **archivo
visual** sí va, porque tiene filtros, epígrafes y lightbox — cada imagen
se puede ver en grande y sabés qué estás mirando. Una tira de miniaturas
que solo rellena, no.

**Tarjetas verticales para las fechas.** Se probaron y se volvió atrás.

---

## Material disponible

Esto es lo que hay hoy en `assets/`, y es la principal limitación.

**Fotos reales — solo 4:**

| Archivo | Qué es |
|---|---|
| `recap-magic.jpg` | Pista de Magic. La mejor foto que hay |
| `javi.jpg` | Javier Bússola en cabina |
| `notas_magic15-2000pista.jpg` | Histórica: primera Magic, Niceto Club, 2000. Baja resolución (46 KB), usar chica |
| `Backstage; Javier Bussola & Darren Shambhala @ Magic (BQ).jpg` | Backstage. También chica (38 KB) |

**Todo lo demás son flyers y gráfica.** Se usan como material visual porque
son buenos, pero no reemplazan fotos de pista.

> **Lo que más mejoraría el sitio: más fotos de pista.** Con cuatro fotos
> reales el material está estirado al límite. Cualquier foto nueva de
> público, cabina o backstage entra directo al archivo y a las bandas.

**Logos:** `psychedelic temple.png`, `Magic logo.png`,
`get out of the city logo.png`, `JBwhite.png` / `JB.png`, `groove logo.png`.
Trance Resistance no tiene logo propio — se resuelve con una marca de color.

---

## Cómo trabajar

- **El diseño primero.** Si falta contenido real, se usa el que hay sin
  preocuparse por la temporalidad. Los datos se corrigen después.
- **Nada se borra.** Las versiones viejas se archivan, no se eliminan.
- **Mostrar el avance mientras se trabaja**, con el sitio corriendo en
  local al costado del editor.
- **Referencia 2026.** El sitio tiene que verse actual: scroll-driven
  animations, View Transitions, bento, tipografía editorial gigante,
  microinteracciones. Sin librerías de animación de terceros.
