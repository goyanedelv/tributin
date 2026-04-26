---
description: Revisión completa de la declaración de renta (F22) — coteja propuesta SII vs certificados y genera informe
---

# Revisar Declaración de Renta

Flujo completo para revisar la propuesta de declaración del SII y generar un informe tributario.

## Pasos

### 1. Leer guías de normativa
// turbo
Lee todos los archivos `.md` en la carpeta `guías/`:
- `guia-renta-sii.md` — Guía oficial de renta
- `guia-f22-formulario.md` — Estructura del F22
- `guia-acciones-dolares-f22.md` — Acciones y dólares
- `guia-planilla-acciones.md` — Planilla de inversiones
- `guia-declaracion-1929.md` — DJ 1929
- `guia-cripto-faq.md` — FAQ cripto del SII

### 2. Extraer propuesta del SII
Extrae el PDF de `declaración-propuesta/` usando `markitdown`:
```
mcp_markitdown_convert_to_markdown(uri="file:///ruta/absoluta/declaración-propuesta/archivo.pdf")
```
Identifica todas las líneas y códigos del F22 con sus montos.

### 3. Extraer certificados del usuario
Extrae **todos** los documentos de `input-usuario/`:
- **PDFs**: usa `markitdown` para cada archivo `.pdf`
- **Excel**: usa el script Python con `openpyxl` (ver instrucciones en `.agents/tributin.md`)

### 4. Identificar líneas relevantes del F22
A partir de los certificados, determina qué líneas/códigos del F22 deberían verse afectados:
- APV → línea 17 (código 765)
- Acciones/fondos mutuos → ganancias de capital, dividendos
- Criptomonedas → mayor valor en enajenación
- Dólares → diferencias de tipo de cambio
- Gastos deducibles → honorarios, salud, educación

### 5. Cotejar propuesta vs. certificados
Para cada línea relevante del F22:
- Compara el monto de la propuesta SII con lo que indican los certificados
- Detecta discrepancias, omisiones y montos incorrectos
- Identifica beneficios tributarios no aprovechados

### 6. Generar informe
Crea el archivo de informe en `output/` con el nombre `{AAAA}{MM}{DD}-{HH:MM}-informe-revisión-tributaria.md` siguiendo la estructura definida en `.agents/tributin.md` (sección "Generar informe").

### 7. Presentar resultados
Muestra al usuario un resumen de los hallazgos clave:
- Número de discrepancias encontradas
- Omisiones detectadas
- Oportunidades tributarias identificadas
- Enlace al informe completo generado
