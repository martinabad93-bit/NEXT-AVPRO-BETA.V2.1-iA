# NEXT GB MOBILE V3.75 — AI Freeze Fix

## Corrección aplicada

Se corrigió el congelamiento de la página que ocurría al enviar una consulta a la IA.

### Causa encontrada
El bloque que añadía el desglose de EMISIÓN DE PLACA utilizaba un `MutationObserver` sobre `#nextgb-ai-result`. El observer vigilaba cambios en `childList` y, dentro de su propio callback, volvía a modificar `innerHTML`. Esa modificación generaba otra mutación y podía producir un ciclo continuo de renderizado que congelaba el navegador.

### Solución
Se eliminó ese ciclo de observación recursiva y se sustituyó por una actualización controlada:
- Actualiza el desglose solo cuando cambian los valores.
- Usa una clave de valores para evitar renders repetidos.
- Bloquea reentrada durante el render.
- Mantiene Placa Provisional, Gestión/Endoso, Normativa, Primera Placa + CO₂ + Marbete y Total Emisión.
- No modifica el cálculo principal de la cotización.

## Validación
- 20 bloques JavaScript revisados.
- 0 errores de sintaxis con `node --check`.
- Se mantienen las lógicas existentes de placa, Aduana, Inversión, Pago 5 y sincronización.
- La corrección se limita al flujo que provocaba el congelamiento de la IA.

## Archivo
`index (1).html` — NEXT GB MOBILE V3.75 con corrección del freeze de IA.
