# openAI-vs-ollama

# GPT-4o vs Modelos Locales Gratuitos - Comparación Real

Comparación exhaustiva entre GPT-4o y modelos de IA locales completamente gratuitos en 6 pruebas del mundo real.

## 🎥 Video del Experimento

[Ver video completo en YouTube](URL_DE_TU_VIDEO)

## 📊 Resumen de Resultados

| Prueba | GPT-4o | Mejor Local | Diferencia | Ganador |
|--------|--------|-------------|------------|---------|
| 1. Código Python | 96/100 | Qwen 7B: 98/100 | +2 | 🟢 Local |
| 2. Sentimiento | 98/100 | Mistral 7B: 98/100 | 0 | 🟡 Empate |
| 3. Extracción Datos | 87/100 | Qwen 14B: 82/100 | -5 | 🔴 GPT-4o |
| 4. Servicio Cliente | 95/100 | Llama 8B: 88/100 | -7 | 🔴 GPT-4o |
| 5. PDFs | 92/100 | Mixtral 8x7B: 85/100 | -7 | 🔴 GPT-4o |
| 6. Workflow Completo | 94/100 | Llama 70B: 90/100 | -4 | 🔴 GPT-4o |

**Score Final: GPT-4o 4 - Locales 2**

**Pero:** Para tareas específicas con el modelo correcto, los locales son iguales o mejores.

## 💰 Análisis de Costos

### Escenario: 10,000 requests/mes

**Solo GPT-4o:**
- Costo mensual: $50
- Costo anual: $600

**Estrategia Híbrida:**
- 60% Modelos locales: $0
- 30% GPT-4o mini: $1.50
- 10% GPT-4o (crítico): $5
- **Total: $6.50/mes = $78/año**
- **Ahorro: $522/año (87%)**

## 🛠️ Stack Tecnológico

- **n8n**: Plataforma de automatización open source
- **Ollama**: Runtime para modelos locales
- **OpenAI API**: Para GPT-4o
- **Python 3.10+**: Scripts de análisis
- **Claude API**: Generación de evaluadores

## 🤖 Modelos Utilizados

### GPT-4o
- Parámetros: 1-2 Trillones (estimado)
- Costo: $0.005/1K tokens input, $0.015/1K output
- Velocidad: ~4-6 segundos

### Modelos Locales

**Para Código:**
- Qwen 2.5 Coder 7B
- DeepSeek Coder 6.7B

**Para Lenguaje Natural:**
- Llama 3.1 8B
- Mistral 7B Instruct

**Para Tareas Complejas:**
- Qwen 2.5 14B
- Mixtral 8x7B

**Para Workflows:**
- Llama 3.1 70B

## 📋 Las 6 Pruebas

### Prueba 1: Generación de Código Python

**Objetivo:** Crear función para calcular distancia euclidiana con:
- Docstring completo
- Type hints
- Error handling
- Código limpio y eficiente

**Prompt:**
```
Genera una función Python que calcule la distancia euclidiana entre dos puntos en un plano 2D.

REQUISITOS OBLIGATORIOS:
1. Nombre: "euclidean_distance"
2. Parámetros: point1, point2 (tuplas con x, y)
3. Docstring completo
4. Type hints para parámetros y retorno
5. Manejo de errores (validación de inputs)
6. Retornar float con distancia

FÓRMULA: distancia = √[(x2 - x1)² + (y2 - y1)²]

Responde ÚNICAMENTE en JSON:
{
  "code": "código completo (usar \\n para saltos)",
  "explanation": "breve explicación",
  "features": {
    "has_docstring": true/false,
    "has_type_hints": true/false,
    "has_error_handling": true/false,
    "function_name": "euclidean_distance"
  },
  "complexity": "básica/intermedia/avanzada",
  "estimated_lines": número
}

NO markdown, NO ```json, solo JSON puro.
```

**Resultado:** 🟢 Qwen ganó (98 vs 96)

---

### Prueba 2: Análisis de Sentimiento

**Objetivo:** Clasificar 5 tweets como positivo, negativo o neutral con:
- Clasificación precisa
- Nivel de confianza
- Razones específicas

**Prompt:**
```
Analiza el sentimiento de los siguientes 5 tweets y clasifícalos como positivo, negativo o neutral.

TWEETS:
1. "¡Increíble producto! Superó mis expectativas 🎉"
2. "El servicio al cliente fue terrible, nunca más compro aquí"
3. "El paquete llegó hoy. Todo en orden."
4. "No sé si recomendarlo, tiene pros y contras"
5. "ESTAFA TOTAL. Me timaron. Eviten esta empresa"

INSTRUCCIONES:
- Clasifica cada tweet: positivo/negativo/neutral
- Asigna confianza (0.0-1.0)
- Razón breve (10-30 palabras) mencionando palabras clave
- Calcula resumen con totales

Responde en JSON:
{
  "resultados": [
    {
      "tweet_id": 1,
      "sentimiento": "positivo/negativo/neutral",
      "confianza": 0.0-1.0,
      "razon": "explicación específica"
    }
  ],
  "resumen": {
    "positivos": número,
    "negativos": número,
    "neutrales": número
  }
}

NO markdown, solo JSON puro.
```

**Resultado:** 🟡 Empate técnico - GPT-4o y Mistral (98/100)

---

### Prueba 3: Extracción de Datos Estructurados

**Objetivo:** Extraer información de 3 emails desordenados a JSON estructurado.

**Prompt:**
```
Extrae información estructurada de los siguientes 3 correos electrónicos de clientes.

CORREOS:

--- EMAIL 1 ---
De: maria.garcia@email.com
Fecha: 15 de marzo de 2024
Asunto: Pedido urgente - Laptop HP

Hola,

Necesito cotización para:
- 5 laptops HP ProBook 450 G10
- 2 monitores Dell 27" 4K
- 1 licencia Microsoft Office 365 Business (10 usuarios)

Presupuesto máximo: 8,500 EUR
Fecha límite de entrega: 30 de marzo
Método de pago preferido: Transferencia bancaria

Saludos,
María García
Empresa: TechSolutions SL
Teléfono: +34 91 123 4567

--- EMAIL 2 ---
De: juan.lopez@startup.io
Fecha: 18 de marzo de 2024
Asunto: Re: Consulta sobre servidores

Buenas tardes,

Después de revisar las opciones, me gustaría proceder con:
- 2x Servidor Dell PowerEdge R740 (32GB RAM, 2TB SSD)
- Instalación y configuración incluida
- Soporte técnico por 1 año

El proyecto tiene un presupuesto de 12,000-15,000 EUR.
Necesitamos instalación antes del 15 de abril.
Podemos pagar 50% por adelantado y 50% al finalizar.

Empresa: InnovaStart
CIF: B98765432
Contacto: Juan López (CTO)
Tel: +34 93 987 6543

--- EMAIL 3 ---
De: ana.martinez@pyme.es
Fecha: 20 de marzo de 2024
Asunto: Renovación equipos oficina

Hola equipo,

Para la renovación de nuestra oficina necesitamos:
- 8 ordenadores de sobremesa (i5, 16GB RAM, 512GB SSD)
- 8 monitores de 24 pulgadas
- Teclados y ratones inalámbricos
- 1 impresora multifunción láser color

No tenemos prisa, puede ser entrega en mayo.
Presupuesto aproximado: 6000€
Forma de pago: Contrareembolso o tarjeta

Ana Martínez
Directora Administrativa
Comercial del Norte SL
ana.martinez@pyme.es
Tel: 987 654 321

INSTRUCCIONES:
- Extrae la información de cada email en formato estructurado
- Identifica: cliente, fecha, productos/servicios, cantidades, presupuesto, fecha entrega, método pago, contacto
- Si algún dato no está presente, usa null
- Calcula el presupuesto total sumando todos los emails
- Clasifica cada pedido por urgencia (alta/media/baja) según la fecha de entrega

Responde ÚNICAMENTE en formato JSON con esta estructura exacta:
{
  "pedidos": [
    {
      "email_id": 1,
      "cliente": {
        "nombre": "nombre completo",
        "empresa": "nombre empresa o null",
        "email": "email",
        "telefono": "telefono o null",
        "cif": "CIF o null"
      },
      "fecha_solicitud": "YYYY-MM-DD",
      "productos": [
        {
          "descripcion": "descripción producto",
          "cantidad": número,
          "categoria": "hardware/software/servicio"
        }
      ],
      "presupuesto": {
        "minimo": número_o_null,
        "maximo": número_o_null,
        "moneda": "EUR"
      },
      "fecha_entrega": "YYYY-MM-DD o null",
      "urgencia": "alta/media/baja",
      "metodo_pago": "descripción o null",
      "notas": "información adicional relevante o null"
    }
  ],
  "resumen": {
    "total_pedidos": número,
    "presupuesto_total_min": número,
    "presupuesto_total_max": número,
    "pedidos_urgentes": número,
    "categorias": {
      "hardware": número_de_items,
      "software": número_de_items,
      "servicio": número_de_items
    }
  }
}

IMPORTANTE:
- NO uses formato markdown
- NO uses ```json o ```
- SOLO responde con el objeto JSON puro
- Todos los números deben ser numéricos, no strings
- Las fechas deben estar en formato ISO (YYYY-MM-DD)
- Calcula correctamente las sumas en el resumen
```

**Resultado:** 🔴 GPT-4o ganó (87 vs 82)

---

### Prueba 4: Servicio al Cliente

**Objetivo:** Responder a una queja de cliente con empatía y profesionalismo.

**Prompt:**
```
Eres un agente de atención al cliente de TechStore. Responde al siguiente email de un cliente frustrado.

EMAIL DEL CLIENTE:
De: carlos.ruiz@email.com
Asunto: Problema con mi pedido #TR-2847
Fecha: 20 de marzo de 2024

"Hola,

Hace más de 2 semanas que hice un pedido de un Lenovo ThinkPad X1 Carbon Gen 11 
(pedido #TR-2847) y todavía no lo he recibido. En la web dice 'En proceso' pero 
no he recibido ninguna actualización. Necesito el portátil urgentemente para mi 
nuevo trabajo que empieza el lunes. ¿Qué está pasando?

Carlos Ruiz"

CONTEXTO INTERNO:
- Hubo un retraso por falta de stock (ya solucionado)
- El producto está listo para envío mañana
- Transportista: DHL Express (1-2 días de entrega)
- URL de seguimiento: https://techstore.com/tracking/TR-2847
- Puedes ofrecer 10% descuento en próxima compra

INSTRUCCIONES:
- Sé empático y reconoce la frustración del cliente
- Explica brevemente la causa del retraso
- Ofrece solución concreta con timeframe
- Incluye información de seguimiento
- Ofrece compensación
- Mantén tono profesional pero cálido

Responde en JSON:
{
  "asunto": "Asunto del email de respuesta",
  "cuerpo": "Texto completo de la respuesta (usar \\n para saltos de línea)",
  "tono": "descripción del tono usado",
  "compensacion_ofrecida": "qué compensación ofreciste",
  "problema_resuelto": true/false,
  "tiempo_respuesta_estimado": "estimación de cuándo recibirá el producto"
}

NO markdown, solo JSON puro.
```

**Resultado:** 🔴 GPT-4o ganó (95 vs 88)

---

### Prueba 5: Procesamiento de PDFs

*(Prompt disponible en el repositorio - similar estructura)*

**Resultado:** 🔴 GPT-4o ganó (92 vs 85)

---

### Prueba 6: Workflow Completo End-to-End

*(Prompt disponible en el repositorio - combina múltiples tareas)*

**Resultado:** 🔴 GPT-4o ganó (94 vs 90)

## 🚀 Instalación y Uso

### Prerrequisitos
```bash
# Hardware recomendado
- GPU: 8GB VRAM mínimo (para modelos 7B-14B)
- RAM: 32GB (para Mixtral 8x7B)
- Disco: 60GB libres

# Software
- Python 3.10+
- Ollama
- n8n (opcional)
- Node.js 18+ (para n8n)
```

### 1. Instalar Ollama
```bash
# Linux/Mac
curl -fsSL https://ollama.com/install.sh | sh

# Windows
# Descargar desde https://ollama.com/download
```

### 2. Descargar Modelos
```bash
# Para código (Prueba 1)
ollama pull qwen2.5-coder:7b
ollama pull deepseek-coder:6.7b-instruct

# Para sentimiento (Prueba 2)
ollama pull llama3.1:8b
ollama pull mistral:7b-instruct-v0.3

# Para datos (Prueba 3)
ollama pull qwen2.5:14b-instruct-q4_K_M
ollama pull mixtral:8x7b-instruct-v0.1-q4_K_M

# Para servicio al cliente (Prueba 4)
# Reutiliza llama3.1:8b y mistral:7b-instruct-v0.3

# Tiempo total descarga: ~30-45 min
# Espacio total: ~55GB
```

### 3. Clonar Repositorio
```bash
git clone https://github.com/tuusuario/gpt4o-vs-local-models.git
cd gpt4o-vs-local-models
```

### 4. Instalar Dependencias
```bash
pip install -r requirements.txt
```

### 5. Configurar API Keys
```bash
# Crear archivo .env
cp .env.example .env

# Editar .env y añadir:
OPENAI_API_KEY=tu_api_key_aqui
ANTHROPIC_API_KEY=tu_api_key_aqui  # Opcional, para evaluadores
```

### 6. Ejecutar Pruebas
```bash
# Prueba 1: Código
python scripts/test_1_code.py

# Prueba 2: Sentimiento
python scripts/test_2_sentiment.py

# Prueba 3: Extracción
python scripts/test_3_extraction.py

# Prueba 4: Servicio
python scripts/test_4_customer_service.py

# Ejecutar todas
python run_all_tests.py
```

## 📁 Estructura del Proyecto
```
gpt4o-vs-local-models/
├── README.md
├── requirements.txt
├── .env.example
├── prompts/
│   ├── prompt_1_code.txt
│   ├── prompt_2_sentiment.txt
│   ├── prompt_3_extraction.txt
│   ├── prompt_4_customer_service.txt
│   ├── prompt_5_pdf.txt
│   └── prompt_6_workflow.txt
├── scripts/
│   ├── code_battle_analysis.py
│   ├── sentiment_battle_analysis.py
│   ├── data_extraction_analysis.py
│   ├── customer_service_analysis.py
│   └── run_all_tests.py
├── n8n_workflows/
│   ├── workflow_test_1.json
│   ├── workflow_test_2.json
│   └── ...
└── results/
    ├── test_1_results.json
    ├── test_2_results.json
    └── ...
```

## 🎯 Filosofía del Experimento

### Por qué diferentes modelos para cada prueba

No usé el mismo modelo local para todas las pruebas porque:

1. **Especialización importa**: Un modelo entrenado en código será mejor en programación
2. **Producción real**: Así es como usarías modelos en un entorno real
3. **Evita cherry-picking**: Si varios modelos especializados compiten bien, valida la estrategia
4. **Optimiza recursos**: Modelos pequeños para tareas simples, grandes para complejas

### Evaluación Imparcial

Para evitar sesgos:
- Usé Claude para generar scripts de evaluación automática
- Criterios objetivos y puntuación numérica
- Claude no sabía qué modelo generó cada output
- Scripts disponibles para replicar

## 💡 Conclusiones Clave

### ✅ Cuándo usar Modelos Locales

- **Código simple a medio**: Qwen Coder es igual o mejor
- **Clasificación/análisis básico**: Llama/Mistral son excelentes
- **Alto volumen**: El ahorro justifica la configuración inicial
- **Privacidad crítica**: Datos nunca salen de tu servidor
- **Prototipado rápido**: Iteraciones gratis

### ✅ Cuándo usar GPT-4o

- **Tareas mission-critical**: Servicio al cliente, legal, médico
- **Contextos muy largos**: GPT-4o tiene 128K tokens
- **Razonamiento complejo**: Mejor en multi-step reasoning
- **Sin recursos técnicos**: No quieres configurar servidores
- **Máxima fiabilidad**: Menos errores, más consistente

### 🎯 Estrategia Recomendada: Híbrido
```
60% → Modelos locales (tareas rutinarias)
30% → GPT-4o mini (equilibrio precio/calidad)
10% → GPT-4o full (casos críticos)

Ahorro: 87% vs usar solo GPT-4o
```

## 📊 Datos Completos

Todos los outputs reales, puntuaciones detalladas y análisis están en:
- `/results/detailed_scores.json`
- `/results/analysis_reports.md`

## 🤝 Contribuir

¿Quieres añadir más pruebas o modelos?

1. Fork el repositorio
2. Crea tu branch (`git checkout -b feature/nueva-prueba`)
3. Commit tus cambios (`git commit -m 'Añade prueba X'`)
4. Push al branch (`git push origin feature/nueva-prueba`)
5. Abre un Pull Request

## 📜 Licencia

MIT License - Úsalo libremente, con atribución

## 👤 Autor

**David Beltrán**
- YouTube: [@DavidBeltran](TU_CANAL)
- GitHub: [@tuusuario](https://github.com/tuusuario)
- LinkedIn: [Tu LinkedIn](TU_LINKEDIN)

Documentando mi camino a 10,000 horas en IA 🚀

## ⭐ Apoya el Proyecto

Si este experimento te ha sido útil:
- ⭐ Dale estrella al repo
- 🔄 Compártelo con tu equipo
- 📹 Suscríbete al canal
- 💬 Déjame saber qué otras comparaciones quieres ver

---

**Última actualización:** Diciembre 2024
