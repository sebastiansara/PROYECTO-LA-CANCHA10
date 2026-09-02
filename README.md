# Cancha10 — Tienda de fútbol urbano

Entregable semanal de **Desarrollo Frontend** — Semana 3: *Fundamentos de CSS y Layouts Responsivos*.

**Integrantes:** Sebastian Andres Sara · Fabian Andres Corpas
**Universidad Tecnologica De Bolivar — Cartagena**

## ¿Qué es esto?

Una landing page responsive de una marca ficticia de fútbol urbano (**Cancha10**), pensada
para practicar Box Model, Flexbox, Grid, media queries mobile-first y unidades CSS **sin usar
ningún framework** (Bootstrap llega la próxima semana).

No usamos el ejemplo de "Auriculares Pro" de la clase para que el entregable no sea idéntico
al de otros compañeros que sigan el mismo taller al pie de la letra: mismo objetivo técnico,
producto y diseño propios.

## Cómo verlo

Abre `index.html` directamente en el navegador (no necesita servidor ni build). Para ver el
comportamiento responsive, abre las herramientas de desarrollador (`F12`) → *Toggle device
toolbar* y prueba en 375px, 768px y 1024px+.

## Estructura

```
cancha10-frontend/
├── index.html          # header + hero + beneficios + catálogo (grid de tarjetas) + footer
├── css/
│   └── styles.css       # reset, variables, box model, flexbox, grid, media queries
├── APRENDIZAJES.md       # reflexión pedida en el entregable
└── README.md
```

## Técnicas usadas (para explicar en clase)

| Sección | Técnica | Detalle |
|---|---|---|
| Reset global | Box Model | `box-sizing: border-box` en `*` (Regla #1 de la clase) |
| Header / nav | Flexbox | `justify-content: space-between` + `flex-wrap` + media query propia en 640px |
| Hero | CSS Grid | `grid-template-columns` de 1 columna en móvil a 2 columnas (`1.1fr 1fr`) en desktop, sin media query extra gracias a `minmax()` |
| Franja de beneficios | Flexbox + breakpoint propio | `flex-wrap` con un breakpoint personalizado en `600px` (no es 768 ni 1024, es nuestro) |
| Catálogo de productos | Flexbox + `flex-wrap: wrap` | Tarjetas de `flex: 1 1 260px`, colapsan solas sin media query |
| Footer | CSS Grid | `grid-template-columns: repeat(auto-fit, minmax(180px, 1fr))` |
| Breakpoints documentados | Mobile-first | `min-width: 640px` (tablet) y `min-width: 1024px` (desktop), comentados en `styles.css` |
| Unidades | `rem` por defecto, `px` solo en bordes/sombras, `%`/`fr` en layouts, `vw` en el alto del hero | Ver sección 6 de la clase |

## Cómo explicarlo al profesor (guion rápido)

1. Abrir `index.html` a 375px de ancho → mostrar que ya se ve completo y usable (mobile-first).
2. Ir agrandando la ventana → señalar el breakpoint de 640px (el nav pasa de apilado a una fila)
   y el de 1024px (el catálogo pasa de 1 a 3 columnas).
3. Abrir `styles.css` y mostrar los comentarios `/* BREAKPOINT: ... */` que documentan cada media
   query.
4. Explicar por qué el header es Flexbox (una sola fila) y el hero es Grid (dos ejes: la columna
   de texto y la columna de imagen, más el `grid-template-rows` del layout general).
5. Mostrar `APRENDIZAJES.md` con las respuestas del equipo.

## Bonus

Flexbox Froggy: pendiente de completar por el equipo antes de la entrega — la captura final
va en `APRENDIZAJES.md` (jugarlo en https://flexboxfroggy.com/#es).
