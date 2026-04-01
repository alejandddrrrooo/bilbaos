# Bilbaos — Substack Ghostwriting con IA

Sistema de ghostwriting asistido por IA para [bilbaos.substack.com](https://bilbaos.substack.com/), el Substack de Andrés Bilbao.

## Cómo funciona

### Paso 1: Configurar el master prompt

El archivo `Master Prompt - Andrés Bilbao.md` contiene todas las reglas de voz, estilo, prohibiciones y estructura que la IA debe seguir. Se carga al inicio de cada sesión de Claude (o cualquier LLM).

Incluye:
- Voz en primera persona como Andrés Bilbao
- Tono conversacional + inteligente, con argentinismos/colombianismos como condimento
- Prohibiciones absolutas (estructuras binarias, em dashes, frases LLM, descriptores vacíos, datos inventados)
- Reglas de formato (números, monedas, listas)
- Estructura de ensayo (apertura, desarrollo, cierre)
- Jerarquía de fuentes (WEF, McKinsey, BCG, filings públicos, TechCrunch/Bloomberg/WSJ/FT)
- Checklist de autoauditoría

### Paso 2: Preparar el insumo

Cada ensayo parte de uno de tres tipos de insumo:

| Tipo | Descripción | Ejemplo |
|------|-------------|---------|
| **Transcripción** | Audio de podcast/entrevista transcrito | Conversación de Andrés en un evento |
| **Artículo fuente** | Artículo o reporte que dispara la reflexión | Reporte de McKinsey, nota de Bloomberg |
| **Tema original** | Solo un tema — la IA investiga y escribe | "El impacto de IA en universidades" |

### Paso 3: Generar el ensayo

1. Cargar el master prompt en Claude
2. Pedir deep research sobre el tema (la IA busca fuentes verificables)
3. Revisar el research y aprobar/ajustar el enfoque
4. Generar el ensayo completo con piedepáginas y enlaces
5. Exportar como `.docx` con footnotes nativas

### Paso 4: Revisar y publicar

1. Revisar el `.docx` generado — corregir lo que haga falta
2. Subir a Substack como borrador
3. Publicar

## Estructura del repo

```
Bilbaos/
├── README.md                                    # Este archivo
├── Master Prompt - Andrés Bilbao.md             # Reglas de voz, estilo y estructura
├── Borrador - *.md                              # Borradores de artículos sobre invitados/temas
└── Ensayo *.docx                                # Ensayos finales con footnotes nativas
```

### Archivos

- **`Master Prompt - Andrés Bilbao.md`** — El cerebro del sistema. Todas las instrucciones que la IA necesita para escribir como Andrés. Se actualiza cada vez que se detecta un patrón LLM nuevo que prohibir.

- **`Borrador - [Nombre].md`** — Artículos en formato Markdown, generalmente sobre invitados o temas específicos. Listos para revisión antes de exportar a `.docx`.

- **`Ensayo N - [Título].docx`** — Ensayos finales en Word con piedepáginas nativas (superíndice + enlace clicable a la fuente). Máximo 8-10 footnotes por ensayo, fuentes consolidadas.

## Reglas clave del master prompt

- Escritura en **primera persona como Andrés Bilbao** (nunca tercera persona)
- **Prohibido**: estructuras binarias ("No es X, es Y"), em dashes, frases cliché de LLM, descriptores vacíos ("El argumento es directo"), datos inventados
- **Monedas**: US$X para dólares, $X COP para pesos colombianos
- **Números**: 0-9 en letras, 10+ en cifras, porcentajes siempre como número + %
- **Fuentes**: Solo fuentes verificables con URL. Nunca CEPAL ni OECD
- **Footnotes**: Máximo 8-10 por ensayo, cada una con enlace clicable

## Herramientas

- **Claude** (Anthropic) — Generación de ensayos y research
- **Node.js + docx** — Generación de `.docx` con footnotes nativas
- **Claude in Chrome** — Upload directo a Substack como borrador
