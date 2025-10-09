Portfolio UX/UI — Proyecto-Osella-85240

Sitio web responsive de Lucía Osella (Córdoba, AR) desarrollado con HTML5, Bootstrap 5, SASS y AOS para animaciones suaves. El proyecto está publicado en Vercel y optimizado con metadatos SEO, robots.txt y sitemap.xml.

Enlaces

Repositorio: https://github.com/Lucia-osella/Proyecto-Osella-85240

Sitio en producción (Vercel): https://portfolio-osella-85240.vercel.app/

Tecnologías

HTML5 semántico

Bootstrap 5 (grid, utilidades, componentes)

SASS (variables/tokens, mixins, placeholders con @extend, nesting, @each)

AOS (Animate On Scroll) por CDN

Vercel para deploy

Características

Diseño responsive mobile-first sin overflow horizontal.

Accesibilidad: foco visible, contraste, alt descriptivos y jerarquía tipográfica.

Performance: CSS minificado, recursos desde CDN, imágenes optimizadas.

SEO on-page: título/description por página, Open Graph/Twitter Cards, JSON-LD.

Animaciones: integración de AOS por CDN (sin animaciones inline ni archivos extra).

Estructura
/            index.html
/pages/      acercade.html, experiencia.html, proyectos.html, contacto.html
/assets/
  /css/      style.css        ← generado por SASS
  /scss/     base/, pages/, etc.
  /img/      imágenes del sitio
vercel.json
robots.txt
sitemap.xml


En index.html el CSS se referencia como assets/css/style.css.
En los HTML dentro de /pages/, usar ../assets/css/style.css.

Animaciones (AOS)

Se carga por CDN y se inicializa al final del <body>:

<link rel="stylesheet" href="https://unpkg.com/aos@2.3.4/dist/aos.css" />
<script src="https://unpkg.com/aos@2.3.4/dist/aos.js"></script>
<script>
  AOS.init({
    once: true,
    duration: 600,
    easing: 'ease-out-cubic',
    offset: 60,
    disable: window.matchMedia('(prefers-reduced-motion: reduce)').matches
  });
</script>


Aplicación por página (contenedor principal):

index: data-aos="fade-up" en bloques clave

acerca de: data-aos="zoom-in-up"

experiencia: data-aos="zoom-in-down"

proyectos: data-aos="zoom-out"

contacto: data-aos="fade-up" data-aos-duration="3000"

SASS

Scripts (package.json):

{
  "name": "portfolio-lucia",
  "private": true,
  "scripts": {
    "dev": "sass --watch assets/scss/main.scss assets/css/style.css --style=expanded --source-map",
    "build": "sass assets/scss/main.scss assets/css/style.css --style=compressed --no-source-map"
  },
  "devDependencies": {
    "sass": "^1.93.2"
  }
}


Ejecutar:

# desarrollo (watch + sourcemap)
npm i
npm run dev

# build de producción (minificado)
npm run build


SASS incluye:

Mixins: respond(), respond-down(), focus-ring, surface-card

Placeholders: %surface-card, %chip (reutilizables con @extend)

Tokens: colores, sombras, radios y espaciados

Nesting y estados con &

Estructuras: @each para utilidades

SEO

Reemplazos ya aplicados con la URL de producción:

link rel="canonical"

og:url, og:image

twitter:image

JSON-LD (url, image)

Ejemplo (index):

<link rel="canonical" href="https://portfolio-osella-85240.vercel.app/" />
<meta property="og:url" content="https://portfolio-osella-85240.vercel.app/">
<meta property="og:image" content="https://portfolio-osella-85240.vercel.app/assets/img/foto-perfil.jpg">
<meta name="twitter:image" content="https://portfolio-osella-85240.vercel.app/assets/img/foto-perfil.jpg">
<script type="application/ld+json">
{
  "@context":"https://schema.org",
  "@type":"Person",
  "name":"Lucía Osella",
  "jobTitle":"UX/UI Designer",
  "url":"https://portfolio-osella-85240.vercel.app/",
  "image":"https://portfolio-osella-85240.vercel.app/assets/img/foto-perfil.jpg",
  "sameAs":["https://www.behance.net/lucaosella"]
}
</script>


Nota: si usás cleanUrls en Vercel, /pages/experiencia funciona sin .html. Algunos checkers SEO esperan la versión con .html. Mantené consistencia en tus enlaces internos y, si un checker marca 404, probá con /pages/experiencia.html.

Deploy en Vercel

vercel.json:

{
  "buildCommand": "npm run build",
  "outputDirectory": ".",
  "cleanUrls": true
}


Vercel ejecuta npm run build (compila SASS) y publica la raíz del proyecto.

No se requiere carpeta public/ para este caso estático.

robots.txt y sitemap.xml

Ubicados en la raíz del proyecto.

robots.txt

# Owner: Osella, Lucía — Comisión 85240
User-agent: *
Allow: /

Sitemap: https://portfolio-osella-85240.vercel.app/sitemap.xml


sitemap.xml

<?xml version="1.0" encoding="UTF-8"?>
<!-- Owner: Osella, Lucía — Comisión 85240 -->
<urlset xmlns="http://www.sitemaps.org/schemas/sitemap/0.9">
  <url><loc>https://portfolio-osella-85240.vercel.app/</loc><lastmod>2025-01-01</lastmod></url>
  <url><loc>https://portfolio-osella-85240.vercel.app/pages/acercade.html</loc><lastmod>2025-01-01</lastmod></url>
  <url><loc>https://portfolio-osella-85240.vercel.app/pages/experiencia.html</loc><lastmod>2025-01-01</lastmod></url>
  <url><loc>https://portfolio-osella-85240.vercel.app/pages/proyectos.html</loc><lastmod>2025-01-01</lastmod></url>
  <url><loc>https://portfolio-osella-85240.vercel.app/pages/contacto.html</loc><lastmod>2025-01-01</lastmod></url>
</urlset>



Compatibilidad

Navegadores: Chrome, Edge, Firefox (últimas versiones)

Viewports: mobile (≤576px), tablet (768–991px), desktop (≥992px)

Autora

Lucía Osella — Diseñadora UX/UI
Behance: https://www.behance.net/lucaosella

Comentarios y mejoras son bienvenidos vía Issues o PRs.
