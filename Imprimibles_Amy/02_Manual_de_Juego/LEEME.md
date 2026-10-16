# Manual de Amy Beyond the Skies

Manual de cuatro páginas, de 12 × 18 cm, con paleta rosa y lavanda, portada existente y tres avatares nuevos: Amy señalando los controles, mirando hacia el ascenso y dando ánimo. Los PNG están en Assets/Avatares y se generaron con el generador integrado a partir del personaje actual. No se modificaron el CAPX ni los assets originales.

## Archivos

- Digital/Manual_Amy_Beyond_the_Skies_12x18_v1.pdf: cuatro páginas en orden de lectura.
- Imprimir/Manual_Amy_Beyond_the_Skies_Cuadernillo_A4_v1.pdf: dos caras A4 ya ordenadas como cuadernillo.
- Produccion: eventos inspeccionados, huella del proyecto, decisiones de contenido y prompts de los avatares.
- Fuente editable: Branding/99_Produccion/crear_manual_amy.py.

## Cómo imprimir

Imprimir ambas páginas del Cuadernillo sobre una misma hoja A4 horizontal, al 100 %, sin ajustar, a doble cara con giro por el borde corto. No activar otro modo folleto. Recortar el contorno exterior continuo de 24 × 18 cm sin separar las páginas y doblar por el centro. Hacer una prueba de orientación antes de imprimir varias copias.

## Contenido cotejado

Se inspeccionó el proyecto vigente Entregas/Actuales/Amy/Amy_Beyond_the_Skies_integrado_v2.capx. El manual describe movimiento con izquierda/derecha o A/D, salto automático, portal final, reinicio al caer por debajo de la pantalla, paso entre bordes y navegación por botones.

Se prioriza la pausa por clic: los eventos de P/Esc requieren comprobación porque hay bloques consecutivos de pausa y reanudación que pueden ejecutarse con la misma pulsación. No se modificó la lógica del juego. Se omiten los controles de inclinación y táctiles porque el manual se presenta para PC.

No se inventaron vidas, monedas, cronómetro ni meta de altura. La cantidad de plataformas generadas no se presenta como una puntuación.

Verificación: renders de las cuatro páginas y dos caras del pliego revisados visualmente. El contenido se cotejó con el XML, pero no se ejecutó el juego en Construct 2 ni se hizo una prueba física de impresión o plegado.
