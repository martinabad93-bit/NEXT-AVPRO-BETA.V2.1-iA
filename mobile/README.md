# NEXT-AVPRO-BETA.V1.5

## Versión
**NEXT-AVPRO-BETA.V1.5 — Mobile**

## Última actualización
2026-10-06

## Objetivo de esta versión
Estabilizar la versión móvil de NEXT GB Auto Import y conectar las principales áreas de trabajo para que una misma operación pueda utilizarse desde IA, Vehículo, Costos, Aduanas, Margen, Cotización y Proforma.

## Mejoras implementadas

### IA
- Se conserva la IA existente como punto central de análisis.
- Los datos generados por la IA se integran con la operación de la aplicación.

### Operación
- Nueva cotización / nueva operación para comenzar desde cero.
- Limpieza de los datos de la operación anterior sin eliminar la base de datos de vehículos.
- Acceso para regresar rápidamente a la IA.

### Vehículo y base de datos
- Selectores de vehículo conectados a la base de datos.
- Integración de marca, modelo, año, serie/trim y tracción.
- Conservación de las reglas de equivalencia de tracción definidas por NEXT GB.

### Grúa Inland
- El usuario introduce únicamente el ZIP de origen.
- El destino permanece guardado internamente como **33142**.
- El cálculo utiliza el origen para determinar la ruta y estimar el costo de grúa.

### Costos
- Valores editables.
- Actualización del costo total en tiempo real.
- Sincronización de los costos con el resto de la operación.

### Aduanas
- Área preparada para trabajar de forma interactiva.
- Los resultados se integran con el costo total de la operación.

### Margen
- Margen neto dinámico.
- Precio de venta editable.
- ROI actualizado automáticamente.
- Resultado visual por estado:
  - Verde: margen positivo.
  - Amarillo: margen ajustado.
  - Rojo: margen negativo.
  - Gris: información incompleta.
- Visualización orientada a la experiencia de la versión Desktop.

### Cotización
- Documento de inversión y rentabilidad.
- Incluye Landed Cost, precio de venta y margen.
- Formato de WhatsApp separado de la Proforma.

### Proforma
- Documento independiente de la Cotización.
- Incluye cronograma de cinco pagos:
  1. Depósito de Seguridad
  2. Balance Subasta
  3. Logística Origen
  4. Aduanas y Flete
  5. Placa y Endoso
- El cronograma se utiliza también en el mensaje de WhatsApp.

### PDF
- Generación orientada a documento real, no a captura de la pantalla.

### WhatsApp y compartir
- WhatsApp para Cotización con formato de reporte interno de inversión.
- WhatsApp para Proforma con cronograma de pagos.
- Opción de compartir mediante las funciones nativas disponibles en el dispositivo.

### Diseño móvil
- Interfaz optimizada para móvil.
- Navegación por las áreas principales:
  **IA | Vehículo | Costos | Margen | Cotización**
- Se conserva el selector Dark/Light existente.

## Funciones que NO forman parte de V1.5
Estas funciones quedan para futuras versiones y no deben agregarse durante la estabilización de V1.5:

- Base completa de ubicaciones IAAI.
- Base completa de ubicaciones Copart.
- Selección automática de sucursal de subasta.
- OCR de facturas.
- Escáner VIN mediante cámara.
- Decoder VIN premium.
- Max Bidder.
- Inteligencia de mercado.
- Historial/CRM avanzado de clientes y operaciones.
- Automatización avanzada de WhatsApp y correo.
- Dashboard administrativo avanzado.

## Próxima etapa
Una vez estabilizada V1.5, el siguiente bloque previsto es la creación de la base de ubicaciones de IAAI/Copart y su integración con el cálculo de transporte Inland.

## Regla de versiones
Cada nueva mejora deberá:
1. Incrementar la versión correspondiente.
2. Actualizar este README.
3. Registrar los cambios realizados.
4. Mantener separada la versión Desktop **NEXT-AVPRO-BETA.V2.1**.
5. Mantener el historial de funciones pendientes.

## Nota
Esta versión móvil debe probarse antes de incorporar nuevas funciones del roadmap.
