# NEXT AVPRO BETA V2.9 — DESKTOP

## Corrección aplicada

Se corrigió la lógica del último pago y el resumen debajo de la IA.

### Pago 5 — último pago
El Pago 5 ahora concentra todo lo relacionado con la Primera Placa:
- Primera Placa + CO₂ + Marbete
- Emisión de placa: PP + Gestión/Endoso + Normativa 03-25

El cronograma muestra **un solo monto en USD** para Pago 5, sin desglosar los RD$2,000 y RD$5,000 al cliente.

### Resumen debajo de la IA
Se agregó una línea visible:
**EMISIÓN DE PRIMERA PLACA · PAGO 5: US$ X,XXX.XX**

Ese monto usa el mismo total canónico del Pago 5, evitando que la placa se calcule pero no se refleje visualmente.

### Sincronización
El total relacionado a placa alimenta:
- Pago 5
- Total Destino
- Landed Cost
- Total Inversión
- Resumen final debajo de la IA
- Salidas que consumen los valores canónicos de placa

La IA existente se conserva.

### Nota de prueba
Se revisó estáticamente el código y se verificaron las referencias nuevas. No se realizó una prueba interactiva completa en navegador en esta ejecución.
