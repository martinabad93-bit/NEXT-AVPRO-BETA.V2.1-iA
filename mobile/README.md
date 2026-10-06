# NEXT-AVPRO-BETA.V2.0

## Versión
**NEXT-AVPRO-BETA.V2.0**  
Fecha: 6 de octubre de 2026

## Base de esta versión
Esta versión parte de **NEXT-AVPRO-BETA.V1.75** y consolida la nueva lógica de costos y operación autorizada para la V2.0.

## Cambios implementados

### 1. Honorarios manuales
- Campo visible **Honorarios (USD$)**.
- Valor predeterminado: **US$0.00**.
- Es manual/editable.
- Se incorpora al **FOB Miami**, Landed Cost, margen, cotización, proforma y cronograma de pagos.
- No se agrega automáticamente ningún honorario si el usuario no lo introduce.

### 2. Nueva Operación
Se agregó **＋ Nueva Operación** con tres opciones:
- Nueva consulta con IA.
- Nueva Cotización.
- Nueva Proforma.

Antes de limpiar se solicita confirmación. Se limpia la operación actual sin borrar:
- Base de datos de vehículos.
- Configuración.
- Preferencia Dark/Light.

### 3. FOB Miami
El **FOB Miami** representa el costo completo de la operación en Miami:
- Compra en subasta.
- Auction Fees.
- Grúa/Inland.
- Documentación y logística en origen.
- Reparación en Miami.
- Fee Broker.
- Honorarios manuales, si existen.

### 4. Total Despacho Sin Placa
Nueva definición acumulativa:

**Total Despacho Sin Placa = FOB Miami + Flete + Aduanas/Impuestos + Paquete de Despacho**

El paquete de despacho conserva el valor predeterminado de **US$465**.

### 5. Emisión de Placa
La sección ahora se denomina:

**EMISIÓN DE PLACA**

Campos:
- **Normativa 03-25:** RD$0.00 por defecto y manual/editable.
- **Placa PP:** RD$2,000.00.
- **Gastos de Endoso / Gestión:** RD$5,000.00.

Los valores de esta sección se manejan en **RD$**.

### 6. Etapas del costo
La estructura de la operación queda:

**FOB Miami → Total Despacho Sin Placa → EMISIÓN DE PLACA → Landed Cost**

### 7. Cronograma de pagos permanente
La Proforma conserva siempre los cinco pagos:
1. **Pago 1: Depósito de Seguridad**
2. **Pago 2: Balance Subasta**
3. **Pago 3: Logística Origen**
4. **Pago 4: Aduanas y Flete**
5. **Pago 5: Placa y Endoso**

También conserva **Total Inversión (Landed)**.

El Pago 2 incorpora compra/fees, broker y honorarios. El Pago 5 toma los conceptos de emisión de placa y endoso/gestión convertidos a USD mediante la tasa vigente de la cotización.

### 8. PDF y WhatsApp
La Proforma mantiene el cronograma completo de cinco pagos y los valores se sincronizan con el motor de cálculo.

### 9. IA y Live Cost
La IA y el Live Cost usan la misma lógica principal de costos, incluyendo honorarios dentro del FOB y la nueva estructura de despacho sin placa.

## Ejemplo de referencia
Si:
- FOB Miami = US$12,000
- Flete = US$910
- Aduanas = RD$67,500
- Paquete despacho = US$465
- Tasa = RD$60.00/USD

Entonces:

**Total Despacho Sin Placa = 12,000 + 910 + 465 + 67,500/60 = US$14,500**

La emisión de placa se agrega después:
- Normativa 03-25: manual.
- Placa PP: RD$2,000.
- Endoso/Gestión: RD$5,000.

## Pendientes / no incluidos
- Cálculo automático de la Normativa 03-25: **pendiente**; permanece manual en RD$0 por defecto.
- Max Bidder: **excluido** por decisión del proyecto.
- Base de datos futura de ubicaciones IAAI/Copart: pendiente de una fase posterior.

## Estructura del paquete
```text
NEXT-AVPRO-BETA.V2.0-GITHUB/
├── README.md
└── mobile/
    ├── index.html
    └── Base de Datos Valores Vehiculos 2026 - 2027.csv
```

## Nota
Esta versión no modifica la versión Desktop **NEXT-AVPRO-BETA.V2.1**. Es una versión de trabajo móvil V2.0 y debe probarse antes de publicarse en GitHub.
