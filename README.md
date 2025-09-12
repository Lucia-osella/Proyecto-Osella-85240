Proyecto-Osella-85240 · Portfolio UX/UI (HTML + Bootstrap + SASS)

Portfolio responsive de Lucía Osella (Córdoba, AR).
Incluye estructura HTML prolija, estilos con SASS (variables, mixins, placeholders, nesting y operadores), grillas con Bootstrap, y deploy en GitHub Pages.

🔗 Enlaces de entrega

Repositorio: https://github.com/Lucia-osella/Proyecto-Osella-85240

Sitio (GitHub Pages): https://lucia-osella.github.io/Proyecto-Osella-85240/


🛠️ Tecnologías y decisiones

HTML5 semántico + Bootstrap 5 (grillas y utilidades).

SASS con:

Variables (tokens): colores, sombras, radios, etc.

Mixins: focus-ring, surface-card, respond()/respond-down().

Placeholders: %surface-card, %chip (extensibles con @extend).

Nesting de selectores y & para estados (:hover, .active, etc.).

Operadores/estructuras: @each (ejemplo incluido abajo).

Accesibilidad: foco visible, contraste, etiquetas y jerarquía.

Performance: CSS minificado, imágenes optimizadas, CDN de Bootstrap.

▶️ Cómo ejecutar y compilar SASS
Opción A — CLI directa (sin Node)
# Compilación continua (watch) + minificado
sass --watch assets/scss/main.scss assets/css/style.css --style=compressed

Opción B — con Node (scripts en package.json)
# Instalar sass si hace falta
npm i -D sass

# Compilar una vez (minificado)
npm run sass:build
# o vigilar cambios
npm run sass:watch


Scripts sugeridos en package.json:

{
  "scripts": {
    "sass:watch": "sass --watch assets/scss/main.scss assets/css/style.css --style=compressed",
    "sass:build": "sass assets/scss/main.scss assets/css/style.css --style=compressed"
  }
}

🔧 Vinculación de estilos y librerías

En cada HTML:

<!-- Bootstrap CSS -->
<link href="https://cdn.jsdelivr.net/npm/bootstrap@5.3.3/dist/css/bootstrap.min.css" rel="stylesheet" />
<!-- Tu CSS generado por SASS -->
<link rel="stylesheet" href="../assets/css/style.css" />


Y al final del <body>:

<script src="https://cdn.jsdelivr.net/npm/bootstrap@5.3.3/dist/js/bootstrap.bundle.min.js"></script>


En index.html, el href de style.css es assets/css/style.css.
En archivos dentro de pages/, usar ../assets/css/style.css.

🧩 Prácticas SASS implementadas

Variables (tokens)

// base/_variables.scss
$ui-accent: #B8D1B5;
:root { --ui-accent:#{$ui-accent}; }


Mixins

// base/_mixins.scss
@mixin focus-ring { outline: 3px solid var(--ui-accent-2); outline-offset: 2px; }
@mixin surface-card($pad:16px,$radius:12px){
  background: linear-gradient(180deg, #fff 0%, #f7faf7 100%);
  border:1px solid var(--ui-border);
  border-radius:$radius;
  box-shadow:0 10px 24px var(--ui-shadow);
  padding:$pad;
}


Placeholders + extend

%surface-card { @include surface-card(); }

// Uso
.exp-card { @extend %surface-card; }


Operadores SASS (@each)

$spacers: (sm:.5rem, md:1rem, lg:2rem);
@each $k, $v in $spacers {
  .mt-#{$k} { margin-top: $v; }
}


Nesting + &

.navbar .nav-link{
  border-radius:10px;
  &:hover{ background: var(--ui-soft); }
  &.active{ background:#e9f3eb; border:1px solid var(--ui-border); }
}


Media queries con mixins

@include respond(sm){ .hero-buttons{ justify-content:center; flex-wrap:wrap; } }

📱 Responsive & diseño

Layouts con Bootstrap Grid (clases row, col- responsivas).

Mobile-first con ajustes por breakpoint:

sm (≤576px): tipografías, gaps, botones centrados.

md/lg (≥768/992px): respiración, grids de 2/3 columnas, etc.

Cards de proyectos: imagen fija (aspect-ratio), título/desc recortados para que todas las tarjetas queden alineadas.

✅ Checklist contra la consigna

HTML

 Estructura semántica y prolija (tabs/indent).

 Enlaces funcionales entre páginas.

 Imágenes con alt descriptivo y rutas relativas correctas.

 Librerías externas linkeadas (Bootstrap CSS/JS).

SASS

 CSS trasladado a SCSS modular (% por páginas/áreas).

 Nesting, @extend (placeholders), mixins, variables.

 Operadores del lenguaje SASS (@each) demostrados.

 Transiciones/animaciones y transformaciones en componentes (hover de cards, etc.).

Git / GitHub

 .gitignore (excluye node_modules, etc.).

 Historial de commits con mensajes claros.

 Repositorio público y URL compartida.

 (Opcional) GitHub Pages activado para deploy.

🧪 Compatibilidad probada

Navegadores: Chrome, Edge, Firefox (últimas versiones).

Viewports: mobile (≤576px), tablet (768–991px), desktop (≥992px).

🚀 Deploy en GitHub Pages

Abrí el repo en GitHub → Settings.

Pages → Branch = main y /root.

Guardá. La URL pública aparece arriba:
https://<usuario>.github.io/Proyecto-Osella-85240/

Si usás rutas relativas como en este proyecto, no necesitás cambios extra.

📥 Cómo clonar y correr
git clone https://github.com/Lucia-osella/Proyecto-Osella-85240.git
cd Proyecto-Osella-85240

# Opción A: CLI SASS
sass --watch assets/scss/main.scss assets/css/style.css --style=compressed

# Opción B: con Node
npm i
npm run sass:watch


Abrí index.html en tu navegador (o servilo con una extensión como “Live Server”).

🧾 Convención de commits (ejemplos)

feat(home): hero responsive + botones centrados

feat(scss): estructura modular, tokens y mixins

style(projects): cards alineadas, título/desc recortados

fix(navbar): estado active y contraste

chore: agrega .gitignore y scripts sass

🪪 Licencia

Uso académico/educativo. Podés reutilizar la estructura y los estilos con atribución a la autora.

✍️ Autora

Lucía Osella — Diseñadora UX/UI
Behance: https://www.behance.net/lucaosella

Para feedback o mejoras, abrí un Issue o enviá un PR.
