# Amy — Beyond the Skies: animaciones y efectos v2

Esta versión vuelve a dibujar las piernas y las botas del personaje. Busca separar mejor las rodillas, las pantorrillas, los tobillos, los talones y las puntas. Se mantienen los efectos, sonidos y elementos de interfaz del paquete anterior. El CAPX no se modifica.

Recursos para importar, con una hoja de 12 poses del personaje, una hoja de 12 fotogramas de efectos, cartel de inicio, panel final, portal de llegada y cuatro sonidos sintetizados. Los PNG tienen canal alfa real. Las ilustraciones se generaron con image_gen tomando el sprite del juego como referencia; son una variante nueva de las poses, no fotogramas extraídos del original.

## Organización

```text
Assets/
  Personaje/amy_movimiento_3x4.png
  Efectos/efectos_4x3.png
  Interfaz/inicio_vamos_amy.png
  Interfaz/final_demo_completada.png
  Meta/portal_llegada.png
  Audio/               salto, aterrizaje, inicio, victoria
Vista_previa.html       catálogo y reproducción de las secuencias
manifest.json           medidas reales, cuadrículas, índices y ajustes
prompts.json            instrucciones usadas para generar las imágenes
```

## Importar las hojas en Construct 2

Construct 2 separa una hoja en fotogramas mediante `Import sprite strip...`, desde la barra Animation Frames. Indica las celdas horizontales y verticales, no el número total en ambos campos. Esta función está documentada en el [manual oficial](https://www.construct.net/en/construct-2/manuals/construct-2/interface/dialogs/import-sprite-strip).

1. Crea un Sprite nuevo `AmyVisual` y abre su editor de imágenes y animaciones.
2. Importa `amy_movimiento_3x4.png` con **3 celdas horizontales y 4 verticales**. El orden es de izquierda a derecha, empezando por arriba.
3. Elimina el fotograma vacío que pudiera existir antes de la importación. La hoja debe aportar exactamente 12 fotogramas.
4. Crea cuatro animaciones con los nombres y grupos de la tabla. Puedes importar la hoja en cada una y eliminar los nueve fotogramas que no pertenecen a ese grupo. Los índices de la tabla se refieren a la hoja completa antes de eliminarlos.
5. Mantén el lienzo completo de cada celda. No apliques recorte automático individual: cambiaría los márgenes usados para alinear las poses.

| Animación | Fila de la hoja | Índices desde 0 | Velocidad sugerida | Bucle |
|---|---:|---|---:|---|
| impulso | 1 | 0, 1, 2 | 16 fps | No |
| ascenso | 2 | 3, 4, 5 | 8 fps | No |
| caida | 3 | 6, 7, 8 | 8 fps | No |
| aterrizaje | 4 | 9, 10, 11 | 16 fps | No |

Los valores son un punto de partida para probar, no tiempos validados en el juego. Configura el origen visual cerca de los pies. `ORIGENES_PERSONAJE.csv` incluye una propuesta medida por fotograma, con coordenadas en píxeles dentro de cada celda; `manifest.json` también las contiene. Estas coordenadas compensan los márgenes variables del dibujo y tienen prioridad sobre el origen común inicial (0,5; 0,9). Comprueba la alineación al alternar poses y ajusta el punto de pies si fuera necesario.

Para los efectos, crea sprites visuales sin colisión e importa `efectos_4x3.png` con **4 celdas horizontales y 3 verticales**:

| Animación | Fila | Índices desde 0 | Velocidad sugerida | Bucle |
|---|---:|---|---:|---|
| fx_impulso | 1 | 0–3 | 16 fps | No |
| fx_aterrizaje | 2 | 4–7 | 16 fps | No |
| fx_victoria | 3 | 8–11 | 12 fps | No |

El origen inicial de los efectos es el centro. Crea el efecto a los pies o en la meta, reproduce una vez y destruye su instancia cuando termine. Prueba aproximadamente 36–56 píxeles de ancho para polvo y 50–80 para destellos. El polvo se coloca ligeramente por encima de la plataforma para que no quede enterrado.

## Conservar el salto actual

Recomendación: conserva el objeto `Player` original como controlador físico y usa `AmyVisual`, sin comportamiento Platform ni colisión, para mostrar las poses. Así podrás probar el arte sin cambiar las medidas y el polígono del controlador. Oculta el dibujo del controlador cuando el visual ya esté alineado.

En el controlador define un punto de imagen `Pies` donde coincide con la plataforma. Haz que el origen de `AmyVisual` siga ese punto y ajusta el tamaño visual en conjunto. Las celdas nuevas no tienen la misma proporción que el PNG original: no copies ciegamente el tamaño 50 × 91,6 del controlador al nuevo dibujo.

Cambia de animación al entrar en un estado; evita reiniciarla en cada tick. Usa impulso al saltar, ascenso mientras sube y caída al descender. En el proyecto original el salto es automático al tocar suelo: prioriza el efecto de aterrizaje y luego el impulso, sin añadir una pausa física para mostrar los tres dibujos de recuperación. La secuencia completa de aterrizaje queda disponible si más adelante cambias ese diseño.

En una revisión previa del proyecto se detectó la referencia `salto2`, que no coincidía con los nombres del personaje. Comprueba si sigue presente antes de conectar las nuevas animaciones. Este paquete no modifica eventos ni el CAPX.

## Inicio y final de la demo

- Importa el cartel y el panel como sprites independientes en una capa de interfaz con paralaje cero. Usa Fade o cambios de opacidad/escala para su entrada y salida.
- El cartel de inicio puede aparecer unos 0,7 segundos. Si deseas inmovilizar al personaje durante la presentación, controla explícitamente ese estado y después activa el juego.
- El portal es una imagen estática. Puedes darle un pulso suave con Sine en opacidad o escala y superponer `fx_victoria` al activarse.
- Coloca el portal sobre una plataforma de llegada. Su imagen no crea por sí sola una condición de victoria: decide una altura o tramo final y detén la generación infinita al completar la demo.
- Al llegar, marca un estado `Completado`, desactiva los controles y el salto automático, muestra el panel y reproduce victoria una sola vez. Deja la plataforma sosteniendo al controlador.
- El área inferior del panel está reservada para botones separados. Los textos sugeridos son `Volver a jugar` y `Menú`; deben crearse y conectarse en el proyecto, no están incrustados en esta imagen.

## Audio

Cada sonido tiene WAV fuente y versiones OGG/M4A con el mismo nombre base. Importa el sonido en la carpeta Sounds del proyecto y comprueba su reproducción en el navegador de destino. Se incluye una [referencia del manual de importación de audio](https://www.construct.net/en/construct-2/manuals/construct-2/interface/dialogs/import-audio).

Son efectos sintetizados cortos, sin grabaciones ni voces. Usa salto/aterrizaje a volumen discreto respecto a la música. `verificacion_audio.json` registra duración y pico de señal.

## Qué se ha comprobado

El paquete se revisa por dimensiones, alfa, presencia de archivos, decodificación del audio y reproducción de las hojas en una vista HTML. Esta vista permite inspeccionar el dibujo y los fotogramas; no ejecuta Construct 2 ni garantiza por sí sola su alineación con las colisiones del juego. La importación y la integración de eventos se deben probar dentro del editor antes de sustituir el personaje actual.

El JSON sirve como ficha técnica y no es un importador automático de Construct 2. Se conservan las hojas originales sin recortar para que el propio editor realice la separación.
