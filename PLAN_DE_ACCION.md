# PLAN DE ACCIÓN — Impulso Legal

---

## Prompt de Contexto (para el agente de desarrollo)

Eres un desarrollador web experto en diseño minimalista, profesional y 100% responsive. Vas a construir una **landing page demo** para **Impulso Legal — Estudio Jurídico y Notarial**, un estudio legal y notarial en Montevideo, Uruguay.

**Stack:** HTML5 · CSS3 (custom properties, grid, flexbox, clamp) · JavaScript ES6+ · Google Fonts (Inter) · Lucide Icons (CDN unpkg)

**Paleta de colores:**
- Principal: `#69363D` (borgoña/granate)
- Secundario/Acento: `#D0A962` (dorado/ámbar)
- Blanco: `#ffffff`

**Referencia de estructura y estilo:** Los proyectos `EJEMPLOS/escribanaScrollini` y `EJEMPLOS/estudioNotariadoModelo` son la base de diseño. Ambos ya son 100% responsive. Se deben respetar sus convenciones: nomenclatura BEM-like, variables CSS, animaciones fade-in con IntersectionObserver, hamburger menu mobile, smooth scroll con offset de navbar, breakpoints en 900px y 640px, y el patrón de archivos separados (index.html / css/styles.css / js/main.js).

**Assets disponibles:**
- `img/logo.png` — Logo de la empresa (navbar y footer)
- `img/Screenshot_1.png` — Imagen hero (derecha, enmarcada)

**Secciones:**
1. NavBar — Logo izq. + links nav + CTA WhatsApp + hamburger mobile
2. Inicio (Hero) — Texto izq. + imagen enmarcada der.
3. Servicios — Dos grupos: Servicios Jurídicos + Servicios Notariales
4. Nosotros — Perfil Dra. Karen Medina García
5. Contacto — Tarjetas de contacto + tabla de horarios + Google Maps
6. Footer — Logo + slogan izq. / links nav der.
7. Botón flotante WhatsApp (abajo a la izquierda, fijo)

---

## Fases de Desarrollo

### Fase 1 — Estructura HTML (`index.html`)

- [ ] Setup base: `<!DOCTYPE html>`, viewport meta, SEO meta tags, Google Fonts (Inter), Lucide Icons CDN
- [ ] **NavBar:** logo (img/logo.png) a la izquierda, links de navegación (Inicio, Servicios, Nosotros, Contacto), botón CTA WhatsApp, hamburger toggle (3 líneas → X) para mobile
- [ ] **Hero (#inicio):** 2 columnas — izq: badge + título "Impulso Legal Estudio Jurídico y Notarial" + slogan inventado + botones CTA; der: imagen `img/Screenshot_1.png` con frame decorativo
- [ ] **Servicios (#servicios):** sección con dos grupos — "Servicios Jurídicos" y "Servicios Notariales", cada uno con tarjetas de servicio con icono y nombre
- [ ] **Nosotros (#nosotros):** sección con texto biográfico de la Dra. Karen Medina García (trayectoria inventada coherente), valores del estudio
- [ ] **Contacto (#contacto):** fila de tarjetas de contacto rápido (teléfono, WhatsApp, mail), tabla de horarios semanal, iframe Google Maps embed
- [ ] **Footer:** columna izquierda (logo + nombre + slogan), columna derecha (links de secciones)
- [ ] **Botón flotante WPP:** posición fija abajo-izquierda, color verde WhatsApp `#25D366`, icono Lucide

---

### Fase 2 — Estilos CSS (`css/styles.css`)

- [ ] **Variables CSS:** `--primary: #69363D`, `--primary-hover`, `--secondary: #D0A962`, `--dark`, `--gray`, `--light-gray`, `--white`, `--border`, `--shadow-*`, `--radius-*`, `--navbar-h: 72px`, `--transition`, `--font`
- [ ] **Reset y base:** box-sizing, smooth scroll, scroll-padding-top, body, a, img
- [ ] **Utilidades:** `.container` (max-width 1160px, centrado), `.section` (padding-block 5rem), `.fade-in` / `.fade-in.visible` (transform + opacity, transition)
- [ ] **Botones:** `.btn`, `.btn--primary` (borgoña), `.btn--secondary` (dorado), `.btn--white`, `.btn--ghost`, `.btn--lg`
- [ ] **NavBar:** fijo, altura 72px, fondo blanco siempre, `box-shadow` al hacer scroll (`.scrolled`), links con hover en color secundario, hamburger animado (3 líneas → X), dropdown menu mobile
- [ ] **Hero:** fondo degradado oscuro basado en `--primary`, 2-col grid, `min-height: calc(100svh - var(--navbar-h))`, imagen con frame decorativo (borde dorado + sombra), badge pill, título grande con `clamp()`, botones de acción
- [ ] **Servicios:** fondo `--light-gray`, dos grupos con título de sección y subtítulo, grid `auto-fill minmax(220px, 1fr)`, tarjetas con icono + nombre, hover lift + borde dorado
- [ ] **Nosotros:** fondo blanco, 2-col (`1fr auto`), texto biográfico + valores, frame para foto/card con acento dorado
- [ ] **Contacto:** fondo `--light-gray`, fila de tarjetas de contacto, bloque de horarios, mapa iframe al 100% (height 420px)
- [ ] **Footer:** fondo `--dark`, color blanco, flex row (logo+slogan izq, nav links der), copyright
- [ ] **Botón flotante WPP:** `position: fixed`, `bottom: 24px`, `left: 24px`, border-radius 50%, tamaño 56px, sombra, hover scale
- [ ] **Media queries:**
  - `@media (max-width: 900px)`: hero 1-col, services 2-col, about 1-col, contact 2-col, hamburger visible
  - `@media (max-width: 640px)`: hero texto centrado, services 1-col, contact 1-col, footer 1-col

---

### Fase 3 — Lógica JavaScript (`js/main.js`)

- [ ] Inicialización Lucide Icons (`lucide.createIcons()`)
- [ ] **Navbar scroll:** evento `scroll` → toggle clase `.scrolled` cuando `scrollY > 20` (passive listener)
- [ ] **Hamburger menu:** `openMenu()` / `closeMenu()`, bloqueo de scroll en body (`overflow: hidden`), cierre al hacer click en link, cierre al click fuera del menú
- [ ] **Smooth scroll:** override de `a[href^="#"]` con offset del navbar (`navbar.offsetHeight`)
- [ ] **Fade-in animations:** IntersectionObserver (`threshold: 0.1`, `rootMargin: -40px`) → `.visible` con stagger delay `i * 0.05s`

---

### Fase 4 — Revisión y QA

- [ ] Probar responsive en viewports: 360px, 390px (iPhone), 640px, 768px, 900px, 1280px, 1440px
- [ ] Verificar todos los datos de contacto (teléfono, WhatsApp, email, mapa)
- [ ] Verificar que el botón flotante WPP abre `https://wa.me/59895594881`
- [ ] Revisar padding/margins en mobile (especialmente hero, servicios, nosotros)
- [ ] Verificar que el iframe del mapa carga correctamente
- [ ] Confirmar que todas las animaciones fade-in funcionan
- [ ] Revisar accesibilidad básica: `alt` en imágenes, `aria-label` en botones, roles de landmarks

---

## Datos para uso en el código

```
Empresa:        Impulso Legal — Estudio Jurídico y Notarial
Profesional:    Dra. Karen Medina García
Slogan:         "Tu respaldo legal, en cada decisión que importa."
Teléfono:       095 594 881
WhatsApp:       https://wa.me/59895594881
Email:          dra.karenmedinagarcia@gmail.com
Dirección:      Of. 1204, Av. 18 de Julio 1474, 11200 Montevideo
Maps embed URL: https://www.google.com/maps/embed?pb=!1m18!1m12!1m3!1d3272.6...
(usar el iframe embed del pin dado en el contexto)

Horarios:
  Lunes a Viernes:  8:00 – 18:00
  Sábado:           Cerrado
  Domingo:          Cerrado
```

---

## Servicios a incluir

**Servicios Jurídicos:**
- Derecho de Familia (icono: `users`)
- Divorcios y Separaciones (icono: `scale`)
- Asesoramiento Empresarial (icono: `briefcase`)
- Sucesiones y Herencias (icono: `file-text`)
- Derecho Laboral (icono: `hard-hat`)
- Contratos y Acuerdos (icono: `clipboard-list`)

**Servicios Notariales:**
- Compraventa de Inmuebles (icono: `home`)
- Poderes Notariales (icono: `stamp` / `pen-tool`)
- Certificaciones y Autenticaciones (icono: `badge-check`)
- Testamentos y Protocolizaciones (icono: `book-open`)
- Arrendamientos (icono: `key`)
- Constitución de Sociedades (icono: `building-2`)

---

## Estructura de archivos resultado

```
Impulsolegal/
├── index.html
├── css/
│   └── styles.css
├── js/
│   └── main.js
└── img/
    ├── logo.png
    └── Screenshot_1.png
```
