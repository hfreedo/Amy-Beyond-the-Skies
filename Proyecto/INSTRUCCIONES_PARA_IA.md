> Ubicación vigente: `Entregas/Actuales/Amy/Amy_Beyond_the_Skies_integrado_v2.capx`. Usar este CAPX para continuar; `Proyecto_base` del kit es una referencia anterior. Recursos actuales: `Entregas/Actuales/Amy/Animaciones` y la biblioteca `Menus animados/Assets`.

# Instrucciones para otra IA: integrar todos los assets de Amy en Construct 2

## Encargo

Integra los recursos de **Amy — Beyond the Skies** en una copia del proyecto actual de Construct 2. Usa la versión **v2 del personaje**, que revisa piernas, rodillas y botas. Conserva el título, el personaje corregido del menú y la identidad visual rosa/lavanda. Realiza la importación, conecta los eventos y prueba la partida dentro de Construct 2. No basta con mostrar las imágenes en una página HTML.

Trabaja sobre una copia y entrega un CAPX nuevo, por ejemplo `Amy_Beyond_the_Skies_integrado_v2.capx`. Conserva el proyecto de partida para comparar. No cambies velocidad, aceleración, gravedad, fuerza de salto, colisiones ni dificultad para compensar problemas del dibujo.

## 1. Rutas verificadas y cómo localizar los archivos

Carpeta raíz en este PC:

```text
C:\Users\Soul Hoshi\Documents\ChatGPT\PAL - Desarrollo de videojuegos
```

Proyecto de partida actual, relativo a esa raíz:

```text
Juegos de alumnos\JuegoLALA\Nueva carpeta\amy_con_menu.capx
```

Biblioteca de recursos principal:

```text
Menus animados\Assets\
```

En las tablas siguientes, los archivos se indican **relativos a esa biblioteca**. Por ejemplo, el sprite nuevo está exactamente en:

```text
C:\Users\Soul Hoshi\Documents\ChatGPT\PAL - Desarrollo de videojuegos\Menus animados\Assets\Amyy\Juego\Animaciones_v2\Personaje\amy_movimiento_3x4.png
```

También existe una copia idéntica del sprite en:

```text
C:\Users\Soul Hoshi\Documents\ChatGPT\PAL - Desarrollo de videojuegos\Entregas\Actuales\Amy\Animaciones\Assets\Personaje\amy_movimiento_3x4.png
```

Ficha técnica, coordenadas de origen y vista previa:

```text
Entregas\Actuales\Amy\Animaciones\manifest.json
Entregas\Actuales\Amy\Animaciones\ORIGENES_PERSONAJE.csv
Entregas\Actuales\Amy\Animaciones\Vista_previa.html
Entregas\Actuales\Amy\Animaciones\Revision_rodillas.html
```

Si trabajas desde **Amy_handoff_IA_v2.zip**, extráelo primero. Dentro del ZIP, el proyecto está en `Proyecto_base/amy_con_menu.capx`, la biblioteca en `Assets/` y los metadatos en `Documentacion/`. Las mismas rutas relativas de las tablas funcionan bajo `Assets/`. No dependas de que exista el usuario de Windows original en otra máquina.

No uses `Animaciones_v1` ni el ZIP de animaciones v1 para el personaje. El sprite correcto v2 mide **1086 × 1448**, tiene **3 columnas × 4 filas** y su SHA-256 es:

```text
327a3c03f9c615ca20ee3b06137a958a5c2f7f670a367037e326a963ac943105
```

## 2. Situación del proyecto revisado

La revisión actual encuentra `Menu`, `Layout 1`, el objeto físico `Player`, las plataformas `Platform` y un fondo `Fondo_Juego` con capa `FondoJuego`. Hay tipos de objetos para los tres botones y ocho bloques de eventos de menú. No aparece todavía `AmyVisual`. Inspecciona de nuevo el CAPX que vayas a modificar por si el docente lo ha actualizado.

Ya existen recursos integrados: evita duplicar fondos, menús u objetos con el mismo propósito. En los eventos del personaje todavía se observa una referencia a `salto2`, mientras que sus animaciones originales se llaman `quieta`, `salto` y `caida`. Revisa y sustituye las acciones visuales incoherentes al conectar las nuevas animaciones; conserva las acciones físicas de esos mismos eventos.

La ventana del proyecto es **320 × 700**. El layout de juego puede tener otras dimensiones y usa desplazamiento vertical sin límites; toma el viewport como referencia para fondos e interfaz.

## 3. Personaje jugable: importación exacta

Archivo: `Amyy/Juego/Animaciones_v2/Personaje/amy_movimiento_3x4.png`.

1. Crea un Sprite visual nuevo llamado `AmyVisual`. No le añadas Platform, Solid ni Jump-thru. Desactiva sus colisiones.
2. Abre el editor de imágenes/animaciones. En la barra Animation Frames, utiliza **Import sprite strip...**.
3. Selecciona el PNG y configura **3 celdas horizontales y 4 verticales**. Cada celda mide **362 × 362 píxeles**, sin separación adicional ni margen externo que deba descontarse. Los espacios transparentes ya pertenecen a cada celda.
4. La hoja aporta 12 fotogramas. Elimina el fotograma vacío inicial si el editor lo conserva. Comprueba que no queden 13.
5. Divide los fotogramas en las animaciones de la tabla. Una forma manual es importar la hoja en cada animación y borrar los fotogramas que no correspondan.
6. Conserva el lienzo completo de cada celda; no recortes cada figura automáticamente. El recorte invalidaría las coordenadas de origen proporcionadas.

| Animación | Fila de la hoja | Índices en la hoja completa, desde 0 | Velocidad inicial | Loop |
|---|---:|---|---:|---|
| impulso | 1 | 0, 1, 2 | 16 fps | No |
| ascenso | 2 | 3, 4, 5 | 8 fps | No |
| caida | 3 | 6, 7, 8 | 8 fps | No |
| aterrizaje | 4 | 9, 10, 11 | 16 fps | No |
| quieta, opcional | 4 | solo 11 | 0 fps, pose fija | No |

**Atención a los índices:** después de conservar solo una fila, sus tres fotogramas pasan a ser 0, 1 y 2 dentro de esa animación. El CSV usa los índices globales de la hoja completa. Así, `caida` local 0 corresponde al frame global 6, no al global 0.

### Origen, tamaño y colisión

Usa `ORIGENES_PERSONAJE.csv` para colocar el origen de cada fotograma. Las columnas `x_px` e `y_px` se refieren a píxeles dentro de la celda de 362 × 362; las columnas normalizadas son una alternativa. Los orígenes medidos por fotograma tienen prioridad sobre el valor genérico `(0.5, 0.9)` que también aparece como punto inicial en el manifiesto.

Los márgenes de dibujo varían entre filas; por eso un único origen aplicado a todas puede provocar desplazamientos aparentes. Estas coordenadas son una propuesta medida al pie de la silueta: revisa su continuidad en movimiento y ajusta si hace falta.

Conserva `Player` como controlador físico y de cámara. Define en él un punto de imagen `Pies`, alineado con la base de su colisión, y haz que el origen de `AmyVisual` siga ese punto en cada tick. Cuando esté alineado, oculta el dibujo de `Player`, manteniendo su colisión y sus comportamientos activos. Mantén estable el fotograma del controlador si sus animaciones pudieran cambiar el polígono; compara previamente los polígonos originales.

Ajusta el tamaño del **visual** para que la figura ocupe aproximadamente lo mismo que el personaje anterior. No copies ciegamente los 50 × 91,6 del controlador a un lienzo cuadrado: se deformaría y el dibujo quedaría demasiado pequeño por sus márgenes. Conserva la proporción del lienzo y calibra el tamaño visible una vez. Revisa primero con la colisión del controlador dibujada temporalmente.

### Conexión de animaciones

Usa un estado visual y cambia la animación únicamente al cambiar de estado. No reinicies `From beginning` en cada tick.

- Salto físico iniciado: reproducir `impulso` una vez.
- Cuando termine impulso y el personaje siga subiendo: `ascenso`.
- Al empezar a bajar: `caida`, con prioridad sobre un impulso o ascenso que aún siga visualmente activo.
- Al tocar plataforma: emitir el efecto de aterrizaje una sola vez. El juego original rebota automáticamente; conserva ese comportamiento.
- En salto automático, no detengas el controlador para mostrar los tres frames de aterrizaje. Usa esa secuencia si hay una pausa de aterrizaje prevista en el diseño, o para una llegada final detenida. El efecto de impacto sí puede reproducirse durante el rebote.

Comprueba si ya existe inversión horizontal y aplícala al visual, sin modificar las dimensiones del controlador. La hoja mira a la derecha; no inviertas verticalmente el sprite al caer.

## 4. Efectos de salto, aterrizaje y victoria

Archivo: `Amyy/Juego/Animaciones_v2/Efectos/efectos_4x3.png`.

Importa como Sprite con **4 celdas horizontales × 3 verticales**. La hoja mide **1448 × 1086**, y cada celda **362 × 362**.

| Efecto | Fila | Índices globales | Velocidad inicial | Uso |
|---|---:|---|---:|---|
| fx_impulso | 1 | 0–3 | 16 fps | Crear una instancia en los pies al saltar |
| fx_aterrizaje | 2 | 4–7 | 16 fps | Crear una instancia en el punto de contacto al aterrizar |
| fx_victoria | 3 | 8–11 | 12 fps | Crear destellos al activar la meta |

Todos sin bucle ni colisión. Destruye cada instancia cuando termine su animación. Como punto de partida, usa origen centrado y ajusta el desplazamiento para que el polvo quede sobre la plataforma, no enterrado. Prueba un ancho visible de 36–56 píxeles para polvo y 50–80 para destellos; ten en cuenta los márgenes de la celda.

Créa los efectos desde eventos de una sola ejecución por salto/contacto. No los crees en cada tick mientras una condición permanezca verdadera. Tras muchas plataformas no deben acumularse instancias invisibles.

## 5. Fondo y plataformas de la partida

| Recurso relativo a Assets | Medidas PNG | Empleo |
|---|---|---|
| `Amyy/Juego/Fondos/cielo_jugable.png` | 848 × 1855 | Fondo de la partida, sin personajes ni texto |
| `Amyy/Juego/Plataformas/plataforma_lavanda.png` | 2172 × 724 | Textura visual de `Platform` |

**Fondo:** reutiliza `Fondo_Juego` y la capa `FondoJuego` si ya funcionan. Debe cubrir todo el viewport de 320 × 700 por debajo de Game. La capa Game debe dejar ver el fondo. Para mantenerlo fijo, utiliza paralaje cero y ancla sus bordes al viewport de su propia capa; al subir muchas pantallas no deben aparecer huecos. Desactiva su colisión.

**Plataformas:** sustituye únicamente la imagen del objeto existente, conservando sus dimensiones de mundo **50 × 10**, origen, polígono, comportamiento Jump-thru y coordenadas. La textura es 3:1, pero las instancias originales son 5:1; esa compresión ya forma parte de la propuesta visual. No cambies el tamaño físico para igualar la proporción del PNG. Las plataformas creadas durante el juego deben seguir usando ese mismo tipo.

No regeneres el polígono de colisión automáticamente a partir de la transparencia. Comprueba que la superficie dibujada coincida visualmente con la zona de aterrizaje y que el personaje no se sostenga en el aire sobre ella.

## 6. Recursos del menú

| Recurso relativo a Assets | Objeto existente / función |
|---|---|
| `Amyy/Menu/Fondos/fondo.png` | `Fondo_Ammy`, paisaje del menú |
| `Amyy/Menu/Ambiente/nube.png` | `Nube`, decoración que puede desplazarse suavemente |
| `Amyy/Menu/Personajes/personaje.png` | `Ammy_Char`, ilustración del menú con manos revisadas |
| `Amyy/Menu/Titulos/titulo.png` | `Titulo`, «Amy — Beyond the Skies» |
| `Amyy/Menu/Botones/jugar.png` | `Btn_Jugar` |
| `Amyy/Menu/Botones/como_jugar.png` | `Btn_ComoJugar` |
| `Amyy/Menu/Botones/creditos.png` | `Btn_Creditos` |
| `Compartidos/Colegio/logo_colegio_transparente.png` | `Logo_Colegio`, escudo con transparencia |

La ilustración `Ammy_Char` pertenece al menú. No la confundas con el sprite pixel art jugable. No uses el fondo detallado del menú detrás de la partida si dificulta ver plataformas y personaje.

Conserva el título correcto y el escudo suministrado. El PNG original blanco del colegio no es el asset que debe importarse. No añadas un rectángulo blanco detrás del escudo transparente.

Los tres botones propios de Amy son rosa/lavanda. Evita los botones compartidos verdes de Monkey Ron. Cada PNG de botón mide 2172 × 724, pero los botones existentes se muestran a **144 × 48**. Mantén sus posiciones si están bien distribuidas.

**Importante con el hover:** `Set scale` depende del tamaño original del fotograma. Si el frame conserva 2172 píxeles de ancho, el tamaño normal de 144 requiere escala `144/2172`, y el hover de +6 % requiere `(144/2172)*1.06`. No apliques escala 1 a ese PNG grande. Alternativamente, establece explícitamente ancho y alto normales/hover, conservando el centro. Si el editor reduce previamente el PNG a 144 × 48, recalcula según ese tamaño real.

Conecta los botones:

- **Jugar:** iniciar la transición, detener o atenuar el bucle musical y entrar en el juego.
- **Cómo jugar:** mostrar panel con izquierda/derecha, salto automático y cruce de bordes laterales; permitir volver al menú. Verifica los controles reales antes de afirmar que hay controles móviles.
- **Créditos:** mostrar nombre del juego, colegio y autores reales si se conocen. No inventes nombres. Permitir cerrar el panel.

Las vistas HTML ya tienen paneles de demostración, pero eso no significa que existan en el CAPX. En el proyecto revisado no se observan todavía acciones de clic para Cómo jugar y Créditos. Implementa esos paneles con objetos de interfaz del motor; los PNG de botones no aportan lógica por sí solos.

Para la animación del menú utiliza movimientos suaves de nubes, flotación del personaje y entrada por opacidad del título. Reutiliza Sine/Fade existentes y evita duplicarlos sobre la misma propiedad. La ilustración del personaje es una sola pieza; no contiene un esqueleto para animar brazos o piernas.

## 7. Inicio y final de nivel

| Recurso relativo a Assets | Empleo |
|---|---|
| `Amyy/Juego/Animaciones_v2/Interfaz/inicio_vamos_amy.png` | Cartel «¡Vamos, Amy!» |
| `Amyy/Juego/Animaciones_v2/Interfaz/final_demo_completada.png` | Panel «¡Demo completada!» |
| `Amyy/Juego/Animaciones_v2/Meta/portal_llegada.png` | Meta física/visual del recorrido |

Carteles: importa cada PNG como Sprite estático, sin colisión, en una capa de interfaz fija. Conserva su proporción. No forman una hoja de animación: su entrada y salida se animan mediante opacidad, escala o Fade.

**Inicio:** muestra el cartel unos 0,7 segundos y retíralo suavemente. Si inmovilizas la partida durante esa presentación, usa un estado explícito `Inicio`; al finalizar activa el estado `Jugando`. No dejes caer al personaje mientras aún está bloqueado y sin plataforma de apoyo.

**Portal:** importa como Sprite estático en el mundo, sobre una plataforma de llegada accesible. Si se desea, añade un pulso discreto de brillo u opacidad. El PNG no contiene una animación ni crea automáticamente la victoria. El controlador puede detectar el contacto con una zona de meta separada, sin convertir todo el portal en un obstáculo sólido.

**Meta de demo:** actualmente el recorrido genera plataformas de forma continua. Para cerrar la demo propone y documenta un umbral de altura en unidades del juego o un tramo final alcanzable. No llames metros a esas unidades sin definir una conversión. Genera la plataforma final y el portal una sola vez, deteniendo la generación infinita cuando corresponda. Comprueba que el último salto sea alcanzable con la física existente.

Al llegar: marca `Completado`, cancela el salto automático y los controles, conserva el soporte de la plataforma, reproduce los destellos y el sonido una sola vez y muestra el panel. Evita que el personaje salte inmediatamente fuera del portal o que la condición de caída reinicie la partida tras completar.

El área inferior del panel queda reservada para botones separados. Crea `Volver a jugar` y `Menú` con texto/controles del motor; no hay PNG específicos con esas dos etiquetas en este paquete. Reutiliza el estilo rosa/lavanda, pero no uses una imagen que diga Jugar como si dijera Menú. Reiniciar debe limpiar los estados de victoria, efectos, variables y temporizadores.

## 8. Audio y música

Los nuevos sonidos se encuentran en:

```text
Amyy/Juego/Animaciones_v2/Audio/
```

| Nombre base | Uso | Repetición |
|---|---|---|
| `salto` | Inicio de cada salto físico | Una vez por salto |
| `aterrizaje` | Contacto con la plataforma | Una vez por aterrizaje |
| `inicio` | Presentación del nivel | Una vez al iniciar |
| `victoria` | Demo completada | Una vez al completar |

Cada uno tiene WAV fuente y versiones OGG/M4A. Son variantes del **mismo** sonido: no reproduzcas las tres a la vez. Impórtalos como Sounds, comprueba las conversiones del editor y verifica la exportación en el navegador de destino. Usa volumen discreto para salto/aterrizaje frente a la música. Son sonidos sintetizados cortos, no voces ni canciones.

El proyecto de partida ya incluye su bucle musical de menú. Conserva esos archivos y eventos salvo para evitar solapamientos al cambiar de layout o volver al menú. El paquete de efectos v2 no contiene una nueva música de fondo.

## 9. Verificación y entrega exigida

Antes de entregar:

1. Abrir y ejecutar el CAPX en Construct 2. Verificar que no hay referencias a imágenes/animaciones inexistentes.
2. Comprobar el menú, los tres clics, el regreso desde paneles y la ausencia de botones gigantes al pasar el ratón.
3. Revisar las doce poses del personaje a tamaño real y ampliadas: piernas distinguibles, una flexión por rodilla, botas sin deformación y pies sin recortes. Comprobar que no hay saltos visuales por cambios de origen o escala.
4. Comparar los parámetros de Platform y los polígonos con el proyecto de partida. Probar varios aterrizajes, el rebote automático y ambos bordes laterales.
5. Subir varias pantallas: fondo completo, plataformas visibles y ausencia de acumulación de efectos.
6. Llegar realmente a la meta: debe poder alcanzarse, mostrarse una sola victoria, detenerse el salto automático y funcionar ambos botones finales.
7. Probar caída/reinicio y una segunda partida completa para detectar variables o música duplicadas.
8. Exportar y probar el resultado si el entorno lo permite. Diferenciar prueba en editor, exportación y una simple vista HTML.

Entregar un CAPX nuevo con recursos incrustados, breve relación de cambios y pruebas realmente realizadas. Si no se dispone del editor o no se puede ejecutar el juego, declarar esa limitación; la validación del ZIP/XML o la vista previa no equivale a una prueba jugable.

Los recursos proporcionados ya se han comprobado por alfa, dimensiones, separación de celdas y reproducción en una vista HTML. **Todavía no se han integrado ni probado estas nuevas animaciones v2 dentro de Construct 2.**

Referencias de importación: [Import Sprite Strip, manual oficial de Construct 2](https://www.construct.net/en/construct-2/manuals/construct-2/interface/dialogs/import-sprite-strip) y [Sprite, manual oficial](https://www.construct.net/en/construct-2/manuals/construct-2/plugin-reference/sprite).
