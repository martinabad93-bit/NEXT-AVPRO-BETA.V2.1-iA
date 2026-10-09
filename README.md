# NEXT GB AUTO IMPORT — Corrección del resumen de WhatsApp

## Problema
El resumen de WhatsApp tomaba los valores de campos heredados ocultos:
- `documentacion_usd` = US$75 (exportación solamente)
- `taller_miami_usd` = US$450 (inspección predeterminada)

Mientras tanto, la plataforma y el PDF usan el campo activo `documentacion_origen_usd`, cuyo valor predeterminado es US$675 y es editable. Por eso WhatsApp desglosaba US$75 como documentación y US$450 como taller aunque la plataforma mostraba correctamente el total.

## Corrección aplicada
Se modificó únicamente la función `enviarWhatsAppCostos()`:
- **Documentación:** ahora lee `documentacion_origen_usd`, con respaldo de US$675 si el campo no tiene un valor numérico.
- **Taller Miami:** ahora lee `reparacion_miami_usd`, respetando el importe que el usuario haya introducido.
- No se modificaron los cálculos de costos, el PDF ni la plataforma.

## Comportamiento esperado
Con documentación predeterminada de US$675 y taller/reparación Miami de US$950, el resumen debe mostrar:
- Documentación: US$675.00
- Taller Miami: US$950.00

Si el usuario cambia cualquiera de esos importes, WhatsApp debe reflejar el valor vigente en su campo activo.

## Validación
- 19 bloques de JavaScript examinados.
- 0 errores de sintaxis detectados con `node --check`.

## Archivo
`NEXT_GB_AUTO_IMPORT_WHATSAPP_FIX.html`
