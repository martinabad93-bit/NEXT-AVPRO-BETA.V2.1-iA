# NEXT GB AUTO IMPORT — Mobile V2.7

## Corrección aplicada: sincronización de placa

Se corrigió exclusivamente el flujo de placa de la versión Mobile V2.7 para que exista un único valor canónico de **Emisión de Placa & Endoso**.

### Fórmula canónica

**TOTAL EMISIÓN DE PLACA = Primera Placa 17% + CO₂/Marbete + Normativa 03-25 + Placa PP + Gestión/Endoso**

La **Reparación en RD permanece separada** y no forma parte de la emisión de placa.

### Dónde se corrigió

- **IA gráfica Mobile (`get24()` / `render24()`):** ahora usa el total completo de placa, incluyendo `window.currentPlaca`.
- **Pago 5:** ahora corresponde únicamente al total completo de Emisión de Placa convertido a USD. No incluye Reparación en RD.
- **Total Destino Local:** incluye el total de placa una sola vez y mantiene Reparación RD como concepto separado.
- **Landed Cost:** utiliza el mismo total canónico de placa.
- **Margen / ROI:** se derivan del Landed Cost corregido.
- **Resumen final:** `Total Emisión de Placa` utiliza Primera Placa + Normativa + PP + Gestión.
- **PDF:** utiliza el mismo total canónico y presenta una sola línea de Emisión de Placa & Endoso; Reparación RD queda separada.
- **Proforma / WhatsApp:** reciben el Pago 5 ya corregido desde el cronograma sincronizado.
- **V2.7 plate sync:** se simplificó para sincronizar el valor canónico, sin volver a sumar manualmente Primera Placa sobre los totales finales.

### Validación realizada

- Se verificó que no permanezca el cálculo anterior de Pago 5 que excluía Primera Placa.
- Se verificó que Pago 5 ya no incluya Reparación RD.
- Se verificó que el PDF use el mismo total de placa.
- Se realizó comprobación de sintaxis de los bloques JavaScript embebidos: **20 bloques revisados, 0 errores de sintaxis**.

### Archivos

- `index (1).html` — Mobile V2.7 corregida.
- `README.md` — documentación de esta corrección.

> Esta corrección no modifica la lógica de Desktop ni pretende reemplazar la V2.5 estable.
