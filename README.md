# Resonancia Magnética: de los protones a la imagen — V37

Versión de estabilización técnica preparada a partir de la V36 y probada en Codex. Los archivos de la aplicación son los mismos que los de la V37 preparada en esa sesión; no es una segunda implementación.

## Descargar y abrir

1. En esta página de GitHub, pulsa el botón **Code** y después **Download ZIP**.
2. En Windows, pulsa con el botón derecho sobre el ZIP descargado y elige **Extraer todo**.
3. Abre `index.html` desde la carpeta extraída. Conserva junto a él `portada.png`, el segundo HTML y la carpeta `imagenes`.

No se necesita instalar paquetes para usar la aplicación. Todos sus recursos están incluidos localmente.

## Cambios y comprobaciones

Consulta [el informe V37](INFORME_V37.md) y [las instrucciones](LEEME_V37.txt). Las ocho correcciones solicitadas están aplicadas, conservando los contenidos docentes, preguntas e imágenes. Solo se modificaron los dos HTML de la aplicación original.

Se comprobaron en Chromium navegación, cuestionarios, controles, animaciones, seis tamaños de pantalla y fallos simulados de almacenamiento. Los registros `PRUEBAS_V37.json` y `PRUEBAS_ADICIONALES_V37.json` contienen las evidencias. `MANIFIESTO_V37.sha256` identifica los 93 archivos de la entrega original de V37.

**Pendiente:** apertura directa desde disco (`file://`) en Windows, Safari, Firefox y móviles físicos. El entorno de pruebas bloqueaba `file://`; los recorridos funcionales se probaron mediante servidor local, con peticiones externas bloqueadas. No se certifican aquí esas modalidades pendientes.

El ZIP original V36 permanece intacto en el entorno de preparación y en la copia aportada por el usuario; no se ha incluido otra copia de ese ZIP en este repositorio.
