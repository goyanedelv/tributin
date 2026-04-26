---
description: Analizar historial de criptomonedas y calcular ganancias/pérdidas para el F22
---

# Analizar Criptomonedas para F22

Workflow para analizar el historial de transacciones de criptomonedas y determinar el tratamiento tributario correcto.

## Pasos

### 1. Leer guía de criptomonedas
// turbo
Lee `guías/guia-cripto-faq.md` para entender la normativa del SII sobre criptomonedas.

### 2. Extraer historial de transacciones
Busca en `input-usuario/` archivos de exchanges (`.xlsx`, `.pdf`):
- **Excel** (ej. Binance): usa el script `openpyxl` de `.agents/tributin.md`
- **PDF**: usa `markitdown`

### 3. Clasificar transacciones
Para cada transacción identifica:
- Tipo: compra, venta, trade, staking, airdrop
- Fecha
- Monto en moneda original
- Monto en CLP (si está disponible)

### 4. Calcular mayor valor
- Determina el costo de adquisición de cada criptoactivo
- Calcula ganancias/pérdidas realizadas en ventas o trades
- Convierte a CLP usando el tipo de cambio de la fecha de la transacción (si la información está disponible)

### 5. Determinar líneas del F22
Según la guía del SII, identifica en qué línea(s) del F22 deben declararse las ganancias de criptomonedas.

### 6. Cotejar con propuesta SII
Si hay propuesta del SII:
- Compara el monto calculado con lo que propone el SII
- Identifica discrepancias

### 7. Reportar hallazgos
Genera un resumen con:
- Total de transacciones analizadas
- Ganancia/pérdida neta calculada
- Línea(s) del F22 donde debe declararse
- Discrepancias con la propuesta SII (si aplica)
- Advertencia: la conversión a CLP puede requerir verificación manual
