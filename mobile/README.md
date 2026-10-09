# NEXT GB MOBILE — Corrección de resumen final

## Problema
La pantalla final **“Tu importación está lista”** mostraba un total incorrecto en **Documentación / Taller**. Estaba sumando los campos heredados `documentacion_usd` (US$75) y `taller_miami_usd` (US$450), dando US$525.

## Corrección aplicada
El resumen final ahora lee los mismos campos activos de la operación que usa la plataforma: 
- `documentacion_origen_usd`: documentación, predeterminado US$675 y editable.
- `reparacion_miami_usd`: taller/reparación Miami, valor editable.

El total mostrado es la suma de esos dos valores, sin sustituir el taller por una tarifa fija ni usar el campo heredado de exportación de US$75. No se modificaron los cálculos de PDF, Aduana, placa ni IA.

## Verificación
- Confirmado que la fórmula anterior aparecía una sola vez y fue reemplazada únicamente en `updateFinalSummary()`.
- Se comprobará sintaxis de los bloques JavaScript inline del HTML.
