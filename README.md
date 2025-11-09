# Metodología BEM aplicada en TechComponents Landing

## Visión general

- **Bloques raíz por sección crítica**: cada área del landing (`landing-header`, `hero-banner`, `feature-section`, `testimonials`, `pricing`, `contact-section`, `landing-footer`) se modela como bloque independiente para garantizar encapsulamiento de estilos y facilitar su reutilización en otras páginas.
- **Elementos declarativos**: los elementos utilizan el patrón `bloque__elemento` para dejar clara la jerarquía. Por ejemplo, `hero-banner__actions` agrupa los CTAs mientras que `pricing-card__feature` describe ítems de valor.
- **Modificadores semánticos**: se añadieron modificadores (`feature-card--highlight`, `pricing-card--featured`, `testimonial-card--accent`, `hero-banner--soft`) que representan variaciones de apariencia sin duplicar estructura ni cambiar la semántica.

## Decisiones clave

1. **Contexto de navegación**
   - `landing-header` se separó en elementos (`__inner`, `__logo`, `__nav`, `__actions`) para desacoplar marca, navegación y CTA. Al usar un único bloque se mantiene la consistencia entre páginas; el menú incluye enlaces a `index`, `about`, `servicios`, `gallery`, `blog` y `contact`.

2. **Hero con variaciones reutilizables**
   - `hero-banner--with-media` cubre la portada principal con imagen y overlay dinámico; `hero-banner--soft` habilita la variante secundaria usada en páginas internas sin sobrecargar el CSS con nuevas clases.

3. **Grillas repetibles**
   - `feature-card`, `service-card`, `gallery-card`, `blog-card`, `pricing-card` y `team-card` se definen como bloques autocontenidos en sus respectivos layouts, encapsulando iconos, títulos y listas (`__icon`, `__title`, `__list-item`). Esto evita colisiones si se componen en otros contextos.

4. **Formulario accesible**
   - `contact-form` agrupa los campos con `contact-form__group` para mantener label, input y mensajes de ayuda sincronizados. Los estados `:invalid` se manejan dentro del bloque sin clases extra (`--error`).

5. **Footer modular**
   - `landing-footer` distribuye contenido en subbloques (`__about`, `__links`, `__social`, `__legal`). Esta estructura permite añadir nuevas columnas (ej. newsletter) sin reescribir la base.

6. **Páginas específicas**
   - `story`, `mission`, `team`, `services`, `gallery`, `blog`, `blog-cta` extienden el sistema para secciones particulares. Cada bloque vive en `css/blocks/` y se importa sólo en las páginas que lo utilizan.

## Organización de estilos

- **`css/base.css`**: tokens, reset, tipografías base y helpers comunes (`section-heading`).
- **`css/components/buttons.css`**: botón reutilizable (`button`, `button--primary`, `button--ghost`). La variante `--ghost` ahora incluye fondo translúcido claro para mejorar la legibilidad sobre héroes con imagen difuminada.
- **Archivos en `css/blocks/`**: cada bloque cuenta con su archivo dedicado (`header.css`, `hero.css`, `features.css`, `testimonials.css`, `pricing.css`, `contact.css`, `footer.css`, `about.css`, `services.css`, `gallery.css`, `blog.css`). Esto facilita localizar reglas, aplicar tree-shaking y escalar hacia un design system.

## Recomendaciones para futuras modificaciones

- Documentar cualquier nuevo bloque o variación en este archivo para mantener consistencia.
- Importar únicamente los estilos necesarios en cada página para optimizar carga.
- Mantener los nombres en minúsculas con guiones, reservando los modificadores para variaciones visuales y evitando usar estilos para comunicar estados funcionales (ej. `--is-open`).

