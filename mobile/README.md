# NEXT GB AUTO IMPORT — MOBILE V3.75
## PDF Cotización y Factura Proforma — alineación con Desktop

### Corrección aplicada

Se alineó la sección de documentos PDF de Mobile V3.75 con la estructura utilizada en Desktop para **Cotización** y **Factura Proforma**.

### Cotización

El documento mantiene:

- Encabezado NEXT GB AUTO IMPORT / SRL · ELITE.
- Tipo de documento: COTIZACIÓN.
- Vehículo, VIN y tasa DOP.
- Inversión y costos.
- FOB Miami.
- Flete marítimo.
- Paquete despacho / puerto RD.
- Despacho Aduanal / Impuestos.
- Reparación en RD.
- Total Despacho Sin Placa.
- Sección **EMISIÓN DE PLACA & ENDOSO**.
- Normativa 03-25.
- Placa Provisional.
- Gestión de Endoso.
- Primera Placa (17%).
- CO₂ & Marbete.
- Total Emisión de Placa.
- Costo Total Landed.
- Rentabilidad, precio de venta, margen y ROI.

### Factura Proforma

Mantiene la misma estructura de costos y agrega el cronograma:

1. Depósito de Seguridad.
2. Balance Subasta.
3. Logística Origen.
4. Aduanas y Flete.
5. Emisión de Primera Placa.

El Pago 5 utiliza el total completo de emisión de placa y no incluye reparación en RD.

### Sincronización de placa

El documento utiliza el mismo cálculo de la operación Mobile:

**Primera Placa + CO₂ + Marbete + Normativa 03-25 + Placa PP + Gestión de Endoso**

El Total Emisión de Placa no se calcula como únicamente PP + Gestión.

### Impresión

Se conserva el sistema de documento dedicado de Mobile V3.75 para que el PDF imprima el documento generado y no la interfaz completa de la aplicación.

### Validación

- 20 bloques JavaScript revisados.
- 0 errores de sintaxis.
- No se modificaron cálculos ajenos a Cotización/Proforma.
- Se mantiene la estabilización de IA de V3.75.
- Se mantiene la navegación y sincronización existente.

## Archivo

`index (1).html` — NEXT GB MOBILE V3.75 con PDF Cotización/Proforma alineado con Desktop.


## Corrección adicional — PDF en Mobile V3.75

Se corrigió el problema por el cual al imprimir PDF el navegador incluía las páginas de la aplicación antes del documento.

### Causa
La impresión utilizaba `window.print()` sobre la página principal y dependía del CSS para ocultar la aplicación. El navegador podía conservar parte del contenido de las tres vistas de Mobile y agregarlas antes de la Cotización/Proforma.

### Solución
`imprimirPDF()` ahora:
1. Genera únicamente el documento seleccionado.
2. Crea un iframe de impresión aislado.
3. Inserta dentro del iframe solamente el documento y sus estilos.
4. Ejecuta `print()` dentro del iframe.
5. Elimina el iframe después de la impresión.

### Resultado esperado
- Cotización: solo las páginas de la Cotización.
- Proforma: solo las páginas de la Proforma.
- No deben aparecer las tres páginas de la aplicación antes del documento.

Validación: 20 bloques JavaScript revisados, 0 errores de sintaxis.
