# NEXT-AVPRO-BETA.V2.5

Fecha: 2026-10-06

## Base
- Basada en NEXT-AVPRO-BETA.V2.1 Desktop.
- V2.1 no se sobrescribe.
- La interfaz Desktop y los documentos/PDF actuales se conservan como base.
- No se incorporó el problema de impresión de Mobile V2.

## Mejoras implementadas
1. Estado de operación y sincronización IA → formulario → cálculo.
2. Nueva operación mantiene configuración y limpia datos de la operación.
3. Honorarios manuales US$0 por defecto y sincronizados.
4. FOB Miami separado de flete, paquete RD y costos de destino.
5. Total Despacho Sin Placa: FOB Miami + flete + aduanas + paquete despacho RD.
6. Paquete de despacho US$465 permanece fuera del FOB.
7. EMISIÓN DE PLACA.
8. Normativa 03-25: RD$0 por defecto y manual; no se calcula automáticamente.
9. Placa PP: RD$2,000.
10. Endoso / Gestión: RD$5,000.
11. Valores de emisión de placa permanecen en RD$.
12. Live Cost, margen y ROI sincronizados.
13. Cronograma de 5 pagos sincronizado.
14. Pago 4 queda limitado a Aduanas y Flete; no incluye Reparación RD.
15. Pago 5 concentra Placa/Endoso y cualquier reparación RD pendiente del desembolso final.
16. ZIP de origen por operación.
17. ZIP de destino predeterminado configurable.
18. ZIP de destino por defecto: 33132, referencia PortMiami.
19. La consulta IA puede extraer un ZIP de 5 dígitos.
20. Si la IA recibe ZIP de origen y no recibe una grúa manual, intenta calcular el inland automáticamente por ruta.
21. Si la ruta no puede calcularse, no se inventa un costo.
22. Contexto de logística expuesto para futuras integraciones con fuentes de subastas.

## Reglas de ZIP
- Prioridad: ZIP indicado en la operación > ZIP predeterminado para origen cuando corresponda.
- El ZIP de destino pertenece a configuración y se conserva al crear una nueva operación.
- El ZIP de origen pertenece a la operación y se limpia al iniciar una nueva operación.
- El destino predeterminado se puede cambiar desde Valores predeterminados NEXT GB.

## Reglas de cálculo V2.5
- FOB Miami = subasta + fees + inland + documentación/logística origen + reparación Miami + broker.
- Despacho Sin Placa = FOB Miami + flete + paquete despacho + aduanas/DGA convertido a USD.
- Landed = Despacho Sin Placa + emisión de placa + reparación RD, convertidos a USD según la tasa.
- Margen bruto = precio de venta - Landed.
- Margen neto = margen bruto - honorarios.
- ROI neto = margen neto / Landed × 100.

## Documentos
Los generadores de documentos/PDF de Desktop V2.1 se mantienen. V2.5 sincroniza el contexto de cálculo sin sustituir sus plantillas.

## Validación realizada
- JavaScript de los scripts HTML: sintaxis validada con Node.js.
- Se verificaron los campos de ZIP, emisión de placa, FOB/Despacho Sin Placa y cronograma.
- No se modificó la versión Desktop V2.1 original.

## Pendiente para futuras versiones
- Integración autorizada con Copart/IAAI/Bid.Cars.
- Recuperación automática de lote/VIN/ubicación cuando exista una fuente autorizada.
- Cálculo de inland basado en datos de lote/fuente externa.
- Automatización avanzada de auction fees según fuente externa.

## Archivo
- NEXT-AVPRO-BETA.V2.5.html
- Este README
