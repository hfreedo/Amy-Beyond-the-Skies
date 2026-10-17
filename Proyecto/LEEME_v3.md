# Amy: animaciones v3 corregidas

## Abrir el juego

Desde el Explorador de archivos de Windows, ejecutar **ABRIR_AMY.cmd** o abrir **Amy_Beyond_the_Skies_animaciones_v3_corregido.capx** con Archivo > Abrir en Construct 2.

No abrir el CAPX mediante una dirección que empiece por `C:/`. En esta instalación de Construct 2 esa forma de ruta produjo “Unknown error loading project”, incluso con el autosave original y proyectos de diagnóstico sin eventos. El mismo CAPX abrió con la ruta normal de Windows `C:\...`. El acceso ABRIR_AMY.cmd utiliza esa ruta de Windows.

## Cambios

- Animaciones transparentes de impulso, ascenso y caída a partir del GIF de saltitos.
- Festejo completo únicamente al aterrizar sobre la plataforma del portal; el panel de victoria aparece al terminar.
- Tras caer por debajo de la pantalla, Amy vuelve con globos a la plataforma segura y retoma el salto automático.
- Se conserva cámara, progreso y plataforma de regreso durante el rescate.
- Referencia inicial del controlador físico ajustada a `quieta`, que sí existe.
- Evitada la doble activación de pausa/reanudación con una sola pulsación de P o Escape.
- Sin plataformas duplicadas durante el rescate.

## Validación

Se abrió este CAPX en Construct 2 y se ejecutó su preview real. Las 22 comprobaciones de `verificacion_runtime.json` pasaron: menú, animaciones según velocidad vertical, pausa/reanudación, rescate, conservación de progreso, reposicionamiento, festejo y victoria sin errores JavaScript. Para reproducir los casos de caída y llegada se reposicionaron objetos en el motor durante la prueba. No fue una partida manual completa.

Los archivos PNG y las capturas están en esta carpeta. Las versiones anteriores y los GIF originales se conservaron. Usar el archivo terminado en **v3_corregido.capx** para estas mejoras.
