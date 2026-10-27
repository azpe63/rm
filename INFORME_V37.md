# V37 — Estabilización técnica de Resonancia Magnética

Fecha: 27 de octubre de 2026.
Base: RM36.zip facilitado por el usuario. La V36 permanece intacta y se entrega como RM36_respaldo.zip.

## Resultado y alcance

Se han aplicado las ocho correcciones solicitadas mediante cambios localizados. Solo se han modificado dos archivos de la aplicación: `index.html` y `Laboratorio_RM_Espines_RF.html`. Se añaden instrucciones y este informe. No se han reorganizado los capítulos, sustituido las imágenes, alterado el contenido científico, modificado las preguntas ni incorporado dependencias.

Las pruebas descritas más abajo han pasado en Chromium. La apertura directa por `file://`, Safari, Firefox y dispositivos móviles físicos siguen pendientes; no se certifican como probados.

## Modificaciones

1. **Vector del laboratorio general de RF.** Se recentran los ejes y se reduce el radio de dibujo dentro del mismo canvas. El recorrido de 0° a 180° cabe en su altura. Se conservan las expresiones, cálculos, textos y colores. Se verificaron los extremos de los trazos en los 181 ángulos enteros y se inspeccionó una captura a 180°.
2. **Deslizadores de los laboratorios generales.** Al cambiar un valor se mantienen los elementos del laboratorio: se actualizan los resultados, la explicación y el canvas. Los controles solo se crean al abrir o cambiar de laboratorio. Se preservan sus rangos, pasos y etiquetas. El arrastre continuo ya no sustituye el elemento que está recibiendo el movimiento.
3. **Laboratorio del capítulo 3.** Se conserva la distribución lateral de animación y curvas cuando el ancho interno lo permite. El documento del laboratorio comunica su altura al capítulo mediante mensajes locales; el receptor valida que el mensaje procede del iframe correspondiente. La altura se ajusta después de cargar y al cambiar el tamaño del contenido. No se consulta ningún servicio externo. La comunicación evita depender de acceder directamente al DOM del iframe, pero su funcionamiento al abrir archivos desde disco queda pendiente de prueba real.
4. **Pantallas estrechas.** Las métricas y los botones de etapas se redistribuyen cuando el ancho interno es inferior a 360 píxeles. Se conserva todo el contenido y se evita el desbordamiento horizontal.
5. **Navegación del capítulo 3.** Se actualiza la variable de estado utilizada por el resto de la aplicación y se utiliza el mecanismo existente de navegación. Se elimina la selección por posición que resaltaba «Glosario y fuentes». La corrección también evita que esa selección equivocada quede persistente al pasar después a otro capítulo.
6. **Bienvenida de Reso.** El panel no se encoge y se alinea de forma segura; cuando la altura es limitada, su contenido empieza en una posición accesible y se puede desplazar hasta el botón de continuación. Se mantienen la ilustración, los textos y la identidad visual.
7. **Marcador temporal en relajación.** Se añade una línea vertical discontinua y un punto en cada curva T1 existente, en el instante elegido. Se mantienen las fórmulas, los tejidos y las explicaciones de V36. No se añade un modelo T2 nuevo.
8. **Almacenamiento tolerante a fallos.** Se protegen tanto las operaciones de progreso con `localStorage` como las de bienvenida con `sessionStorage`. Si no se puede guardar el progreso, permanece en memoria durante esa apertura y se permite continuar. Si el almacenamiento funciona, el progreso sigue persistiendo tras recargar. Cuando el almacenamiento está bloqueado, no se promete persistencia después de cerrar o recargar.

## Pruebas ejecutadas y superadas

### Navegación y conservación

- Recorrido de los once capítulos a 320, 375, 768, 1024, 1366 y 1920 píxeles de ancho, sin desbordamiento horizontal del documento principal en las comprobaciones realizadas.
- Comparación del texto visible de los once capítulos: coincide con V36.
- Comparación de los datos docentes y bancos `DATA`, `v9Questions` y `v19Qs`: coinciden con V36. La sección y las preguntas del capítulo 3 no se han editado; su cuestionario se ejecutó hasta el resultado final.
- Comparación píxel a píxel de la captura inicial del contenido principal, a 1366 × 900: coincide en los once capítulos. Es una comparación de la vista inicial, no de todos los estados y posiciones de desplazamiento. Se excluye el lateral, donde se corrige la selección errónea.
- Todos los recursos y documentos originales distintos de los dos HTML modificados siguen siendo idénticos byte a byte. No se eliminó ningún archivo de V36.
- La copia de V36 utilizada como referencia sigue siendo idéntica a los 91 archivos del ZIP original.

### Cuestionarios y Reso

- Capítulo 1: recorrido de sus 8 preguntas y retroalimentación correcta.
- Capítulo 2: resultado 5/5, repetición y nueva respuesta después del reinicio.
- Capítulo 3: resultado 10/10, repetición y retroalimentación de una respuesta incorrecta con Reso.
- Autoevaluación general: sus 24 opciones configuradas como correctas fueron reconocidas.
- Se conservaron los mecanismos y textos de corrección; estas pruebas no son una nueva validación científica de las claves de respuesta.

### Laboratorios y controles

- Nueve deslizadores de los laboratorios generales: arrastre real con ratón hasta más del 80 % del recorrido, conservación del mismo elemento DOM y teclas Inicio/Fin para alcanzar ambos extremos.
- RF: 181 ángulos enteros entre 0° y 180°, con los extremos de los trazos dentro del canvas. Inspección visual de la captura a 180°.
- Relajación: variar únicamente el tiempo cambia el gráfico por la aparición/movimiento del marcador.
- Los seis laboratorios generales actualizan su canvas con los controles correspondientes.
- Laboratorio de seis espines: acceso a las cinco etapas, reproducción, pausa, reinicio y cambios de la línea temporal. A 30 % muestra Mz = 0 % y Mxy = 100 %; tras reiniciar muestra Mz = 100 % y Mxy = 0 %.
- Larmor del capítulo 2: actualización de su control y frecuencia; el recorrido funcional comprobó 127,74 MHz a 3 T.

### Adaptación del laboratorio incrustado

| Ancho exterior | Ancho interno | Altura útil del iframe | Disposición |
| --- | --- | --- | --- |
| 320 px | 266 px | 2134 px | Apilada |
| 375 px | 321 px | 1798 px | Apilada |
| 768 px | 668 px | 1529 px | Apilada |
| 1024 px | 704 px | 1484 px | Apilada |
| 1366 px | 1020 px | 881 px | Lateral |
| 1920 px | 1350 px | 857 px | Lateral |

En esas mediciones, el documento interno cabe en el ancho y alto del iframe, sin necesitar desplazamiento interno adicional. En móvil se desplaza la página principal para recorrer el laboratorio completo. Las alturas pueden cambiar con el navegador y sus fuentes.

Se verificaron también la accesibilidad del comienzo de la bienvenida de Reso y la posibilidad de desplazarse hasta su botón y cerrarla en esos tamaños. Son ventanas simuladas en Chromium, no teléfonos físicos.

### Almacenamiento, sintaxis y red

- Navegación y progreso en memoria con acceso a `localStorage` y `sessionStorage` bloqueado mediante una simulación de `SecurityError`.
- Navegación y progreso en memoria con lectura permitida y escritura rechazada mediante una simulación de `QuotaExceededError`.
- Persistencia normal del progreso después de recargar.
- Comprobación de sintaxis de todos los bloques JavaScript de los dos HTML mediante Node.js.
- Sin excepciones de JavaScript, respuestas HTTP de error ni peticiones externas en las suites que registran esos eventos.
- Ejecución servida exclusivamente desde el equipo local, con peticiones a destinos externos bloqueadas. Esto verifica los recorridos ensayados sin Internet, sin recurrir a recursos remotos.

El registro técnico contiene 90 comprobaciones principales y 40 adicionales superadas. Incluye comprobaciones de sintaxis, integridad y conservación, además de pruebas funcionales; no representa 130 recorridos completos de usuario independientes.

## Comprobaciones pendientes y límites

1. **Apertura directa con doble clic (`file://`).** El navegador administrado de este entorno bloquea ese protocolo con `ERR_BLOCKED_BY_ADMINISTRATOR`. No se ha desactivado esa política. Es necesario probar la apertura local real, especialmente el ajuste del iframe y la persistencia de progreso.
2. **Safari, Firefox y dispositivos móviles físicos.** No probados. Verificar arrastre táctil, bienvenida, fuentes y mensajes de ajuste de altura del iframe.
3. **Zoom, tamaños de letra del sistema y accesibilidad completa.** No se ha efectuado una auditoría exhaustiva de esos escenarios.
4. **Todos los estados visuales de todos los capítulos.** Las comparaciones automáticas abarcan textos y vistas iniciales, y las pruebas funcionales descritas. No equivalen a inspeccionar cada figura a cada escala ni cada combinación de parámetros.
5. **Rendimiento en equipos de estudiantes.** No se certifican tiempos de carga o fluidez en hardware real de baja potencia.

No se han abordado la reorganización global del código, la unificación de bancos de preguntas, la compresión de imágenes ni otros cambios de alcance mayor. Continúa siendo recomendable aplicar futuros cambios de forma localizada y repetir las comprobaciones de regresión.

## Archivos de entrega

- `RM37.zip`: aplicación completa, con todos los recursos locales, las instrucciones V37 y este informe.
- `RM36_respaldo.zip`: copia exacta del archivo original aportado.
- `INFORME_V37.md`: este informe, también disponible fuera del ZIP.
- `PRUEBAS_V37.json` y `PRUEBAS_ADICIONALES_V37.json`: evidencias técnicas de las comprobaciones.

Para utilizar la aplicación, extraer completamente el ZIP y conservar juntos los HTML, `portada.png` y la carpeta `imagenes`. El modo previsto es abrir `index.html`; esa modalidad directa requiere la verificación pendiente descrita arriba. Como alternativa sin Internet, si ya se dispone de Python, se puede ejecutar `python -m http.server 8000 --bind 127.0.0.1` desde la carpeta extraída y abrir el índice en el navegador local. No se necesita instalar paquetes para ello.
