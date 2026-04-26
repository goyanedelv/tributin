# Cómo Declarar Acciones y Dólares (Fintual) en el Formulario 22

> Fuente: Fintual — "Cómo declarar tus movimientos en Dólares y Acciones en Fintual en el Formulario 22"

## Requisitos Previos

- Completar la **DJ 1929** antes del F22 (los datos de la DJ afectan la declaración de renta).
- Tener la **planilla de inversiones** enviada por Fintual con las hojas Resumen, Declaración de activos, etc.

## Datos a Calcular Antes de Llenar el F22

A partir de la planilla de Fintual (hoja "Resumen"):

1. **Ganancias/pérdidas por venta de acciones**: celda C11.
2. **Ganancias/pérdidas por venta de moneda extranjera (dólares)**: celda C12.
3. **Dividendos netos recibidos**: celda C13.
4. **Base imponible**: sumar ganancias de acciones + ganancias de dólares. Si da negativo → $0.
5. **Impuesto de Primera Categoría (IDPC)**: base imponible × 25%.

## Mapeo de Líneas y Códigos del F22

### Caso SIN impuestos pagados en el exterior (IPE)

| Línea | Código | Contenido | Fuente |
|-------|--------|-----------|--------|
| 5 | **1865** | Base imponible (ganancias totales). Si es negativa → 0 | Calculado |
| 5 | **1864** | IDPC = base imponible × 25% (redondear decimales) | Calculado |
| 5 | **954** | Se llena automáticamente desde código 1864 | Automático |
| 5 | **955** | Se llena automáticamente desde código 1865 | Automático |
| 12 | **1104** | Dividendos netos recibidos | Celda C13 hoja "Resumen" |
| 48 | **610** | Se llena automáticamente desde código 954 (crédito IDPC) | Automático |
| 52 | **304** | Se llena automáticamente con créditos anotados | Automático |
| 58 | **1901** | Ganancias por venta de dólares (si base imponible = 0 → vacío) | Celda C12 hoja "Resumen" |
| 58 | **1903** | Se llena automáticamente desde código 1901 (IDPC 25%) | Automático |
| 58 | **1912** | Ganancias por venta de acciones (si pérdida → solo dividendos netos) | Celda C11 hoja "Resumen" |
| 58 | **1913** | Se llena automáticamente desde código 1912 | Automático |
| 97 | **116** | Se llena automáticamente desde código 610 | Automático |
| 97 | **757** | Se llena automáticamente desde código 116 | Automático |

> ⚠️ **Códigos 1903, 1913 y 116**: Históricamente el SII ha tenido problemas con el autocompletado de estos códigos. Verificar manualmente.

### Caso CON impuestos pagados en el exterior (IPE)

Si se decide usar los IPE como crédito, se agregan las siguientes líneas:

| Línea | Código | Contenido | Fuente |
|-------|--------|-----------|--------|
| 14 | **748** | Impuestos pagados en el exterior (total) | Hoja "Ejemplo DJ1929", celda "TOTAL IMPUESTO A LA REMESA" |
| 14 | **749** | Se llena automáticamente desde código 748 | Automático |
| 45 | **1018** | Crédito por impuesto soportado en el exterior = código 748 | Automático |

> ⚠️ **Usar IPE como crédito puede generar observaciones del SII.** Se requiere documentación que acredite el pago en el extranjero. Se recomienda asesoría tributaria.

## Notas Importantes

- Si tienes inversión extranjera en **otras instituciones** además de Fintual, los datos de cada código deben **incluir todas las rentas**, no solo las de Fintual.
- Completar la DJ 1929 **antes** del F22.
- Los montos se declaran en **pesos chilenos**.
