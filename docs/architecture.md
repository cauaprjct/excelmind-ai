# Arquitetura do ExcelMind AI

## Visao Geral

O ExcelMind AI e composto por camadas bem definidas:

```
+--------------------------------------------------------------+
|                    Interface Layer                            |
|   +---------------------+  +---------------------+          |
|   |    Streamlit Web    |  |     Typer CLI       |          |
|   |   (src/main.py)     |  |   (src/cli.py)      |          |
|   +---------------------+  +---------------------+          |
+--------------------------------------------------------------+
|                   UI Components                              |
|              src/excelmind_ai/ui/components.py               |
+--------------------------------------------------------------+
|                    Core Engine                               |
|   +--------------+ +--------------+ +--------------+        |
|   | Data Loader  | |  Analyzer    | | Visualizer   |        |
|   |  (Polars)    | |  (Polars)    | |  (Plotly)    |        |
|   +--------------+ +--------------+ +--------------+        |
|   +--------------+ +--------------+ +--------------+        |
|   | Auto Analyzer| |   Reports    | |  Advanced    |        |
|   |  (KPIs)      | |(Excel+PDF)   | |  Analytics   |        |
|   +--------------+ +--------------+ +--------------+        |
+--------------------------------------------------------------+
|                   AI Agents (LangGraph)                      |
|              src/excelmind_ai/agents/graph.py                |
|   Interprete --> Planner --> Responder                      |
+--------------------------------------------------------------+
|                   LLM Factory                                |
|              src/excelmind_ai/llm/                           |
|   Gemini (padrao) | OpenAI | Anthropic Claude               |
+--------------------------------------------------------------+
```

## Modulos Principais

### 1. Core Engine (`src/excelmind_ai/core/`)

| Modulo | Responsabilidade |
|--------|------------------|
| `data_loader.py` | Carrega Excel/CSV com deteccao de abas |
| `data_analyzer.py` | Analise estatistica e perfil de colunas |
| `auto_analyzer.py` | KPIs, tendencias, anomalias, correlacoes |
| `visualizer.py` | Graficos Plotly automaticos |
| `report_generator.py` | Exportacao Excel e PDF |
| `advanced_analytics.py` | Previsao temporal, comparacao de arquivos |

### 2. Agentes de IA (`src/excelmind_ai/agents/`)

O grafo LangGraph usa 3 agentes em sequencia:

1. **Interprete**: Analisa a pergunta e valida com o schema
2. **Planner**: Planeja operacoes baseado em keywords
3. **Responder**: Formata resposta rica em PT-BR

### 3. LLM Factory (`src/excelmind_ai/llm/`)

Factory para criacao de LLMs com fallback automatico:

- **Prioridade**: Gemini > OpenAI > Claude
- **Fallback**: Se um provedor falhar, tenta o proximo
- **Configuracao**: Via arquivo `.env`

### 4. Interface Web (`src/excelmind_ai/main.py`)

5 abas principais:
1. Preview dos Dados
2. Analise Inteligente
3. Graficos Automaticos
4. Relatorios (Excel/PDF)
5. Chat com IA

### 5. Interface CLI (`src/excelmind_ai/cli.py`)

Comandos disponiveis:
- `excelmind analyze` - Analise completa
- `excelmind chat` - Chat interativo
- `excelmind report` - Gerar relatorios
- `excelmind compare` - Comparar arquivos
- `excelmind serve` - Iniciar Streamlit
- `excelmind info` - Informacoes do sistema

## Fluxo de Dados

```
[Arquivo] --> [DataLoader] --> [pl.DataFrame]
                                    |
                    +---------------+---------------+
                    v               v               v
              [Analyzer]     [AutoAnalyzer]   [Visualizer]
                    |               |               |
                    +---------------+---------------+
                                    v
                            [ReportGenerator]
                                    |
                    +---------------+---------------+
                    v                               v
               [Excel]                           [PDF]
```

## Decisoes Tecnicas

### Polars vs Pandas
- **Performance**: 10-50x mais rapido em grandes planilhas
- **Lazy Evaluation**: Otimizacao automatica de queries
- **Type Safety**: Schema tipado

### Streamlit
- Prototipagem rapida
- Componentes interativos
- Cache inteligente

### Plotly
- Graficos interativos
- Exportacao para PNG
- Temas customizaveis

### LangGraph
- Agentes com estado
- Multi-turn conversations
- Debugging facilitado

## Configuracao

Arquivo `.env`:
```
GEMINI_API_KEY=...    # Provedor padrao (gratuito)
OPENAI_API_KEY=...    # Alternativa 1
ANTHROPIC_API_KEY=... # Alternativa 2
LLM_PROVIDER=gemini   # Escolha do provedor
TEMPERATURE=0.2       # Temperatura do modelo
```

## Performance

- **Cache**: Analises cacheadas por 1h
- **Lazy Loading**: Datasets > 50k registros
- **Limite**: Arquivos ate 200 MB
- **Preview**: Maximo 10k linhas na visualizacao