# REAL MADRID FRAMEWORK CSS ⚽

> Un framework CSS modular construido con SCSS, inspirado en los colores y la identidad del Real Madrid: **blanco**, **azul** y **dorado**.

---

## 📋 Tabla de contenidos

- [Descripción general](#descripción-general)
- [Características](#características)
- [Estructura del proyecto](#estructura-del-proyecto)
- [Instalación y uso](#instalación-y-uso)
- [Variables y tokens de diseño](#variables-y-tokens-de-diseño)
- [Mixins y funciones](#mixins-y-funciones)
- [Sistema de grid](#sistema-de-grid)
- [Componentes](#componentes)
  - [Botones](#botones)
  - [Cards](#cards)
  - [Navbar](#navbar)
  - [Alerts](#alerts)
  - [Badges](#badges)
  - [Tablas](#tablas)
  - [Formularios](#formularios)
- [Utilidades](#utilidades)
  - [Helpers generales](#helpers-generales)
  - [Módulo Football](#módulo-football)
- [Documentación interactiva](#documentación-interactiva)
- [Convención de nomenclatura](#convención-de-nomenclatura)
- [Tecnologías utilizadas](#tecnologías-utilizadas)

---

## Descripción general

**Madrid CSS v3** es un framework CSS desarrollado desde cero con **Sass (SCSS)**, siguiendo una arquitectura modular y escalable. Está pensado para construir interfaces web limpias y responsivas que reflejan la identidad visual del Real Madrid: paleta cromática oficial, efectos de brillo dorado (*madrid-glow*), tipografía moderna y componentes reutilizables.

El framework incluye una documentación interactiva completa compuesta por páginas HTML independientes para cada componente, facilitando tanto el aprendizaje como la referencia rápida durante el desarrollo.

---

## Características

- ✅ **Mobile-first** — diseño responsivo que escala desde móvil hacia pantallas de escritorio.
- ✅ **Modular** — cada componente es un archivo SCSS independiente; se usa solo lo que se necesita.
- ✅ **Sin dependencias de JavaScript** — el navbar colapsable funciona exclusivamente con CSS (checkbox hack).
- ✅ **BEM + prefijo `rm-`** — nomenclatura consistente y sin colisiones con otros frameworks.
- ✅ **Sass moderno** — usa `@use`, `@forward`, funciones matemáticas (`sass:math`, `sass:map`) y bucles `@each` / `@for`.
- ✅ **Tokens de diseño centralizados** — colores, tipografía, espaciados y sombras definidos en un único archivo de variables.
- ✅ **Documentación integrada** — 10 páginas HTML con ejemplos de uso para cada componente.

---

## Estructura del proyecto

```
madrid-v3/
├── index.html          # Página de introducción / documentación principal
├── buttons.html        # Documentación de botones
├── cards.html          # Documentación de tarjetas
├── navbar.html         # Documentación de la barra de navegación
├── alerts.html         # Documentación de alertas
├── badges.html         # Documentación de insignias
├── forms.html          # Documentación de formularios
├── tables.html         # Documentación de tablas
├── grid.html           # Documentación del sistema de grid
├── helpers.html        # Documentación de clases utilitarias
├── football.html       # Módulo especial: alineación de fútbol
├── docs-nav.html       # Fragmento de navegación compartido entre páginas de docs
└── scss/
    ├── main.scss           # Punto de entrada principal — importa todos los módulos
    ├── main.css            # CSS compilado listo para producción
    ├── docs.css            # Estilos de la documentación
    ├── _variables.scss     # Tokens de diseño: colores, fuentes, breakpoints
    ├── _mixins.scss        # Mixins y funciones reutilizables
    ├── base/
    │   └── _reset.scss     # Reset CSS normalizado
    ├── layout/
    │   └── _grid.scss      # Sistema de columnas responsivo (12 columnas)
    ├── components/
    │   ├── _buttons.scss   # Botones con variantes de color y tamaño
    │   ├── _cards.scss     # Tarjetas con cabecera, cuerpo y pie
    │   ├── _navbar.scss    # Barra de navegación responsiva (CSS-only)
    │   ├── _alerts.scss    # Alertas de estado (success, danger, warning, info)
    │   ├── _badges.scss    # Insignias e indicadores
    │   ├── _tables.scss    # Tablas con estilos opcionales
    │   └── _forms.scss     # Controles de formulario con validación visual
    └── utilities/
        ├── _helpers.scss   # Clases utilitarias (espaciado, colores, flexbox…)
        └── _footbal.scss   # Componentes de alineación futbolística
```

---

## Instalación y uso

### Opción 1 — Usar el CSS compilado (recomendado para inicio rápido)

Enlaza directamente el archivo `main.css` ya compilado en tu HTML:

```html
<!-- Fuente tipográfica (Roboto) -->
<link rel="preconnect" href="https://fonts.googleapis.com">
<link href="https://fonts.googleapis.com/css2?family=Roboto:wght@300;400;700;900&display=swap" rel="stylesheet">

<!-- Madrid CSS -->
<link rel="stylesheet" href="scss/main.css">
```

### Opción 2 — Compilar desde las fuentes SCSS

Requiere tener instalado **Dart Sass** (`sass >= 1.45`).

```bash
# Instalar Sass globalmente (si no lo tienes)
npm install -g sass

# Compilar en modo desarrollo (con source maps)
sass scss/main.scss scss/main.css

# Compilar en modo producción (minificado)
sass scss/main.scss scss/main.css --style=compressed --no-source-map
```

### Opción 3 — Modo watch (desarrollo continuo)

```bash
sass --watch scss/main.scss:scss/main.css
```

### Ver la documentación

Abre `index.html` directamente en el navegador o sírvela con cualquier servidor local:

```bash
# Con Node.js
npx serve .

# Con Python
python -m http.server 8080
```

---

## Variables y tokens de diseño

Todas las decisiones de diseño están centralizadas en `scss/_variables.scss`. Modificar este archivo afecta a todo el framework de forma consistente.

### Paleta de colores

| Variable                | Valor     | Descripción                          |
|-------------------------|-----------|--------------------------------------|
| `$color-blanco-madrid`  | `#ffffff` | Color primario — blanco Real Madrid  |
| `$color-azul-madrid`    | `#00529F` | Color secundario — azul institucional|
| `$color-dorado-madrid`  | `#FEBE10` | Acento — dorado Real Madrid          |
| `$color-primary`        | `#ffffff` | Alias semántico del blanco           |
| `$color-secondary`      | `#00529F` | Alias semántico del azul             |
| `$color-accent`         | `#FEBE10` | Alias semántico del dorado           |
| `$color-success`        | `#28a745` | Éxito                                |
| `$color-danger`         | `#dc3545` | Error / Peligro                      |
| `$color-warning`        | `#ffc107` | Advertencia                          |
| `$color-info`           | `#17a2b8` | Información                          |

### Tipografía

| Variable           | Valor                  |
|--------------------|------------------------|
| `$font-family-base`| `'Roboto', sans-serif` |
| `$font-size-base`  | `16px`                 |

### Espaciado y efectos

| Variable           | Valor                          | Descripción                        |
|--------------------|--------------------------------|------------------------------------|
| `$border-radius`   | `8px`                          | Radio de borde estándar            |
| `$transition-base` | `all 0.3s ease`                | Transición CSS predeterminada      |
| `$gutter`          | `15px`                         | Espaciado interno de columnas      |
| `$shadow-madrid`   | `0 0 10px $color-dorado-madrid`| Sombra dorada característica       |

### Breakpoints responsivos

| Clave  | Valor   | Dispositivo objetivo         |
|--------|---------|------------------------------|
| `sm`   | `576px` | Móvil horizontal / phablet   |
| `md`   | `768px` | Tablet                       |
| `lg`   | `1024px`| Escritorio                   |

---

## Mixins y funciones

Definidos en `scss/_mixins.scss`. Se importan en los componentes que los necesitan mediante `@use '../mixins' as *`.

### Funciones

#### `strip-unit($number)`
Elimina la unidad de un valor numérico. Se usa internamente para cálculos matemáticos.

```scss
strip-unit(16px) // → 16
```

#### `rem($px, $base: 16px)`
Convierte un valor en píxeles a `rem`, relativo a la base especificada.

```scss
rem(24px)     // → 1.5rem
rem(32px, 16px) // → 2rem
```

---

### Mixins

#### `respond($breakpoint)`
Genera un media query `min-width` a partir de los breakpoints definidos en `$variables`.

```scss
.mi-elemento {
  font-size: 1rem;

  @include respond(md) {
    font-size: 1.25rem;
  }
}
```

#### `flex-center`
Centra el contenido horizontal y verticalmente con Flexbox.

```scss
.contenedor {
  @include flex-center;
}
// Equivale a: display: flex; justify-content: center; align-items: center;
```

#### `button-base`
Aplica los estilos base compartidos por todos los botones del framework.

```scss
.mi-boton {
  @include button-base;
}
```

#### `madrid-glow`
Aplica la sombra dorada característica del framework.

```scss
.elemento:hover {
  @include madrid-glow;
}
// Equivale a: box-shadow: 0 0 10px #FEBE10;
```

#### `madrid-border`
Aplica un borde de 2px sólido en el color dorado de acento.

```scss
.elemento {
  @include madrid-border;
}
// Equivale a: border: 2px solid #FEBE10;
```

#### `container`
Genera un contenedor centrado con ancho máximo de 1200px y gutters laterales.

```scss
.mi-seccion {
  @include container;
}
```

---

## Sistema de grid

Definido en `scss/layout/_grid.scss`. Implementa un sistema de 12 columnas, mobile-first, basado en Flexbox.

### Contenedores

```html
<!-- Contenedor con ancho máximo (75rem / 1200px) -->
<div class="rm-contenedor">...</div>

<!-- Contenedor de ancho completo -->
<div class="rm-contenedor-fluido">...</div>
```

### Filas y columnas

Las columnas se colocan dentro de una fila (`.rm-fila`). El sistema genera clases para todos los tamaños de `1` a `12`.

```html
<div class="rm-fila">
  <!-- Base: aplica en todos los tamaños -->
  <div class="rm-col-12">Ancho completo</div>
  <div class="rm-col-6">Mitad</div>
  <div class="rm-col-4">Un tercio</div>
  <div class="rm-col-3">Un cuarto</div>
</div>
```

### Columnas responsivas

Prefijos disponibles: `rm-col-{n}` (todos los tamaños), `rm-col-sm-{n}` (≥ 576px), `rm-col-md-{n}` (≥ 768px), `rm-col-lg-{n}` (≥ 1024px).

```html
<!-- Apiladas en móvil, 2 columnas en tablet, 3 en escritorio -->
<div class="rm-fila">
  <div class="rm-col-12 rm-col-md-6 rm-col-lg-4">Columna A</div>
  <div class="rm-col-12 rm-col-md-6 rm-col-lg-4">Columna B</div>
  <div class="rm-col-12 rm-col-md-6 rm-col-lg-4">Columna C</div>
</div>
```

---

## Componentes

### Botones

**Archivo:** `scss/components/_buttons.scss`

La clase base es `.rm-btn`. Se combina con modificadores de **color** y **tamaño**.

#### Variantes de color

| Clase            | Descripción                              |
|------------------|------------------------------------------|
| `.rm-btn-azul`   | Fondo azul, texto blanco                 |
| `.rm-btn-dorado` | Fondo dorado, texto azul                 |
| `.rm-btn-blanco` | Fondo blanco, borde gris                 |
| `.rm-btn-borde`  | Transparente con borde azul (outline)    |

#### Variantes de tamaño

| Clase        | Descripción        |
|--------------|--------------------|
| `.rm-btn-sm` | Pequeño            |
| `.rm-btn-md` | Mediano (estándar) |
| `.rm-btn-lg` | Grande             |

#### Ejemplo de uso

```html
<button class="rm-btn rm-btn-azul rm-btn-md">Confirmar</button>
<button class="rm-btn rm-btn-dorado rm-btn-lg">Guardar</button>
<button class="rm-btn rm-btn-borde rm-btn-sm">Cancelar</button>

<!-- Botón deshabilitado -->
<button class="rm-btn rm-btn-azul rm-btn-md rm-deshabilitado" disabled>Deshabilitado</button>
```

> **Efecto hover:** todos los botones incluyen `madrid-glow` (sombra dorada) al pasar el ratón.

---

### Cards

**Archivo:** `scss/components/_cards.scss`

Componente BEM con estructura opcional de cabecera, cuerpo y pie.

```html
<div class="card">
  <!-- Cabecera opcional -->
  <div class="card__header">Título de la tarjeta</div>

  <!-- Imagen opcional -->
  <img class="card__image" src="imagen.jpg" alt="Descripción">

  <!-- Cuerpo -->
  <div class="card__body">
    <h3 class="card__title">Nombre del jugador</h3>
    <p class="card__text">Descripción o información relevante sobre el elemento.</p>
    <button class="rm-btn rm-btn-azul rm-btn-md">Ver más</button>
  </div>

  <!-- Pie opcional -->
  <div class="card__footer">
    <span>Publicado: 24 abril 2026</span>
    <span class="badge badge--accent">Activo</span>
  </div>
</div>
```

> **Efecto hover:** la tarjeta sube (`translateY(-6px)`) y muestra `madrid-border` (borde dorado).

---

### Navbar

**Archivo:** `scss/components/_navbar.scss`

Barra de navegación completamente responsiva implementada **solo con CSS**, sin JavaScript. En móvil muestra un botón hamburguesa; en tablet y escritorio el menú se despliega horizontalmente.

```html
<!-- El checkbox oculto activa/desactiva el menú en móvil -->
<input type="checkbox" id="nav-toggle" class="navbar__toggle-check">

<nav class="navbar">
  <div class="navbar__container">
    <!-- Logo / marca -->
    <a href="#" class="navbar__brand">Madrid CSS</a>

    <!-- Botón hamburguesa (visible solo en móvil) -->
    <label for="nav-toggle" class="navbar__toggle-label">
      <span></span>
      <span></span>
      <span></span>
    </label>

    <!-- Menú de navegación -->
    <ul class="navbar__nav">
      <li><a href="index.html" class="navbar__link navbar__link--active">Inicio</a></li>
      <li><a href="buttons.html" class="navbar__link">Botones</a></li>
      <li><a href="cards.html" class="navbar__link">Cards</a></li>
    </ul>
  </div>
</nav>
```

> **Mecanismo CSS-only:** el estado del menú se controla con `:checked` sobre el `<input type="checkbox">`, sin una sola línea de JavaScript.

---

### Alerts

**Archivo:** `scss/components/_alerts.scss`

Generadas dinámicamente con `@each` sobre un mapa de temas.

| Clase              | Uso                   |
|--------------------|-----------------------|
| `.alert--success`  | Operación exitosa     |
| `.alert--danger`   | Error o peligro       |
| `.alert--warning`  | Advertencia           |
| `.alert--info`     | Información general   |

```html
<div class="alert alert--success">✅ Los cambios se guardaron correctamente.</div>
<div class="alert alert--danger">❌ Ha ocurrido un error. Inténtalo de nuevo.</div>
<div class="alert alert--warning">⚠️ Tu sesión está a punto de expirar.</div>
<div class="alert alert--info">ℹ️ Hay una actualización disponible.</div>
```

> **Efecto hover:** al pasar el ratón, aplica `madrid-glow` (sombra dorada).

---

### Badges

**Archivo:** `scss/components/_badges.scss`

Indicadores compactos, generados con `@each` sobre un mapa de colores.

| Clase               | Color de fondo        |
|---------------------|-----------------------|
| `.badge--primary`   | Blanco (`#ffffff`)    |
| `.badge--secondary` | Azul (`#00529F`)      |
| `.badge--accent`    | Dorado (`#FEBE10`)    |
| `.badge--danger`    | Rojo (`#dc3545`)      |

```html
<!-- Badge estándar -->
<span class="badge badge--secondary">Nuevo</span>

<!-- Badge tipo píldora (borde completamente redondeado) -->
<span class="badge badge--accent badge--pill">Oferta</span>
<span class="badge badge--danger badge--pill">3</span>
```

---

### Tablas

**Archivo:** `scss/components/_tables.scss`

Estructura BEM con modificadores opcionales de estilo.

```html
<table class="table table--striped table--hover table--bordered">
  <thead class="table__thead">
    <tr>
      <th class="table__th">Jugador</th>
      <th class="table__th">Posición</th>
      <th class="table__th">Dorsal</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <td class="table__td">Vinicius Jr.</td>
      <td class="table__td">Extremo izquierdo</td>
      <td class="table__td">7</td>
    </tr>
  </tbody>
</table>
```

| Modificador         | Efecto                                       |
|---------------------|----------------------------------------------|
| `.table--striped`   | Filas alternas con fondo gris muy sutil      |
| `.table--hover`     | Fila activa con fondo azul tenue al pasar el ratón |
| `.table--bordered`  | Añade bordes a todas las celdas              |

---

### Formularios

**Archivo:** `scss/components/_forms.scss`

Sistema de formularios con grupos, etiquetas, controles y retroalimentación visual de validación.

```html
<!-- Campo de texto -->
<div class="form__group">
  <label class="form__label" for="nombre">Nombre completo</label>
  <input type="text" id="nombre" class="form__control" placeholder="Ej. Vinicius Jr.">
</div>

<!-- Campo válido -->
<div class="form__group">
  <label class="form__label" for="email">Correo electrónico</label>
  <input type="email" id="email" class="form__control form__control--valid">
  <span class="form__feedback form__feedback--valid">Correo válido ✓</span>
</div>

<!-- Campo inválido -->
<div class="form__group">
  <label class="form__label" for="pass">Contraseña</label>
  <input type="password" id="pass" class="form__control form__control--invalid">
  <span class="form__feedback form__feedback--invalid">La contraseña debe tener al menos 8 caracteres.</span>
</div>

<!-- Checkbox personalizado -->
<label class="form__check">
  <input type="checkbox">
  <span class="form__check-label">Recordar sesión</span>
</label>

<!-- Radio button personalizado -->
<label class="form__check">
  <input type="radio" name="posicion" value="delantera">
  <span class="form__check-label">Línea delantera</span>
</label>
```

> **Al hacer foco:** el campo aplica `madrid-glow` (sombra dorada). Los estados `--valid` e `--invalid` muestran sombras verde y roja respectivamente.

---

## Utilidades

### Helpers generales

**Archivo:** `scss/utilities/_helpers.scss`

Clases atómicas generadas por bucles Sass para espaciado, visualización, alineación y color. Todas usan el prefijo `rm-`.

#### Espaciado (márgenes y rellenos)

Escala del 1 al 5: `0.25rem` → `0.5rem` → `1rem` → `1.5rem` → `3rem`.

```html
<!-- Márgenes -->
<div class="rm-m-3">Margen en todos los lados (1rem)</div>
<div class="rm-mt-2">Margen superior (0.5rem)</div>
<div class="rm-mb-4">Margen inferior (1.5rem)</div>
<div class="rm-ml-1">Margen izquierdo (0.25rem)</div>
<div class="rm-mr-5">Margen derecho (3rem)</div>

<!-- Rellenos (mismo esquema con rm-p-) -->
<div class="rm-p-3 rm-pt-1">Relleno compuesto</div>
```

#### Visualización

```html
<div class="rm-oculto">Oculto (display: none)</div>
<div class="rm-flex">Flex container</div>
<div class="rm-cuadricula">Grid container</div>
<div class="rm-bloque">Block</div>
<div class="rm-linea-bloque">Inline-block</div>
```

#### Flexbox

```html
<div class="rm-flex rm-jc-entre rm-ai-centro rm-gap-3">
  <div>Elemento A</div>
  <div>Elemento B</div>
</div>
```

| Clase              | Propiedad CSS                       |
|--------------------|-------------------------------------|
| `.rm-jc-inicio`    | `justify-content: flex-start`       |
| `.rm-jc-fin`       | `justify-content: flex-end`         |
| `.rm-jc-centro`    | `justify-content: center`           |
| `.rm-jc-entre`     | `justify-content: space-between`    |
| `.rm-jc-alred`     | `justify-content: space-around`     |
| `.rm-ai-inicio`    | `align-items: flex-start`           |
| `.rm-ai-centro`    | `align-items: center`               |
| `.rm-ai-fin`       | `align-items: flex-end`             |
| `.rm-gap-1` a `rm-gap-4` | `gap` de `0.25rem` a `1.5rem`|

#### Texto y tipografía

```html
<p class="rm-texto-centro rm-negrita">Texto centrado y en negrita</p>
<p class="rm-fs-1">Texto grande (2rem)</p>
<p class="rm-fs-2">Texto mediano (1.5rem)</p>
<p class="rm-fina">Texto delgado (font-weight: 300)</p>
```

#### Colores de texto

```html
<span class="rm-color-azul">Azul Real Madrid</span>
<span class="rm-color-dorado">Dorado Real Madrid</span>
<span class="rm-color-exito">Verde éxito</span>
<span class="rm-color-error">Rojo error</span>
<span class="rm-color-gris">Gris neutro</span>
```

#### Fondos

```html
<div class="rm-fondo-azul">Fondo azul, texto blanco automático</div>
<div class="rm-fondo-dorado">Fondo dorado, texto azul automático</div>
<div class="rm-fondo-claro">Fondo gris muy claro (#f7f9fc)</div>
<div class="rm-fondo-oscuro">Fondo oscuro, texto blanco</div>
```

#### Efectos decorativos

```html
<div class="rm-redondeado">Bordes redondeados (8px)</div>
<div class="rm-sombra-sm">Sombra pequeña</div>
<div class="rm-sombra-lg">Sombra grande azulada</div>
```

#### Componentes estadísticos (`.rm-stat`)

Tarjetas de estadística compactas, ideales para dashboards:

```html
<div class="rm-flex rm-gap-3">
  <div class="rm-stat rm-stat--azul">
    <div class="rm-stat__valor">34</div>
    <div class="rm-stat__label">Goles</div>
  </div>
  <div class="rm-stat rm-stat--dorado">
    <div class="rm-stat__valor">12</div>
    <div class="rm-stat__label">Asistencias</div>
  </div>
</div>
```

#### Tarjetas de características (`.rm-feature`)

```html
<div class="rm-feature rm-feature--azul">
  <div class="rm-feature__icono">⚽</div>
  <div class="rm-feature__titulo">Grid Responsivo</div>
  <div class="rm-feature__desc">Sistema de 12 columnas adaptable a cualquier dispositivo.</div>
</div>
```

#### Tarjetas de navegación (`.rm-navcard`)

```html
<a href="buttons.html" class="rm-navcard">
  <span class="rm-navcard__icono">🔘</span>
  <div>
    <div class="rm-navcard__titulo">Botones</div>
    <div class="rm-navcard__sub">4 variantes de color</div>
  </div>
</a>

<!-- Versión destacada -->
<a href="index.html" class="rm-navcard rm-navcard--destacado">
  <span class="rm-navcard__icono">🏠</span>
  <div>
    <div class="rm-navcard__titulo">Inicio</div>
    <div class="rm-navcard__sub">Introducción al framework</div>
  </div>
</a>
```

---

### Módulo Football

**Archivo:** `scss/utilities/_footbal.scss`

Módulo temático especial para representar la **alineación táctica** de un equipo de fútbol mediante un campo visual interactivo.

#### Campo de fútbol (`.rm-field`)

```html
<div class="rm-field">
  <!-- Portero -->
  <div class="rm-player portero">Courtois</div>

  <!-- Defensas -->
  <div class="rm-player defensa-izquierdo">Mendy</div>
  <div class="rm-player defensa-central">Militão</div>
  <div class="rm-player defensa-derecho">Carvajal</div>

  <!-- Mediocampistas -->
  <div class="rm-player medio-izquierdo">Camavinga</div>
  <div class="rm-player medio-central">Tchouaméni</div>
  <div class="rm-player medio-derecho">Valverde</div>

  <!-- Delanteros -->
  <div class="rm-player extremo-izquierdo">Vinicius</div>
  <div class="rm-player delantero-centro">Mbappé</div>
  <div class="rm-player extremo-derecho">Rodrygo</div>
</div>
```

#### Posiciones disponibles

| Clase CSS               | Posición en el campo              |
|-------------------------|-----------------------------------|
| `.portero`              | Arco (90% vertical, 50% horizontal)|
| `.defensa-izquierdo`    | Lateral izquierdo                 |
| `.defensa-central`      | Central (zona de defensa)         |
| `.defensa-derecho`      | Lateral derecho                   |
| `.medio-izquierdo`      | Mediocampista izquierdo           |
| `.medio-central`        | Mediocampista central             |
| `.medio-derecho`        | Mediocampista derecho             |
| `.extremo-izquierdo`    | Extremo izquierdo                 |
| `.delantero-centro`     | Delantero centro                  |
| `.extremo-derecho`      | Extremo derecho                   |

> **Efecto hover sobre jugadores:** aplica `madrid-glow` (sombra dorada) y escala el elemento (`scale(1.1)`).

---

## Documentación interactiva

El proyecto incluye 10 páginas HTML de documentación completamente funcionales, accesibles abriendo `index.html` en el navegador:

| Página            | Descripción                                        |
|-------------------|----------------------------------------------------|
| `index.html`      | Introducción, paleta de colores y bienvenida       |
| `buttons.html`    | Todas las variantes de botones con ejemplos de código |
| `cards.html`      | Tipos de tarjetas: imagen, cabecera, pie            |
| `navbar.html`     | Navbar responsiva con demo interactiva             |
| `alerts.html`     | Los 4 tipos de alertas                             |
| `badges.html`     | Badges estándar y tipo píldora                     |
| `forms.html`      | Formularios completos con validación               |
| `tables.html`     | Tablas con todos los modificadores                 |
| `grid.html`       | Ejemplos del sistema de columnas                   |
| `helpers.html`    | Referencia completa de las clases utilitarias      |
| `football.html`   | Demo interactiva del campo de fútbol               |

---

## Convención de nomenclatura

Madrid CSS sigue la metodología **BEM** (Block, Element, Modifier) y utiliza el prefijo `rm-` (por *Real Madrid*) en todos los componentes utilitarios y de layout, evitando colisiones con otros frameworks como Bootstrap o Tailwind.

```
Bloque:      .navbar
Elemento:    .navbar__link
Modificador: .navbar__link--active

Utilidad:    .rm-flex
Columna:     .rm-col-md-6
Botón:       .rm-btn .rm-btn-azul .rm-btn-md
```

---

## Tecnologías utilizadas

| Tecnología     | Versión mínima | Uso                                          |
|----------------|---------------|----------------------------------------------|
| Sass (Dart)    | >= 1.45        | Preprocesador CSS principal                  |
| `sass:math`    | Módulo Sass    | Cálculos matemáticos (`math.div`, `math.percentage`) |
| `sass:map`     | Módulo Sass    | Acceso a mapas de variables                  |
| `sass:color`   | Módulo Sass    | Manipulación de colores (`color.adjust`)     |
| Google Fonts   | —              | Tipografía Roboto (300, 400, 700, 900)       |
| HTML5          | —              | Estructura de las páginas de documentación   |

---

## Licencia / Uso Académico

Real Madrid Framework CSS es un proyecto desarrollado con fines exclusivamente educativos como parte de la asignatura **Herramientas de Productividad**, perteneciente a la carrera de **Ingeniería de Sistemas y Redes Informáticos** de la **Universidad de El Salvador**.Este framework fue creado con propósito académico para poner en práctica conocimientos relacionados con maquetación web, preprocesadores CSS, metodologías de organización de código y trabajo colaborativo mediante herramientas de desarrollo. 
La propuesta visual toma inspiración en la identidad gráfica asociada al **Real Madrid C.F.** (colores representativos y estilo temático). Sin embargo, este proyecto **no posee relación oficial, patrocinio ni afiliación** con dicha institución deportiva. 
Todos los nombres, escudos, marcas, colores institucionales y demás elementos asociados al Real Madrid C.F. pertenecen a sus respectivos propietarios y se mencionan únicamente como referencia estética dentro de un contexto educativo.Queda prohibido el uso comercial de este proyecto sin la autorización correspondiente de los titulares de marcas involucradas.

---

<div align="center">
  <strong>Madrid CSS v3</strong> — Hecho con ⚽ y CSS puro
</div>