# Portafolio de Fabio Reyes

Sitio de una sola página para Fabio Reyes: fotografía, video, diseño y edición en El Salvador.
Todo vive en `index.html` (HTML, CSS y JS en línea, sin dependencias ni paso de compilación).

## Estructura

```
index.html            la página completa
img/                  fotos ORIGINALES (pesadas, 2-126 MB; la página no las usa)
img/web/              copias de 1800 px: fotos grandes, vitrina y visor
img/thumb/            copias de 720 px: copias de portada, vitrina, cuadrículas y destacadas
videos/               video-01.mp4, video-02.mp4
_respaldo/            versiones anteriores (index-anterior.html = original, index-diseno-2.html = 2.ª versión)
.claude/launch.json   servidor local (node, puerto 5173) para previsualizar
.agents/skills/       skills de diseño instaladas (emilkowalski, design-taste-frontend); no se publica
.taste-skill/         capturas del inspector de diseño; no se publica
```

Nombres de archivo: `<categoría>-NN.jpg` en minúsculas (`retrato-urbano-01.jpg`). Las categorías,
cantidades (`n`), foto de portada (`cover`) y textos están en `CATS` al inicio del `<script>`.
Las 5 copias de la portada salen de `FAN` y "Fotos destacadas" de `PICKS`. El total de trabajos de la
portada se calcula solo a partir de `CATS`.

**Al agregar una foto**: ponla en `img/`, crea su copia en `img/web/` (lado largo 1800 px) y en
`img/thumb/` (720 px), JPG calidad ~80, nombre en minúsculas, y sube `n` en `CATS`. Nunca enlaces
los originales desde la página. Ojo con mayúsculas en extensiones (`.JPG` se rompe en servidores Linux).

## Preferencias de Fabio (mandan sobre cualquier regla de estilo genérica)
- **Esquinas redondeadas suaves**, nunca rectas.
- **Le gustan los degradados**, sobre todo en el amarillo.
- **Combinación amarillo / negro / blanco** como base.
- El cambio de modo claro/oscuro es **un botón con icono** (luna / sol), sin texto.
- Nada de texto grande cruzando encima de fotos que cambian, ni texto pequeño difícil de leer
  sobre fotos. Todo ordenado, legible y con sentido: secciones claras, tarjetas, cuadrículas.
- Le gusta el panel de **Contacto** tal como está: conservarlo en cualquier rediseño.
- En un rediseño se respetan los **textos** (se puede agregar texto coherente); la tipografía sí se puede cambiar.
- Diseño rechazado (no repetir): nombre gigante tipo "monumento", índice de categorías con
  nombres enormes pasando sobre un cuadro fijo con fotos, esquinas rectas, sin degradados.

## Decisiones de diseño (tercera versión, nov. 2026)

Idea: **copias sobre la mesa**. Las fotos se presentan como copias impresas con marco claro (`--print`)
sobre negro, blanco y amarillo en degradado.

### Color
| Token | Oscuro (por defecto) | Claro |
| --- | --- | --- |
| `--bg` fondo | `#0c0c0d` | `#f4f4f2` |
| `--surface` tarjetas | `#161618` | `#ffffff` |
| `--surface-2` | `#202023` | `#ebebe8` |
| `--ink` texto | `#f6f5f2` | `#131313` |
| `--muted` texto secundario | `#a8a39b` | `#57534e` |
| `--accent-text` amarillo como texto | `#ffc414` | `#8f6500` |
| `--print` marco de las copias | `#f6f5f2` | `#ffffff` |

- Amarillo de marca `#ffc414`. Degradado `--grad`: `#ffd84d → #ffc414 → #ffa800` (135°) en botones
  principales, logo, pestaña activa, números de los pasos, tarjeta detrás del retrato y panel de contacto.
- `--grad-text` en "Reyes" y "Fabio" (más oscuro en modo claro). `--grad-soft` es un tinte amarillo
  suave en la vitrina y en "A continuación". Brillo radial `--glow` bajo las copias de la portada.
- Ningún texto encima de fotos: los nombres van al lado (vitrina) o debajo (tira de destacadas).
- Sombras neutras (negras), solo en las copias, el retrato y el formulario.

### Forma
- Radios: `--r-xl` 28px (paneles grandes), `--r-lg` 20px (tarjetas y fotos), `--r-md` 14px (botones),
  `--r-sm` 10px (campos). Cabecera, pestañas, chips y botones de icono: píldora o círculo.
- Bordes de 1px (`--line`) como sombra interior en tarjetas.

### Tipografía
- Titulares: **Unbounded** (Google Fonts, 500-800): ancha y redonda, combina con las esquinas suaves.
  Peso 700, tracking -0.035 a -0.045em.
- Texto: **Schibsted Grotesk** (400-700), 17px, interlineado 1.6. Nada menor a ~13.5px.
- Ya probadas: Plus Jakarta Sans (genérica, 1.ª), Bricolage Grotesque (2.ª versión), Instrument Sans
  (cambiada por estar muy usada).
- El fondo claro es un blanco cálido neutro (`#f4f4f2`), no crema ni beige.

### Secciones, en orden
1. **Cabecera flotante en píldora**: logo "FR" circular con degradado, nombre, enlaces (Trabajo,
   Destacadas, Sobre mí, Cómo trabajo), botón de icono luna/sol y botón "Contacto".
2. **Portada centrada**: línea de servicios, "Fabio **Reyes**", frase, dos botones, **5 copias en
   abanico** (`FAN`; cada una abre su categoría; 3 en móvil) y tarjeta con las 3 cifras.
   - La línea de servicios (Fotografía, Video, Diseño, Edición) **no debe parecer botones**: texto en
     mayúsculas con Unbounded, gris, separado por rombos amarillos en degradado y con trazos que se
     desvanecen a los lados. En pantallas de 460px o menos va en dos filas parejas
     (Fotografía ◆ Video / Diseño ◆ Edición). Nunca por debajo de 11px.
   - Copias del abanico, de izquierda a derecha: evento-17, estudio-03, retrato-urbano-02 (centro),
     producto-01, retrato-04.
3. **Mi trabajo**: pestañas por categoría (nombre + cantidad) y una **vitrina**: a la izquierda número,
   nombre, descripción, cantidad, "Ver galería completa" y flecha a la siguiente; a la derecha 3 fotos
   (portada + 2 repartidas por la categoría) que abren el visor. Las flechas del teclado cambian de pestaña.
4. **Fotos destacadas**: panel con una **tira horizontal** (`PICKS`), flechas y barra de avance en
   degradado; nombre de la categoría debajo de cada foto.
5. **Sobre mí**: retrato como copia inclinada sobre una tarjeta amarilla degradada, presentación y chips;
   luego "Lo que hago": 4 filas de servicio con miniatura (Video con clip real en bucle).
6. **Cómo trabajo** (texto nuevo): 3 pasos numerados (idea, preparación, entrega).
7. **Contacto**: panel amarillo degradado con WhatsApp, correo, Instagram (Copiar) y formulario oscuro
   que abre el correo con el mensaje listo. **Conservar.**
8. **Pie** en tarjeta: logo, enlaces, botón "Volver arriba", derechos.

Galería por categoría (pantalla completa, píldora con "Volver" y categorías, "A continuación") y visor
(flechas, Escape, deslizar, botón Atrás del navegador) funcionan igual que antes.

### Movimiento
- Al cargar, las copias de la portada se reparten desde el centro (escalonado 90ms).
- Entradas suaves al hacer scroll (subir 22px + opacidad, escalonado 70ms). Sin JavaScript todo se ve.
- Al cambiar de categoría, el texto y las fotos de la vitrina entran escalonados.
- Copias que suben al pasar el ratón, zoom lento de fotos, icono luna/sol que gira.
  Con `prefers-reduced-motion` no hay movimiento.

## Previsualizar
Abre la vista previa "portafolio" (`.claude/launch.json`) o, desde la carpeta:

```bash
node -e "require('http').createServer((q,r)=>require('fs').createReadStream('.'+(q.url=='/'?'/index.html':decodeURIComponent(q.url))).on('error',()=>r.end()).pipe(r)).listen(5173)"
```
