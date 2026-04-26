---
description: Verificar si los APV están correctamente integrados en la propuesta del SII
---

# Verificar APV en Declaración

Workflow para verificar que los aportes de Ahorro Previsional Voluntario (APV) están correctamente reflejados en la propuesta del SII.

## Pasos

### 1. Leer guía de normativa
// turbo
Lee `guías/guia-renta-sii.md` y `guías/guia-f22-formulario.md` para entender dónde se reflejan los APV en el F22 (línea 17, código 765).

### 2. Extraer certificado de APV
Busca en `input-usuario/` archivos que contengan "apv" o "certificado_24" en el nombre. Extráelos con `markitdown`:
```
mcp_markitdown_convert_to_markdown(uri="file:///ruta/absoluta/al/certificado_apv.pdf")
```

### 3. Extraer propuesta del SII
Extrae el PDF de `declaración-propuesta/` con `markitdown`. Ubica la línea 17 (código 765) y su monto.

### 4. Cotejar APV
Compara:
- Monto aportado según certificado APV vs. monto en línea 17 del F22
- Régimen tributario (letra A o B) — verifica que sea consistente
- Si hay múltiples certificados APV, suma todos los aportes

### 5. Reportar hallazgos
Informa al usuario:
- Si el APV está correctamente reflejado ✅
- Si hay discrepancia en el monto ⚠️
- Si el APV no aparece en la propuesta ❌
- Recomendaciones para corregir
