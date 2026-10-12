# Hernández & Asociados — flyer digital

Sitio estático de una sola página. Sin build, sin Node, sin backend.
HTML + CSS + JavaScript sin dependencias externas salvo el tema alternativo.

## Publicar en Cloudflare Pages

1. **Sube esta carpeta a un repositorio de GitHub** (puede ser privado).
   ```
   git init && git add . && git commit -m "Flyer Hernández & Asociados"
   git branch -M main
   git remote add origin git@github.com:USUARIO/hernandez-asociados.git
   git push -u origin main
   ```

2. **Cloudflare → Workers & Pages → Create → Pages → Connect to Git.**
   Elige el repositorio y configura:

   | Campo | Valor |
   |---|---|
   | Framework preset | **None** |
   | Build command | *(vacío)* |
   | Build output directory | `/` |
   | Root directory | `/` |

3. **Save and Deploy.** En un minuto queda en `https://TU-PROYECTO.pages.dev` con HTTPS.

4. **Dominio propio** (opcional): Pages → Custom domains → Set up a domain.
   Cloudflare emite el certificado solo. El dominio es el único costo del proyecto.

Cada `git push` a `main` vuelve a publicar. Cada rama genera su propia URL de vista previa.

## Antes de publicar

- [ ] Cambia `hernandezyasociados.pages.dev` por el dominio real en `index.html`
      (etiquetas `og:`, `canonical`, JSON-LD), `robots.txt` y `sitemap.xml`.
- [ ] Activa Cloudflare Web Analytics y pega el token al final de `index.html`.
- [x] WhatsApp confirmado en el 55 8794 5383 — el QR ya es definitivo.

### Pendiente de contenido, no de código

- [ ] Los seis asuntos de **Derecho laboral**. Mientras no lleguen, esa tarjeta
      remite a WhatsApp en vez de listar asuntos.
- [ ] Nombres y cédulas de los **abogados asociados**, si se quieren publicar.
- [ ] Revisar si conviene publicar el **domicilio particular**: quien lleva
      asuntos de violencia familiar expone dónde vive.

## Archivos

```
index.html            la página completa
fonts.css             @font-face de las tipografías autoalojadas
fonts/                Marcellus, Barlow Condensed y Karla en woff2 (128 KB)
retrato.jpg           foto del licenciado, duotono en los colores de la firma
qr-whatsapp.svg       QR estático a wa.me con el mensaje precargado
galeria/              fotos de la sección Galería (optimizadas desde ../Fotos)
og.jpg                1200×630 — la vista previa al compartir por WhatsApp
favicon.svg           emblema del búho
apple-touch-icon.png  icono para iOS
_headers              caché y cabeceras de seguridad (lo lee Cloudflare Pages)
robots.txt sitemap.xml
```

Peso total: unos 490 KB, la mayor parte foto y vista previa.

## Temas

Se publica el tema **Sello**. El tema **Aurea** queda de alternativa: se abre
con `?tema=aurea` al final de la dirección, o desde «Notas de revisión» en el pie.
Aurea es lo único que pide tipografías a Google, y solo cuando se activa.

## Cambios frecuentes

| Qué | Dónde |
|---|---|
| Teléfono y WhatsApp | busca `525587945383` en `index.html` (y regenera el QR) |
| Servicios de cada área | bloques `<article class="card">` |
| Dirección del despacho | `streetAddress` del JSON-LD y el `tile` de Maps en «Contacto» (texto y enlace) |
| Retrato sin duotono | sustituye `retrato.jpg` |
| Fotos de la galería | bloques `<figure class="ph">` en `#galeria`; la imagen va en `galeria/` |
| Quitar «Notas de revisión» | borra el `<dialog id="notes">` y el botón `data-notes` |
