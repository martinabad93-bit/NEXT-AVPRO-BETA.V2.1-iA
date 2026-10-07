# NEXT AVPRO BETA V2.7 — MOBILE

## Corrección principal

Se corrigió la sincronización de los conceptos relacionados con placa.

### 1. Impuesto de Primera Placa
El valor calculado en la sección **Aduanas** como:

- Primera Placa
- CO₂
- Marbete

ahora se incorpora al costo real de la operación y al cálculo de inversión/Landed.

### 2. Emisión de Placa
Se mantiene como concepto separado:

- Placa PP: RD$ 2,000.00
- Gestión / Endoso: RD$ 5,000.00
- Normativa 03-25: RD$ 0.00 por defecto
- **Total Emisión de Placa:** suma de los tres conceptos.

### 3. Pago 5
El Pago 5 ya no debe presentar solamente “RD$7,000” como si ese fuera el monto final del pago.

El sistema debe tomar el **total de Emisión de Placa**, convertirlo a USD según la tasa de la operación y usar ese monto como importe del Pago 5.

### 4. Sincronización
Los conceptos se mantienen sincronizados entre:

- Aduanas
- Costos
- Resumen final
- Total de operación / Landed
- Cotización / Proforma
- WhatsApp
- Salida de IA cuando corresponda

### Regla importante

**Impuesto Primera Placa + CO₂ + Marbete** y **Emisión de Placa (PP + Gestión/Endoso + Normativa)** son conceptos diferentes.

No deben mezclarse ni contarse dos veces.

## Archivos

- `NEXT-AVPRO-BETA.V2.7-MOBILE.html` — versión corregida.
- ZIP incluido para distribución.

## Nota de prueba

La corrección fue aplicada sobre el código existente. No se realizó una prueba interactiva completa en un navegador dentro de esta ejecución.
