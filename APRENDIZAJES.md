# Aprendizajes — Semana 3: CSS y Layouts Responsivos

**Equipo:** Sebastian Andres Sara · Fabian Andres Corpas

## ¿Qué fue lo más difícil?

Lo que más nos costó no fue ninguna propiedad nueva en sí, sino decidir **cuál técnica usar
en cada sección** antes de escribir una sola línea de CSS. Es fácil resolver todo con Flexbox
porque ya lo conocíamos un poco más, pero eso nos hubiera llevado a apilar `flex` dentro de
`flex` para simular columnas y filas al mismo tiempo (justo el problema que Grid resuelve
mejor). Tuvimos que parar, mirar cada sección (header, hero, beneficios, catálogo, footer) y
preguntarnos: *¿esto necesita una sola dirección o dos ejes a la vez?* antes de tocar el código.

El otro punto difícil fue el Box Model "invisible": tuvimos un momento en el que una tarjeta
del catálogo se veía más ancha de lo esperado, y la causa era que un elemento no estaba
heredando `border-box` como esperábamos. Nos recordó por qué la clase insiste tanto en poner
`box-sizing: border-box` de forma global desde la primera línea del CSS.

## ¿En qué situación usarías Grid y en cuál Flexbox?

Usamos **Flexbox** en todo lo que es, por naturaleza, una fila (o columna) de elementos que no
necesitan alinearse con nada más en la página: el header/nav (una fila: logo + enlaces + botón),
la franja de beneficios (una fila de 4 tarjetas que se acomodan solas) y el grid de tarjetas del
catálogo (`flex-wrap`, para que las tarjetas "caigan" a la siguiente fila sin que tengamos que
calcular cuántas caben).

Usamos **CSS Grid** solo en el hero, porque ahí sí necesitábamos controlar **dos ejes a la vez**:
una columna de texto y una columna de imagen, con proporciones distintas (`1.1fr 1fr`) y que
cambiaran juntas de layout en el mismo punto. Esa es la señal que nos quedó más clara: si el
contenido "solo" fluye en una dirección, es Flexbox; si hay que pensar en filas Y columnas
relacionadas entre sí, es Grid.

## ¿Qué breakpoint agregamos y por qué?

Documentamos **cuatro** breakpoints en total (dos "oficiales" del entregable y dos propios,
pedidos en el paso 5 del taller):

- **`min-width: 40rem` (640px)** — en el header. Es el punto exacto en el que el logo, los 4
  enlaces y el botón "Ver catálogo" ya caben en una sola fila sin apretarse, dado el tamaño de
  nuestra tipografía (Bebas Neue es más ancha que una fuente normal). Antes de eso, el menú
  colapsa en un botón de hamburguesa.
- **`min-width: 64rem` (1024px)** — en el hero. Ahí pasamos de 1 a 2 columnas de Grid, porque
  antes de ese ancho el texto y la imagen lado a lado quedaban demasiado angostos para leerse
  cómodo.
- **`min-width: 37.5rem` (600px)** y **`min-width: 48rem` (768px)** — en la franja de
  beneficios: primero pasa de 1 a 2 columnas, y luego de 2 a 4. Elegimos 600px porque es el
  punto real (probando en el navegador, no un número "de manual") en el que dos tarjetas de
  beneficio ya no quedan apretadas con su texto.

El catálogo y el footer decidimos **no** ponerles media queries: con `flex-wrap` en las
tarjetas y `grid-template-columns: repeat(auto-fit, minmax(...))` en el footer, se acomodan
solos sin que tengamos que adivinar breakpoints — es lo que la clase llamó la "regla mental"
más poderosa de Grid responsive.

## Bonus — Flexbox Froggy

_(Pendiente: jugarlo en equipo en https://flexboxfroggy.com/#es y pegar aquí la captura de la
pantalla final antes de entregar.)_
![A screenshot of the Flexbox Froggy game page in Spanish, showing a grid of round green frogs in different colors on a teal pond background. The frogs are arranged in a playful layout, with some facing left and some facing right, and each has a large white belly area. The left side of the screen shows two example cards titled Grid Garden and CSS Scoops, plus a small card with an anchor icon and the label Anchoereum. At the top of the image, browser chrome includes tabs, a URL bar showing https://flexboxfroggy.com/#es, and a few controls. The overall tone is cheerful and game-like, with bright green and yellow colors and a relaxed educational feel. The page includes visible text: FLEXBOX FROGGY, Grid Garden, Anchoereum, CSS Scoops, and the URL https://flexboxfroggy.com/#es.](image.png)
