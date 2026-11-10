# FC Formularios V4 — RELMA

## Contenido
- `index.html`: aplicación completa con las funciones originales y mejoras integradas.
- `app.css` / `app.js`: interfaz adaptable, panel principal, importación desde carpeta/JSON, administración de fórmulas, búsqueda mejorada, comparación RGB perceptual, controles PWA y consulta móvil.
- `dymo.connect.framework.js`: biblioteca DYMO proporcionada para conectar con DYMO Connect en PC.
- `manifest.webmanifest`, `sw.js`, `icons/`: instalación como aplicación web (PWA) y caché de archivos principales.

## Publicación e instalación
La PWA debe publicarse mediante HTTPS (por ejemplo, GitHub Pages). No se instala correctamente abriendo `index.html` con doble clic (`file://`). Sube **todos los archivos y carpetas** de este paquete al repositorio manteniendo la estructura.

- Windows: abre la URL con Chrome o Edge y usa el icono Instalar de la barra de direcciones o el menú del navegador.
- Android: abre la URL con Chrome y selecciona Instalar aplicación / Añadir a pantalla principal.
- iPhone: abre la URL en Safari → Compartir → Añadir a pantalla de inicio.

## Base de datos
- En PC compatible: `Seleccionar carpeta` usa el selector de carpetas del navegador (Chrome/Edge en contexto seguro). La carpeta puede contener varios JSON de catálogo, también dentro de subcarpetas.
- También se puede elegir un archivo `.json` desde el explorador de archivos.
- En Android/iPhone se recomienda elegir el archivo JSON desde el selector de archivos. El acceso persistente directo a una carpeta depende del navegador y del sistema.
- La importación combina fórmulas por código + base + línea + marca. No sustituye fórmulas de fabricantes distintos que compartan código.
- Los datos se mantienen en el almacenamiento local de cada navegador/dispositivo y se respaldan adicionalmente en IndexedDB. **No hay sincronización automática entre equipos ni con Google Drive en esta entrega**. Para otro equipo, importa el mismo JSON allí.

## DYMO
- Impresión habilitada únicamente en PC/Mac con DYMO Connect instalado, servicio de impresión en ejecución, impresora conectada y navegador compatible.
- La biblioteca JavaScript de DYMO está incluida localmente.
- En celulares, la fórmula y vista previa son consultables; el botón de impresión queda oculto/deshabilitado.
- DYMO requiere software de escritorio instalado; la PWA móvil no sustituye ese componente.
- La rutina conserva la etiqueta original del proyecto. Plantillas DYMO personalizadas se intentan abrir desde Configuración; verifica nombres de objetos y medidas antes de producción.

## Importante antes del primer uso
1. Haz una copia de seguridad JSON de los datos actuales.
2. Publica esta carpeta completa por HTTPS.
3. En PC instala/abre DYMO Connect y verifica que la LabelWriter 450 aparezca en Windows.
4. Prueba primero con una etiqueta de prueba y confirma el tamaño físico, márgenes y legibilidad de la DYMO.
5. Importa el catálogo JSON original y comprueba algunas fórmulas conocidas comparándolas con el sistema anterior.

## Notas técnicas
- La lectura de PDF continúa usando PDF.js desde CDN; la primera importación de PDF requiere conexión a Internet.
- La app es PWA, no un APK ni una app nativa publicada en Google Play / App Store. En la primera visita se descargan los archivos principales para habilitar la apertura offline; el importador de PDF necesita que PDF.js se haya cargado desde CDN al menos una vez.
- Los resultados RGB usan distancia CIELAB Delta E 1976 como orden de cercanía aproximada; la igualación real depende de la pintura, la base, la iluminación y la calibración.
- Los cálculos y reglas de dosificación preexistentes se conservaron para evitar cambiar resultados sin una tabla patrón de validación de la sucursal.
