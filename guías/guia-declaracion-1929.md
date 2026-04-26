# Guía Paso a Paso: Declaración Jurada 1929 (DJ 1929)

> Fuente: Fintual — "Guía paso a paso para completar la declaración 1929"

## ¿Qué es la DJ 1929?

La **Declaración Jurada 1929** informa al SII sobre **operaciones e inversiones en el exterior**. Es obligatoria si tienes inversiones extranjeras (acciones, ETFs, dólares, dividendos de empresas extranjeras).

- **Plazo formal**: 30 de junio.
- **Recomendación**: completarla **antes del F22** (30 de abril), porque los datos afectan directamente la declaración de renta.

## Métodos de Envío

### Opción A: Importador de Datos (solo Fintual)
Si **solo** tienes inversiones en el exterior con Fintual:
1. Buscar DJ 1929 en "Declaraciones Comunes" → "Declarar".
2. Elegir "Importador de Datos".
3. Verificar datos personales y periodo.
4. Subir el archivo CSV enviado por Fintual (`dj1929_formato_sii.csv`).
5. Agregar RUT del representante (tu RUT si declaras tú mismo).
6. "Validar y Enviar".

### Opción B: Formulario en Pantalla (múltiples instituciones)
Si tienes inversiones con **Fintual y otras instituciones**, usar esta opción para ingresar toda la información manualmente.

## Campos a Completar por Activo

### Sección B — Ganancias de Capital (hoja "Declaración de tus activos")

| Campo | Fuente en planilla |
|-------|--------------------|
| Operación | 13.- Ganancias de capital |
| Nombre o razón social | Columna A (Nombre) |
| TAX-ID | Columna B (Tax-id) |
| País | Columna C (País) |
| Relación | 99.- No existe relación |
| Participación | 0 |
| Monto Actualizado al 31.12 | Columna D (Valor inversión al 31.12) |
| Rentas del Exterior | Columna E (Ganancias por ventas). Si no hay → vacío |
| Pérdidas en el Exterior | Columna F (Pérdidas por ventas). Si no hay → vacío |

### Sección B — Dividendos (hoja "Declaración de tus dividendos")

| Campo | Fuente en planilla |
|-------|--------------------|
| Operación | 10.- Dividendos |
| Nombre o razón social | Columna A (Nombre) |
| TAX-ID | Columna B (Tax-id) |
| País | Columna C (País) |
| Domicilio | Columna D (Domicilio) |
| Ciudad | Columna E (País) |
| Relación | 99.- No existe relación |
| Participación | 0 |
| Rentas del Exterior | Columna F (Dividendos recibidos) |
| Impuesto a la Remesa | Columna G (Impuestos pagados en el exterior). Si no hay → vacío |

## Cuadro Resumen Final

Verificar que el cuadro resumen coincida con la hoja "Ejemplo DJ1929" de la planilla:

| Campo del Cuadro Resumen | Fuente |
|--------------------------|--------|
| Total Monto Actualizado al 31.12 | "TOTAL MONTO ACTUALIZADO AL 31.12" |
| Total Rentas del Exterior | "TOTAL RENTAS DEL EXTERIOR" |
| Total Pérdidas en el Exterior | "TOTAL PÉRDIDAS EN EL EXTERIOR" |
| Total Impuesto a la Remesa | "TOTAL IMPUESTO A LA REMESA" |

> ⚠️ Si tienes inversiones en el exterior con **otras instituciones**, estas se agregan en la misma DJ 1929. El cuadro resumen sumará todas las filas, no solo las de Fintual.

## Relación con el F22

Una vez completada la DJ 1929, los datos se utilizan para completar las líneas del F22 relacionadas con inversiones extranjeras (ver `guia-acciones-dolares-f22.md`).
