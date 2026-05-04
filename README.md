# ExcelMind AI

<p align="center">
  <img src="assets/logo.svg" alt="ExcelMind AI Logo" width="120">
</p>

<p align="center">
  <a href="#"><img src="https://img.shields.io/badge/python-3.11%2B-blue.svg" alt="Python 3.11+"></a>
  <a href="#"><img src="https://img.shields.io/badge/license-MIT-green.svg" alt="License"></a>
  <img src="https://img.shields.io/badge/Polars-Data%20Engine-ff69b4.svg" alt="Polars">
  <img src="https://img.shields.io/badge/Streamlit-Web%20App-ff4b4b.svg" alt="Streamlit">
  <img src="https://img.shields.io/badge/LangGraph-AI%20Agents-10a37f.svg" alt="LangGraph">
</p>

---

## O que e o ExcelMind AI?

**ExcelMind AI** e uma ferramenta que analisa suas planilhas Excel e CSV de forma inteligente usando Inteligencia Artificial. Com ela voce pode:

- **Carregar planilhas** Excel (.xlsx, .xls) ou CSV de qualquer tamanho
- **Ver analises automaticas**: KPIs, tendencias, anomalias e correlacoes
- **Criar graficos** interativos automaticamente
- **Conversar com a IA** sobre seus dados em portugues
- **Gerar relatorios** profissionais em Excel e PDF
- **Usar via navegador** (interface visual) ou **terminal** (linha de comando)

---

## Guia Rapido de Instalacao

### Passo 1: Pre-requisitos

Voce precisa ter instalado:
- **Python 3.11 ou superior** - [Baixe aqui](https://www.python.org/downloads/)
- **Git** (opcional) - [Baixe aqui](https://git-scm.com/downloads)

### Passo 2: Baixar o projeto

**Opcao A - Com Git:**
```bash
git clone https://github.com/cauaprjct/excelmind-ai.git
cd excelmind-ai
```

**Opcao B - Download direto:**
1. Clique no botao verde "Code" > "Download ZIP"
2. Extraia o arquivo
3. Abra o terminal na pasta extraida

### Passo 3: Criar ambiente virtual

**Windows (PowerShell):**
```powershell
python -m venv .venv
.venv\Scripts\Activate.ps1
```

**Windows (CMD):**
```cmd
python -m venv .venv
.venv\Scripts\activate.bat
```

**Linux/Mac:**
```bash
python3 -m venv .venv
source .venv/bin/activate
```

### Passo 4: Instalar dependencias

```bash
pip install --upgrade pip
pip install -e .
```

### Passo 5: Configurar a IA (opcional)

Para usar o chat com IA, voce precisa de uma chave de API. O mais facil e usar o **Google Gemini** (gratuito):

1. Acesse https://ai.google.dev/
2. Crie uma conta e gere uma API Key
3. Copie o arquivo de configuracao:
   ```bash
   cp .env.example .env
   ```
4. Edite o arquivo `.env` e adicione sua chave:
   ```
   GEMINI_API_KEY=sua_chave_aqui
   ```

> **Nota:** O chat com IA e opcional. Todas as outras funcionalidades (analise, graficos, relatorios) funcionam sem API key.

---

## Como Usar

### Interface Web (mais facil para iniciantes)

Execute o comando:

```bash
streamlit run src/excelmind_ai/main.py
```

O navegador abrira automaticamente em `http://localhost:8501`.

**O que voce pode fazer:**
1. Arraste sua planilha na area de upload (lado esquerdo)
2. Veja os KPIs automaticos no topo
3. Navegue pelas abas: Preview, Analise, Graficos, Relatorios, Chat

### Interface de Linha de Comando (CLI)

Para usuarios mais avancados:

```bash
# Analise completa no terminal
excelmind analyze sua_planilha.xlsx

# Chat interativo
excelmind chat sua_planilha.xlsx

# Gerar relatorios
excelmind report sua_planilha.xlsx --format=both

# Comparar arquivos
excelmind compare janeiro.xlsx fevereiro.xlsx

# Iniciar interface web
excelmind serve

# Ver informacoes do sistema
excelmind info
```

---

## Licenca

Este projeto esta sob a licenca MIT. Veja o arquivo [LICENSE](LICENSE) para detalhes.
