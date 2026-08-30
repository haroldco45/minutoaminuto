# Minuto a Minuto — Consejo de Ministros

PWA de transparencia ciudadana. Resume, en lenguaje propio, los anuncios de la declaración a medios de la Presidencia de la República tras el Consejo de Ministros de agosto de 2026, y ancla cada punto al segundo exacto del video oficial para que cualquiera pueda verificarlo.

**Desarrollada por Vibras Positivas HM — Derechos de Autor Reservados**

---

## Qué hace

- **Minutero interactivo**: barra de 18 minutos con una marca por anuncio. Tocar una marca lleva al punto correspondiente.
- **16 anuncios en 5 frentes**: contratación pública, reestructuración del Estado, emergencias, código de tránsito y Libro de la Verdad.
- **Enlace por marca de tiempo**: cada folio abre el video en `youtu.be/fUGvd8pt8Vg?t=SEGUNDOS`.
- **Búsqueda y filtros** por frente temático.
- **Bloque "Verifícalo tú mismo"**: SECOP II, Contraloría, Procuraduría, Fiscalía, RUNT, SIMIT y Presidencia.
- **Compartir por WhatsApp** (usa `navigator.share` cuando está disponible).
- **Funciona sin conexión** una vez instalada.

Sin chat de IA: la app es 100 % estática y compatible con GitHub Pages.

---

## Archivos

| Archivo | Para qué sirve |
|---|---|
| `index.html` | Toda la app (HTML, CSS, JS y contenido) |
| `manifest.json` | Manifiesto PWA |
| `sw.js` | Service worker: caché e instalabilidad |
| `og.png` | Vista previa 1200×630 para WhatsApp, X y Facebook |
| `icon-192.png`, `icon-512.png`, `icon-maskable.png` | Iconos de instalación |
| `README.md` | Este documento |

---

## Antes de publicar: un solo cambio obligatorio

Las etiquetas Open Graph exigen **URL absoluta**. En `index.html` reemplaza las cuatro ocurrencias de:

```
https://vibraspositivashm.com/consejo-ministros/
```

por la URL real donde quede alojada. Ejemplo para GitHub Pages:

```
https://TU-USUARIO.github.io/consejo-ministros/
```

Están en `og:url`, `og:image`, `twitter:image`. Si no se corrigen, WhatsApp no mostrará la tarjeta de vista previa.

---

## Publicar en GitHub Pages

```bash
git init
git add .
git commit -m "Minuto a Minuto — Consejo de Ministros"
git branch -M main
git remote add origin https://github.com/TU-USUARIO/consejo-ministros.git
git push -u origin main
```

Luego: **Settings → Pages → Source: `main` / carpeta raíz**. En dos o tres minutos queda en línea.

Para forzar la actualización de la vista previa en WhatsApp, sube la versión de caché en `sw.js` (`minuto-a-minuto-v1` → `-v2`) y comparte el enlace con un parámetro nuevo la primera vez: `?v=2`.

---

## Actualizar el contenido

Todo el contenido vive en dos arreglos al final de `index.html`:

```js
const EJES = [ … ];      // los cinco frentes temáticos y su color
const ANUNCIOS = [ … ];  // cada anuncio
```

Formato de un anuncio:

```js
{ t: 774,                    // segundo exacto en el video
  eje: 3,                    // id del frente
  etiq: "Instrumento",       // Anuncio | Instrucción | Instrumento | Foco | Alcance | Efecto…
  tit: "Fondo Milagro para la reconstrucción",
  txt: "Descripción en lenguaje propio.",
  dato: "Opcional: contexto verificado o a quién afecta." }
```

Para calcular `t`: minutos × 60 + segundos. `12:54` → 774.

---

## Criterio editorial

- Los puntos se presentan como **anuncios del Gobierno, no como hechos cumplidos**. El aviso bajo el encabezado lo dice de forma explícita.
- No se reproduce el texto literal de la declaración. El resumen está redactado con palabras propias y remite siempre a la fuente.
- El nombre oficial del fondo de reconstrucción es **Fondo Milagro** (no "Fondo Patria Milagro"), anunciado el 12 de agosto de 2026 dentro de la declaratoria de emergencia económica por el sismo de magnitud 7,4 del 10 de agosto.
- El **Libro de la Verdad** es un informe de 135 páginas radicado el 19 de agosto de 2026 ante Fiscalía, Contraloría y Procuraduría, con 82 casos señalados. Un señalamiento no es una condena: la app lo advierte.
- Tono informativo y sin filiación política. Si se agregan anuncios de otros gobiernos o periodos, conviene mantener el mismo criterio.

---

## Ideas para la próxima versión

- Columna de **estado** por anuncio: *anunciado → decreto expedido → en ejecución*, con fecha y enlace al decreto en el Diario Oficial.
- Filtro **"cómo me afecta en el Bajo Cauca"**, marcando los puntos con impacto regional directo (tránsito, energía, reconstrucción).
- Alerta cuando el nuevo Código Nacional de Tránsito llegue a primer debate.

---

**Desarrollada por Vibras Positivas HM — Derechos de Autor Reservados**
