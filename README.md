# 🧾 Tributín

**Agente de IA para revisar tu Declaración de Renta (F22) ante el SII de Chile.**

Tributín es un agente que revisa tu propuesta de declaración del SII, la coteja contra tus certificados de inversión y genera un informe detallado con discrepancias, omisiones y oportunidades tributarias.

> ⚠️ **Disclaimer**: Tributín es una herramienta de **análisis preliminar**. Puede cometer errores. El uso de este agente es de **estricta responsabilidad del usuario**. Los resultados deben ser verificados con un **Contador Auditor o profesional tributario** antes de tomar decisiones. Este proyecto no constituye asesoría tributaria profesional.

---

## ✨ ¿Qué hace?

- 📄 Lee tu propuesta de declaración del SII (Formulario 22)
- 📑 Extrae y analiza tus certificados de inversión (APV, fondos mutuos, acciones, dólares, criptomonedas)
- 🔍 Coteja línea por línea lo que propone el SII vs. lo que dicen tus documentos
- ⚠️ Detecta discrepancias, omisiones y montos incorrectos
- 💡 Identifica beneficios tributarios que podrías estar dejando pasar
- 📊 Genera un informe Markdown detallado con un plan de acción

---

## 🚀 Requisitos

- [VS Code](https://code.visualstudio.com/) con **Antigravity** o [GitHub Copilot](https://github.com/features/copilot) habilitado
- Python 3 con `openpyxl` (para archivos Excel, ej. historial de Binance)

### Dependencias opcionales

```bash
# openpyxl (para leer archivos Excel)
pip install openpyxl
```

> **Nota**: La extracción de PDFs se realiza con el servidor MCP `markitdown` (Antigravity) o con `pdftotext` (Copilot). Si usas Copilot, instala `poppler-utils`:
> ```bash
> sudo apt-get install -y poppler-utils    # Debian/Ubuntu
> brew install poppler                      # macOS
> ```

---

## 📁 Estructura del Proyecto

```
tributín/
├── .agents/                     # 🤖 Agente Antigravity
│   ├── tributin.md              #    Instrucciones del agente
│   └── workflows/               #    Workflows disponibles
│       ├── revisar-declaracion.md
│       ├── verificar-apv.md
│       └── analizar-cripto.md
├── .github/agents/              # 🤖 Agente GitHub Copilot (compatibilidad)
│   └── tributin.agent.md
├── declaración-propuesta/       # 📄 Tu propuesta del SII (PDF)
│   └── .gitkeep
├── guías/                       # 📚 Guías y normativa tributaria
│   ├── guia-renta-sii.md
│   ├── guia-f22-formulario.md
│   ├── guia-acciones-dolares-f22.md
│   ├── guia-planilla-acciones.md
│   ├── guia-declaracion-1929.md
│   ├── guia-cripto-faq.md
│   └── originales/              # PDFs originales (respaldo)
├── input-usuario/               # 📑 Tus certificados e inputs
│   └── .gitkeep
├── output/                      # 📊 Informes generados por Tributín
│   └── .gitkeep
├── .gitignore
└── README.md
```

---

## 📝 ¿Qué poner en cada carpeta?

### `declaración-propuesta/`

Aquí va **un solo archivo**: la propuesta de declaración que te genera el SII.

**Cómo obtenerlo:**
1. Entra a [sii.cl](https://www.sii.cl) → Servicios Online → Declaración de Renta
2. Revisa tu propuesta de declaración (Formulario 22)
3. Estando en la vista de la propuesta, presiona **Ctrl+P** (o Cmd+P en Mac)
4. Selecciona **"Guardar como PDF"** como destino de impresión
5. Guárdalo como `Propuesta Declaración.pdf` dentro de esta carpeta

> Es literalmente una impresión en PDF de lo que muestra el SII en pantalla. No necesitas hacer nada especial.

### `input-usuario/`

Aquí van **todos tus certificados y documentos de inversión**. Ejemplos:

| Documento | Descripción |
|-----------|-------------|
| `certificado_24_apv.pdf` | Certificado N° 24 de APV (lo emite tu administradora: Fintual, AFP, etc.) |
| `certificado-21--(0).pdf` ... | Certificado N° 21 de fondos mutuos (mayor valor en rescates) |
| `certificado_pesos.pdf` | Certificado de inversiones en pesos (acciones, ETFs) |
| `certificado_dolares.pdf` | Certificado de inversiones en dólares |
| `certificado.pdf` | Otros certificados de tu corredora/plataforma |
| `*.xlsx` | Historial de transacciones de exchanges cripto (ej. Binance) |

> Descarga estos certificados desde tu corredora, administradora de fondos o exchange. Generalmente están disponibles en la sección "Documentos tributarios" o "Certificados" de cada plataforma.

### `guías/`

Guías y normativa tributaria de referencia. **Ya vienen incluidas** en el repositorio en formato **Markdown resumido**, listas para que Tributín las lea directamente sin conversión. Contienen:

| Archivo | Contenido |
|---------|-----------|
| `guia-renta-sii.md` | Guía oficial de Renta del SII: clasificación de rentas, quién declara, tabla IGC, beneficios tributarios |
| `guia-f22-formulario.md` | Guía completa del Formulario 22: estructura, secciones, deducciones, errores comunes |
| `guia-acciones-dolares-f22.md` | Cómo declarar acciones y dólares (Fintual) en el F22: mapeo de líneas/códigos |
| `guia-planilla-acciones.md` | Estructura de la planilla de inversiones de Fintual (7 hojas) |
| `guia-declaracion-1929.md` | Guía paso a paso para la Declaración Jurada 1929 |
| `guia-cripto-faq.md` | Preguntas frecuentes del SII sobre criptomonedas e impuestos |

Los PDFs originales de donde se generaron estos resúmenes están en la subcarpeta `guías/originales/` como respaldo.

> Puedes agregar más guías si lo necesitas. Tributín las leerá automáticamente.

### `output/`

Aquí Tributín genera sus informes de revisión. **No necesitas poner nada** — el agente crea los archivos automáticamente con formato:

```
AAAAMMDD-HH:MM-informe-revisión-tributaria.md
```

---

## 💬 Cómo usar Tributín

### Con Antigravity (recomendado)

1. Clona este repositorio y abre la carpeta en VS Code con Antigravity
2. Agrega tus archivos en `declaración-propuesta/` e `input-usuario/`
3. Usa los workflows disponibles:

```
/revisar-declaracion    → Revisión completa del F22
/verificar-apv          → Verificar APV en la propuesta
/analizar-cripto        → Analizar historial de criptomonedas
```

O simplemente pide:

```
Revisa mi declaración de impuestos
```

4. Tributín analizará todos los documentos y generará un informe en `output/`

### Con GitHub Copilot

1. Abre la carpeta en VS Code con GitHub Copilot habilitado
2. Agrega tus archivos en `declaración-propuesta/` e `input-usuario/`
3. Abre Copilot Chat y escribe:

```
@tributin Revisa mi declaración de impuestos
```

4. Tributín analizará los documentos y generará el informe

### Otros prompts útiles

```
Verifica si mis APV están bien integrados en la propuesta
Revisa el archivo de criptomonedas y calcula las ganancias
¿Qué beneficios tributarios me estoy perdiendo?
```

---

## 🔒 Privacidad

Tus datos **nunca se suben a GitHub**. El `.gitignore` excluye automáticamente:

- `input-usuario/*` — tus certificados y documentos personales
- `declaración-propuesta/*` — tu propuesta del SII
- `output/*` — los informes generados
- `.gemini/` — datos locales de Antigravity

Solo se versiona el agente, las guías públicas y este README.

---

## 🤝 Contribuir

¡Las contribuciones son bienvenidas! Algunas ideas:

- **Nuevas guías**: Si encuentras documentación tributaria útil, agrégala a `guías/`
- **Mejoras al agente**: Las instrucciones están en `.agents/tributin.md` (Antigravity) y `.github/agents/tributin.agent.md` (Copilot)
- **Workflows**: Puedes agregar nuevos workflows en `.agents/workflows/`
- **Soporte para más plataformas**: Agregar instrucciones para certificados de otras corredoras (Racional, BTG, LarrainVial, etc.)
- **Más años tributarios**: Actualizar las guías cuando el SII publique nueva normativa
- **Bugs y mejoras**: Si Tributín se equivoca en algo, abre un issue describiendo el caso

### Cómo contribuir

1. Haz fork de este repositorio
2. Crea una rama para tu cambio (`git checkout -b feature/mi-mejora`)
3. Haz commit de tus cambios (`git commit -m 'Agrega soporte para certificado X'`)
4. Push a tu rama (`git push origin feature/mi-mejora`)
5. Abre un Pull Request

---

## 📄 Licencia

MIT

---

## ⚠️ Aviso Legal

Este proyecto es una **herramienta de análisis preliminar** desarrollada como experimento de IA aplicada a la tributación chilena. **No reemplaza** la asesoría de un Contador Auditor o profesional tributario certificado.

- Los resultados pueden contener **errores e imprecisiones**
- La normativa tributaria cambia cada año — las guías incluidas pueden estar desactualizadas
- El usuario es **el único responsable** de la información que declara ante el SII
- Antes de enviar tu declaración, **verifica los resultados con un profesional**

**Usar este agente implica aceptar que el resultado es orientativo y no vinculante.**
