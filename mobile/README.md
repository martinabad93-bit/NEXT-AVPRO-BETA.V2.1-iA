# NEXT-AVPRO-BETA.V1.75 — Mobile

## Versión
**NEXT-AVPRO-BETA.V1.75**

## Fecha
**2026-10-06**

## Objetivo
Estabilizar la operación móvil para que cada nueva operación comience realmente desde cero, completar la Proforma con la estructura de la versión web y corregir la lógica de honorarios y cronograma de pagos.

## Cambios implementados

### 1. Nueva operación desde cero
Se agregó **＋ Nueva operación** como acción visible en la parte superior.

Al pulsarlo aparecen tres opciones:
- 🤖 Nueva consulta con IA
- 📊 Nueva cotización
- 📄 Nueva proforma
- Cancelar

La nueva operación elimina los datos de la operación anterior y no reutiliza el resultado de la IA anterior.

### 2. Limpieza de operación
Se limpian los datos de:
- Vehículo
- VIN
- Millaje
- Compra/subasta
- Auction fees
- Grúa Inland
- Documentación
- Taller Miami
- Broker
- Honorarios
- Flete
- Despacho
- Placa
- Reparación RD
- Precio de venta
- Depósito de seguridad
- Resultado IA
- Consulta IA anterior

No se elimina:
- Base de datos de vehículos
- Configuración de valores predeterminados
- Tema Dark/Light
- Configuración de la aplicación

También se elimina el estado persistido de la operación para evitar que una operación nueva recupere valores de la anterior.

### 3. Honorarios
Los **Honorarios NEXT GB** pasan a formar parte real del costo de inversión/Landed Cost, siguiendo la estructura de la Proforma web.

El valor es manual y editable.

Se sincroniza con:
- Costos
- Margen
- Cotización
- Proforma
- Cronograma de pagos
- WhatsApp
- PDF

### 4. Proforma completa
La Proforma móvil fue alineada con la estructura de la referencia web e incluye:

- Vehículo
- VIN / Chasis
- Millaje
- Tasa DOP
- Subasta y Fees
- Grúa Inland
- Documentación y Taller Miami
- Fee Broker & Honorarios
- Total Gastos en Origen
- Flete Marítimo
- Despacho Aduanal (Sin Placa)
- Total Despacho (Sin Placa)
- Primera Placa y Marbete
- Reparación en RD
- Total Destino Local
- Costo Total (Landed Cost)
- Cronograma completo de 5 pagos
- Total Inversión
- Nota de presupuesto referencial

### 5. Cronograma de pagos
Los cinco pagos quedan sincronizados con el cálculo real:

1. Depósito de Seguridad
2. Balance Subasta — incluye compra, fees, broker y honorarios, menos el depósito
3. Logística Origen — grúa, taller y documentación
4. Aduanas y Flete
5. Placa y Endoso

El total de los pagos debe corresponder al Landed Cost de la operación.

### 6. Total Despacho (Sin Placa)
Se agregó un subtotal/total específico para el despacho sin placa.

Se muestra:
- Equivalente en USD
- Equivalente en RD$

La cifra agrupa el paquete de despacho/puerto RD y el despacho aduanal sin incluir primera placa.

### 7. Margen
El margen neto ahora se calcula sobre el Landed Cost real, incluyendo Honorarios cuando fueron introducidos.

**Margen = Precio de Venta − Landed Cost**

### 8. PDF y WhatsApp
La Proforma PDF y el mensaje de WhatsApp utilizan el cronograma corregido y los valores de honorarios/depósito correspondientes.

## Pendiente / Roadmap
No forma parte de V1.75:
- Base completa de ubicaciones IAAI/Copart
- Selección automática de sucursal
- OCR de facturas
- Escáner VIN por cámara
- Decoder VIN premium
- Max Bidder
- Inteligencia de mercado
- CRM avanzado
- Automatización avanzada de WhatsApp/correo
- Dashboard administrativo

## Estructura GitHub
```text
NEXT-AVPRO-BETA.V1.75-iA/
├── index.html                 # Desktop V2.1, fuera de esta actualización
└── mobile/
    ├── index.html             # NEXT-AVPRO-BETA.V1.75 Mobile
    ├── README.md
    └── Base de Datos Valores Vehiculos 2026 - 2027.csv
```

## Nota de compatibilidad
La versión Desktop **NEXT-AVPRO-BETA.V2.1** no se modifica en esta actualización.

## Regla de versiones
Cada nueva mejora debe generar un README actualizado con:
- versión
- fecha
- cambios
- correcciones
- nuevas funciones
- pendientes
- estructura de archivos
- notas de uso
