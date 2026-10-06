# NEXT-AVPRO-BETA.V2.0

## Versión
**NEXT-AVPRO-BETA.V2.0 — estabilización móvil**

## Fecha
06 de octubre de 2026

## Objetivo de esta actualización
Estabilizar la arquitectura móvil y evitar que la navegación entre pasos convierta la aplicación en una página de desplazamiento vertical o vuelva a mostrar el layout Desktop.

## Cambios aplicados

### 1. Navegación controlada por pasos
- Paso 01 → Paso 02 mediante **Continuar a Aduanas**.
- Paso 02 → Paso 03 mediante **Continuar a Inversión**.
- Cada paso se trata como una vista independiente.
- Se aplica una transición visual tipo slide, no un `scrollIntoView()` para avanzar.
- El usuario conserva control para regresar a pasos desbloqueados.

### 2. Layout móvil
- En iPhone se fuerza una sola columna.
- El panel Desktop `Live Cost Preview` queda oculto durante el flujo normal móvil.
- El panel de resultados solo aparece en la vista final.
- Se evita el desbordamiento horizontal.

### 3. PDF / Cotización / Proforma
Se corrigió un problema en el que el botón PDF podía imprimir la página/pestaña actual.

Ahora el botón PDF construye un **documento independiente de impresión** antes de llamar al diálogo de impresión del navegador.

- **Cotización:** documento independiente con inversión, FOB Miami, Despacho Sin Placa, Emisión de Placa, Landed y rentabilidad.
- **Factura Proforma:** documento independiente con el cronograma completo de 5 pagos y Total Inversión (Landed).
- No se imprime el formulario actual de la aplicación.

### 4. Estructura de costos conservada
- FOB Miami = operación completa en Miami.
- Total Despacho Sin Placa = FOB Miami + Flete + Paquete de Despacho + Aduanas/Impuestos convertidos a USD.
- Paquete de Despacho = US$465 por defecto.
- Honorarios = campo manual en USD.
- Normativa 03-25 = RD$0 por defecto y manual.
- Placa PP = RD$2,000.
- Gastos de Endoso / Gestión = RD$5,000.

### 5. Proforma
Se mantiene obligatoriamente:
1. Pago 1 — Depósito de Seguridad
2. Pago 2 — Balance Subasta
3. Pago 3 — Logística Origen
4. Pago 4 — Aduanas y Flete
5. Pago 5 — Placa y Endoso
6. Total Inversión (Landed)

## Correcciones
- Evitado el retorno accidental al layout Desktop al cambiar de paso en móvil.
- Evitado el desplazamiento automático como mecanismo de navegación del wizard.
- Evitado que PDF imprima la pestaña actual.
- Se mantiene el documento formal separado de la interfaz de cálculo.

## Base de datos
Se incluye:
`mobile/Base de Datos Valores Vehiculos 2026 - 2027.csv`

## Estructura
```text
NEXT-AVPRO-BETA.V2.0-GITHUB/
├── README.md
└── mobile/
    ├── index.html
    └── Base de Datos Valores Vehiculos 2026 - 2027.csv
```

## Validación
- 17 bloques JavaScript inspeccionados.
- 0 errores de sintaxis con `node --check`.
- La versión Desktop **NEXT-AVPRO-BETA.V2.1** no fue modificada.
- Este paquete es una versión móvil preparada para GitHub Pages.

## Pendientes / próximos pasos
- Pruebas completas en iPhone de todos los pasos y documentos.
- Consolidación adicional de código heredado de versiones anteriores si se decide hacer una limpieza estructural mayor.
- Integración futura de funciones OCR, ubicaciones de IAAI/Copart y otras funciones del roadmap.

## Nota
No se debe mezclar esta versión móvil con la aplicación Desktop V2.1. El ZIP está preparado para publicarse como la versión móvil del proyecto.
