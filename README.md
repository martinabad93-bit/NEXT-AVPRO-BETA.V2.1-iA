# NEXT GB AUTO IMPORT --- V3.75 ESTABILIZACIÓN

## Corrección de estabilización

Esta versión se limita a los problemas solicitados para el flujo final:

1.  Último paso reducido al resultado real de la importación.
2.  Cotización y Proforma impresas como documentos independientes, sin
    imprimir la aplicación.
3.  Numeración independiente para Cotización (`NGQ`) y Proforma (`NGP`).
4.  Con VIN: últimos 6 caracteres.
5.  Sin VIN: secuencia desde `2610`.

------------------------------------------------------------------------

## 1. Último paso --- TU IMPORTACIÓN ESTÁ LISTA

Al finalizar la cotización, la aplicación presenta solamente el
resultado comercial:

-   Vehículo.
-   Inversión total / Landed Cost.
-   Precio de venta.
-   Ganancia estimada.
-   ROI / Margen.
-   Acciones:
    -   Presentar cotización.
    -   PDF.
    -   Imagen.
    -   WhatsApp.

Se oculta el `final-main-grid`, que contenía los desgloses extensos de
costos, placa, pagos, análisis comercial y demás información interna.

También se oculta el pie de información de la vista final.

**No se modifican los cálculos para conseguir este resultado.**

------------------------------------------------------------------------

## 2. PDF --- CORRECCIÓN DE RAÍZ

### Problema anterior

La aplicación intentaba imprimir desde el contexto de la página
principal mediante elementos de impresión internos/iframes. En
Chrome/Brave esto podía provocar:

-   Página de la aplicación.
-   Páginas adicionales.
-   Documento de Cotización o Proforma al final.

### Solución actual

La función `window.imprimirPDF()` ya no imprime desde el DOM de la
aplicación.

Ahora:

1.  Determina `Cotización` o `Proforma`.
2.  Construye exclusivamente el documento solicitado.
3.  Abre una ventana independiente.
4.  Escribe en esa ventana un HTML completamente independiente.
5.  Incluye únicamente los estilos necesarios para el documento.
6.  Ejecuta `print()` dentro de esa ventana.
7.  Reserva el siguiente número solamente cuando se inicia la impresión.
8.  Cierra la ventana después del proceso.

Por diseño, la ventana de impresión no contiene:

-   Formularios.
-   Tabs.
-   Live Cost.
-   IA.
-   Menús.
-   Botones de la aplicación.
-   Pantalla final.
-   Otros documentos.

### Resultado esperado

**Cotización → solamente Cotización.**

**Proforma → solamente Proforma.**

La página web principal no forma parte del documento que se imprime.

------------------------------------------------------------------------

## 3. Numeración

### Cotización

Prefijo:

`NGQ`

Sin VIN:

-   `NGQ-2610`
-   `NGQ-2611`
-   `NGQ-2612`
-   etc.

### Proforma

Prefijo:

`NGP`

Sin VIN:

-   `NGP-2610`
-   `NGP-2611`
-   `NGP-2612`
-   etc.

Las secuencias son independientes:

-   `nextgb_cotizacion_seq`
-   `nextgb_proforma_seq`

------------------------------------------------------------------------

## 4. VIN

Si existe un VIN de al menos 6 caracteres:

### Cotización

`NGQ-XXXXXX`

### Proforma

`NGP-XXXXXX`

`XXXXXX` corresponde a los últimos 6 caracteres del VIN en mayúsculas.

Si no existe VIN válido, se utiliza la secuencia correspondiente.

------------------------------------------------------------------------

## 5. Reglas de estabilización

No se modifican en esta corrección:

-   Cálculos de subasta.
-   Cálculos de aduana.
-   Primera placa.
-   IA.
-   Base de datos.
-   Fees.
-   Navegación.
-   WhatsApp.
-   Generación de imagen.

La prioridad es estabilizar:

**ÚLTIMO PASO + PDF + PROFORMA + NUMERACIÓN.**

------------------------------------------------------------------------

## 6. Validación técnica realizada

Sobre `index.html`:

-   19 bloques `<script>` detectados.
-   19/19 bloques pasan `node --check`.
-   Una única implementación de `window.imprimirPDF`.
-   Una única llamada a `.print()` dentro de la implementación de
    impresión.
-   La impresión utiliza una ventana independiente.
-   La vista final oculta explícitamente el bloque `final-main-grid`.

------------------------------------------------------------------------

## 7. Prueba real requerida en Chrome/Brave

### Cotización sin VIN

Primera ejecución:

`NGQ-2610`

Segunda:

`NGQ-2611`

Debe aparecer solamente el documento de Cotización.

### Proforma sin VIN

Primera ejecución:

`NGP-2610`

Segunda:

`NGP-2611`

Debe aparecer solamente el documento Proforma.

### Con VIN

Ejemplo de VIN terminado en:

`123456`

Cotización:

`NGQ-123456`

Proforma:

`NGP-123456`

### Último paso

Debe aparecer únicamente la pantalla:

**TU IMPORTACIÓN ESTÁ LISTA**

con los resultados comerciales y sus acciones.

------------------------------------------------------------------------

## Archivos de esta versión

-   `index.html` --- aplicación V3.75 corregida.
-   `README.md` --- documentación de V3.75.

## Estado

**V3.75 --- ESTABILIZACIÓN**

No continuar con nuevas funcionalidades hasta validar estos cuatro
puntos en Chrome/Brave:

1.  Último paso limpio.
2.  Cotización aislada.
3.  Proforma aislada.
4.  Numeración NGQ/NGP correcta.
