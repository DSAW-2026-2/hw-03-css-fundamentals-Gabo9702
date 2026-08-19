1.- ¿Cuál es la diferencia entre sticky y fixed?

RESPUESTA DE IA:
Aquí te explico la diferencia exacta y por qué elegir una sobre la otra.

position: fixed
Cuando le pones fixed a un elemento, este se arranca por completo del flujo normal de la página.

Cómo actúa: Se pega directamente a la "ventana" de tu navegador (el viewport) en las coordenadas que le digas (por ejemplo, top: 0).

El problema: Como se sale del flujo, los demás elementos de la página actúan como si ese elemento ya no existiera. Si tu <header> mide 100px de alto y lo haces fixed, el texto que estaba debajo (tu sección de características) se subirá de golpe 100px para ocupar su lugar vacío.

El resultado: Tu título o tu primera sección quedarían ocultos debajo del menú, y tendrías que usar trucos (como ponerle un margen gigante al <body>) para arreglarlo.

position: sticky
Esta propiedad es como una mezcla entre un comportamiento normal y uno fijo.

Cómo actúa: Al principio, el elemento respeta su lugar original. Ocupa su espacio físico normal y no empuja a nadie ni se encima con nadie.

La magia: Solo cuando el usuario hace scroll y el elemento toca el borde que le indicaste (como top: 0), se activa y se vuelve "pegajoso".

El resultado: Todo el contenido de abajo fluye perfectamente sin que tengas que ajustar márgenes, pero obtienes el mismo efecto visual de un menú que te acompaña por toda la página.



2.- ¿Por qué se utilizan rem en la parte responsiva?, ¿Y no pixeles o valores porcentuales?

- ¿Por qué no Píxeles (px)? (El problema de accesibilidad)
Los píxeles son unidades absolutas. Si tú le dices a un título font-size: 32px;, medirá exactamente 32 píxeles sin importar nada más.

El problema: Muchas personas con problemas de visión entran a la configuración de su navegador (Chrome, Safari, etc.) y cambian el tamaño de letra predeterminado de "Mediano" a "Muy Grande" para poder leer cómodamente.

Si usas px, tu código ignora la configuración del usuario y fuerza a que la letra sea pequeña, arruinando su experiencia (y fallando las reglas básicas de accesibilidad web).

- ¿Por qué no Porcentajes (%) o la unidad em? (El problema de la cascada)
Los porcentajes (y su unidad hermana, el em) son unidades relativas al elemento padre.

El problema: Imagina que a una sección le pones font-size: 120%, luego adentro pones un artículo con 120%, y adentro un título con 120%. El tamaño se empieza a multiplicar sobre sí mismo (el 120% del 120% del 120%).

Esto crea un efecto de "bola de nieve" donde calcular de qué tamaño real va a quedar una letra se vuelve una pesadilla matemática.

- La solución: rem (Root EM)
La unidad rem es lo mejor de ambos mundos. Significa que es relativa únicamente a la raíz (root) del documento, es decir, a la etiqueta <html>.

¿Cómo funciona? Por defecto, todos los navegadores del mundo le dan a la etiqueta <html> un tamaño base de 16px.

Entonces, si tú escribes 2rem (como hicimos en tu título para tabletas), el navegador calcula: 2 * 16px = 32px.

La magia responsiva: Si un usuario con problemas visuales cambia su navegador para que la letra base sea de 24px en lugar de 16px, tu título con 2rem automáticamente crecerá a 48px (2 * 24px).