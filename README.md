# ✨ Amy — Beyond the Skies (Aventura en el Cielo)

## Versión vigente: v3.1

Menú corregido para mouse y toque, sin el texto negro de instrucciones; conserva salto, rescate y festejo al aterrizar en la plataforma del portal.

- **Abrir en Construct 2:** [`Proyecto/Amy_Beyond_the_Skies_animaciones_v3_corregido.capx`](Proyecto/Amy_Beyond_the_Skies_animaciones_v3_corregido.capx).
- **Descargar:** [CAPX](https://github.com/hfreedo/Amy-Beyond-the-Skies/releases/download/v3.1/Amy_Beyond_the_Skies_animaciones_v3_corregido.capx) · [paquete de proyecto y recursos](https://github.com/hfreedo/Amy-Beyond-the-Skies/releases/download/v3.1/Amy_actual_v3_1.zip).
- **Abrir en Windows:** ejecutar [`Proyecto/ABRIR_AMY.cmd`](Proyecto/ABRIR_AMY.cmd) desde el Explorador tras extraer el paquete.
- **Historial:** [CHANGELOG.md](CHANGELOG.md). Las versiones anteriores se conservan en Git y Releases.
- **Pruebas y límites:** [Proyecto/VALIDACION.md](Proyecto/VALIDACION.md). Los recursos de etapas anteriores conservan sus nombres originales.


<p align="center">
  <img src="Portadas/Amy_Beyond_the_Skies_PC_Demo.png" alt="Portada Amy: Beyond the Skies" width="760">
</p>

<p align="center">
  <a href="https://github.com/hfreedo/Amy-Beyond-the-Skies/releases/latest/download/Amy_Beyond_the_Skies_animaciones_v3_corregido.capx">
    <img src="https://img.shields.io/badge/🎮_Descargar_Proyecto_Construct_2-Amy__animaciones__v3.capx-d946ef?style=for-the-badge" alt="Descargar CAPX v3 corregido">
  </a>
  <a href="https://github.com/hfreedo/Amy-Beyond-the-Skies/releases/download/v3.1/Amy_actual_v3_1.zip">
    <img src="https://img.shields.io/badge/📦_Descargar_Kit_de_Recursos-Amy__recursos.zip-8b5cf6?style=for-the-badge" alt="Descargar Kit de Recursos">
  </a>
</p>

---

## 👋 ¡Bienvenidos al repositorio oficial de Amy: Beyond the Skies!

Este repositorio reúne el proyecto actualizado de **Amy: Beyond the Skies** (desarrollado en **Construct 2**), junto con su hoja de sprites mejorada (`v2`), efectos visuales de salto/aterrizaje/victoria, sonidos, música del menú, guías de desarrollo y **materiales listos para imprimir para la exposición escolar (stickers, manual de juego y portadas)**.

---

## 📥 1. ¿Cómo descargar el juego? (Guía para alumnos)

Elige la opción que mejor se adapte a lo que necesitas:

1. **Solo quiero abrir el juego actualizado en Construct 2 (Recomendado):**
   - Haz clic en el botón rosa superior **🎮 Descargar Proyecto Construct 2 (`Amy_Beyond_the_Skies_animaciones_v3_corregido.capx`)** o entra en [`Proyecto/Amy_Beyond_the_Skies_animaciones_v3_corregido.capx`](Proyecto/Amy_Beyond_the_Skies_animaciones_v3_corregido.capx) y pulsa **Download raw file**.
2. **Quiero descargar el paquete vigente con el proyecto y las animaciones:**
   - Haz clic en el botón violeta **📦 Descargar Kit de Recursos** o entra a la sección [**Releases (Lanzamientos)**](https://github.com/hfreedo/Amy-Beyond-the-Skies/releases), donde encontrarás:
     - `Amy_Beyond_the_Skies_animaciones_v3_corregido.capx` (Proyecto integrado listo para Construct 2)
     - `Amy_actual_v3_1.zip` (Proyecto v3.1, animaciones v3, acceso de apertura e informes de validación)
     - Los paquetes de animaciones y recursos v2 permanecen en las publicaciones anteriores.
3. **Quiero descargar todo el repositorio (proyecto, imprimibles, catálogos HTML, música, videos y portadas):**
   - Arriba a la derecha en esta página de GitHub, haz clic en el botón verde **`<> Code`** y selecciona **`Download ZIP`**. Luego descomprime la carpeta en tu PC.

> [!IMPORTANT]
> **Consejo antes de editar en Construct 2:** Parte siempre de **`Proyecto/Amy_Beyond_the_Skies_animaciones_v3_corregido.capx`** y guarda una copia de respaldo antes de hacer cambios. Los archivos dentro de `Proyecto_Original/` se conservan como referencia histórica de las primeras entregas del equipo.

---

## 🖼️ 2. Vista previa del Menú y Catálogo de Animaciones v2

| Menú Principal Animado | Catálogo de Sprites y Efectos v2 |
|:---:|:---:|
| ![Menú Principal de Amy](Menu_Animado/Amy_Beyond_the_Skies_menu.png) | ![Catálogo de Animaciones v2](Animaciones_v2/Catalogo_cielo.png) |

💡 *Al descargar el repositorio, puedes abrir en tu navegador [`Animaciones_v2/Vista_previa.html`](Animaciones_v2/Vista_previa.html) para probar en vivo las animaciones cuadro por cuadro y escuchar los efectos de sonido.*

---

## 🎮 3. Mecánicas y Controles del Juego

- **Ventana del proyecto:** `320 × 700` píxeles (diseño vertical de ascenso continuo).
- **Controles:**
  - **Flechas Izquierda / Derecha (`←` / `→`):** Mover a Amy en el aire hacia las plataformas.
  - **Cruce de bordes laterales:** Si sales por el borde izquierdo de la pantalla, reapareces por el derecho (y viceversa).
  - **Salto automático:** Al aterrizar sobre una plataforma lavanda (`Platform`), Amy rebota automáticamente hacia arriba para seguir subiendo.
- **Inicio y Meta de la Demo:**
  - Al iniciar el nivel se muestra el cartel **«¡Vamos, Amy!»** (`inicio_vamos_amy.png`).
  - Al aterrizar sobre la plataforma del **Portal de Llegada** (`portal_llegada.png`) en la cima de la demo, se activan los destellos de victoria y el panel **«¡Demo completada!»** (`final_demo_completada.png`) con opciones para volver a jugar o ir al menú.

---

## 🛠️ 4. Guía Técnica para Construct 2 (Hojas de Sprites y Sonidos v2)

### A. Hoja de Personaje (`amy_movimiento_3x4.png`)
Ubicada en [`Animaciones_v2/Assets/Personaje/amy_movimiento_3x4.png`](Animaciones_v2/Assets/Personaje/amy_movimiento_3x4.png).
- **Dimensiones totales:** `1086 × 1448 px` dividida en **3 columnas × 4 filas** (12 celdas exactas de **`362 × 362 px`**).
- **Cómo se usa en Construct 2:** El objeto `Player` original conserva la física (`Platform`) y las colisiones (invisible), mientras que el sprite `AmyVisual` muestra las animaciones siguiendo los pies del jugador:

| Animación en Construct 2 | Fila de la hoja | Fotogramas (índices globales) | Velocidad sugerida | Loop |
|---|:---:|:---:|:---:|:---:|
| `impulso` | Fila 1 | `0, 1, 2` | 16 fps | No |
| `ascenso` | Fila 2 | `3, 4, 5` | 8 fps | No |
| `caida` | Fila 3 | `6, 7, 8` | 8 fps | No |
| `aterrizaje` | Fila 4 | `9, 10, 11` | 16 fps | No |
| `quieta` *(opcional)* | Fila 4 | Solo `11` | 0 fps | No |

📌 *Los puntos de origen exactos (`X, Y`) medidos al pie de cada fotograma están en [`Animaciones_v2/ORIGENES_PERSONAJE.csv`](Animaciones_v2/ORIGENES_PERSONAJE.csv).*

### B. Hoja de Efectos Visuales (`efectos_4x3.png`)
Ubicada en [`Animaciones_v2/Assets/Efectos/efectos_4x3.png`](Animaciones_v2/Assets/Efectos/efectos_4x3.png).
- **Dimensiones totales:** `1448 × 1086 px` dividida en **4 columnas × 3 filas** (celdas de **`362 × 362 px`**):
  - **Fila 1 (`fx_impulso`, frames 0–3, 16 fps):** Polvo al iniciar el salto en los pies.
  - **Fila 2 (`fx_aterrizaje`, frames 4–7, 16 fps):** Impacto suave sobre la plataforma al tocarla.
  - **Fila 3 (`fx_victoria`, frames 8–11, 12 fps):** Destellos mágicos al llegar al portal de meta.

---

## 🖨️ 5. Materiales Imprimibles para el Stand Escolar (`Imprimibles_Amy/`)

Todos los materiales promocionales del equipo están listos en formato **PDF A4** (imprimir al 100 % sin escalar):

| Material | Archivo PDF listo para imprimir (A4) | Vista previa / Contenido |
|---|---|---|
| **1. Plancha de Stickers (v1)** | [`Paquete_Stickers_Amy_Beyond_the_Skies_A4_v1.pdf`](Imprimibles_Amy/01_Stickers/Imprimir/Paquete_Stickers_Amy_Beyond_the_Skies_A4_v1.pdf) | 9 stickers por hoja A4 con 3 motivos exclusivos: **Amy Explorando**, **Amy Pulgar Arriba** y **Amy Señalando**. [Ver vista previa](Imprimibles_Amy/01_Stickers/Vista_previa/Plancha_A4_v1.png) |
| **2. Manual de Juego Cuadernillo (v1)** | [`Manual_Amy_Beyond_the_Skies_Cuadernillo_A4_v1.pdf`](Imprimibles_Amy/02_Manual_de_Juego/Imprimir/Manual_Amy_Beyond_the_Skies_Cuadernillo_A4_v1.pdf) · [Versión Digital](Imprimibles_Amy/02_Manual_de_Juego/Digital/Manual_Amy_Beyond_the_Skies_12x18_v1.pdf) | Librito de 4 páginas (12 × 18 cm) con portada, controles, objetivo y consejos ilustrados. [Leer instrucciones de plegado](Imprimibles_Amy/02_Manual_de_Juego/LEEME.md) |
| **3. Portada Promocional 12×18 (v1)** | [`Portada_Amy_Beyond_the_Skies_12x18_A4_v1.pdf`](Imprimibles_Amy/03_Portada_Imprimible/Imprimir/Portada_Amy_Beyond_the_Skies_12x18_A4_v1.pdf) · [Digital](Imprimibles_Amy/03_Portada_Imprimible/Digital/Portada_Amy_Beyond_the_Skies_PC_Demo_v1.png) | Portada para caja o exhibidor del stand lista para recortar a 12 × 18 cm. [Leer guía](Imprimibles_Amy/03_Portada_Imprimible/LEEME.md) |

---

## 📚 6. Documentación del equipo en Office

Los tres archivos editables están juntos en [`Documentacion/`](Documentacion/), con sus nombres actuales:

| Archivo | Para qué sirve | Descarga directa |
|---|---|---|
| [GDD Amy.docx](Documentacion/GDD%20Amy.docx) | Diseño del juego con explicaciones sencillas, imágenes, organización del grupo, bitácora y pruebas pendientes. | [Descargar Word](https://github.com/hfreedo/Amy-Beyond-the-Skies/raw/refs/heads/main/Documentacion/GDD%20Amy.docx) |
| [Inventario Amy.xlsx](Documentacion/Inventario%20Amy.xlsx) | Catálogo visual de los assets, con nombres, descripciones y cinco audios incrustados. | [Descargar Excel](https://github.com/hfreedo/Amy-Beyond-the-Skies/raw/refs/heads/main/Documentacion/Inventario%20Amy.xlsx) |
| [Guía Amy.pptx](Documentacion/Gu%C3%ADa%20Amy.pptx) | Presentación para explicar los controles y las partes del juego. | [Descargar PowerPoint](https://github.com/hfreedo/Amy-Beyond-the-Skies/raw/refs/heads/main/Documentacion/Gu%C3%ADa%20Amy.pptx) |

Para escuchar los audios del inventario, abrir el archivo en Excel de escritorio para Windows y hacer doble clic en el icono de cada sonido. Para recorrer la guía, iniciar la presentación con diapositivas en PowerPoint. En el GDD quedan espacios para completar los integrantes, las tareas y la bitácora del grupo.

Estos documentos también se incluyen al descargar el repositorio completo mediante **Code → Download ZIP**.

---

## 📂 7. Estructura de carpetas del repositorio

```text
Amy-Beyond-the-Skies/
├── Documentacion/                                 # Documentos editables para el equipo y la exposición
│   ├── GDD Amy.docx                               # Diseño, organización y bitácora del grupo
│   ├── Inventario Amy.xlsx                        # Assets visuales y cinco audios incrustados
│   └── Guía Amy.pptx                              # Presentación de controles y reglas
├── Proyecto/                                       # Versión vigente integrada
│   ├── Amy_Beyond_the_Skies_animaciones_v3_corregido.capx      # ⭐ Archivo principal para abrir en Construct 2
│   └── INSTRUCCIONES_PARA_IA.md                    # Guía paso a paso de configuración y eventos
├── Proyecto_Original/                              # Versiones iniciales de referencia de los alumnos
│   ├── amy.capx                                    # Prototipo original de salto
│   └── amy_con_menu.capx                           # Primera versión con menú incorporado
├── Imprimibles_Amy/                                # 🖨️ Materiales listos para imprimir en A4
│   ├── 01_Stickers/                                # Plancha de stickers coleccionables (3 poses)
│   ├── 02_Manual_de_Juego/                         # Manual cuadernillo A4 (4 páginas plegables)
│   └── 03_Portada_Imprimible/                      # Carátula 12x18 cm en A4 y PNG digital
├── Animaciones_v2/                                 # Kit de animaciones corregidas v2 y vistas HTML
│   ├── Assets/                                     # Sprites 3x4, efectos 4x3, carteles, portal y audio
│   ├── ORIGENES_PERSONAJE.csv                      # Coordenadas exactas de origen por fotograma
│   ├── Vista_previa.html                           # Visor interactivo de animaciones y sonidos
│   └── Revision_rodillas.html                      # Comparativa de corrección anatómica del sprite v2
├── Assets_Menu_y_Juego/                            # Biblioteca completa de imágenes separadas (Menú y Nivel)
├── Menu_Animado/                                   # Video MP4 del menú, capturas y pistas de música MP3
└── Portadas/                                       # Ilustraciones promocionales de portada en alta calidad
```
