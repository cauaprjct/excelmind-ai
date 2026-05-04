# Guia de Contribuicao

Obrigado pelo interesse em contribuir com o ExcelMind AI! Este documento explica como voce pode ajudar.

## Como Contribuir

### Reportar Bugs

1. Verifique se o bug ja foi reportado nas [Issues](../../issues)
2. Se nao, crie uma nova Issue com:
   - Descricao clara do problema
   - Passos para reproduzir
   - Comportamento esperado vs atual
   - Versao do Python e sistema operacional
   - Logs de erro (se houver)

### Sugerir Melhorias

1. Crie uma Issue descrevendo sua ideia
2. Explique o beneficio para os usuarios
3. Se possivel, inclua exemplos de uso

### Enviar Codigo

1. **Fork** o repositorio
2. Crie uma **branch** para sua feature:
   ```bash
   git checkout -b feature/minha-feature
   ```
3. Faca suas alteracoes seguindo as convencoes do projeto
4. Adicione **testes** para novas funcionalidades
5. Execute os testes:
   ```bash
   pytest tests/ -v
   ```
6. Commit suas mudancas:
   ```bash
   git commit -m "Adiciona minha feature"
   ```
7. Push para sua branch:
   ```bash
   git push origin feature/minha-feature
   ```
8. Abra um **Pull Request**

## Configuracao do Ambiente de Desenvolvimento

```bash
# Clone o repositorio
git clone https://github.com/SEU_USUARIO/excelmind-ai.git
cd excelmind-ai

# Crie o ambiente virtual
python -m venv .venv
source .venv/bin/activate  # Linux/Mac
# ou
.venv\Scripts\activate  # Windows

# Instale em modo de desenvolvimento
pip install -e ".[dev]"
```

## Convencoes de Codigo

### Estilo

- Use **Black** para formatacao automatica
- Use **Ruff** para linting
- Siga PEP 8

```bash
# Formatar codigo
black src/ tests/

# Verificar linting
ruff check src/ tests/
```

### Commits

- Use mensagens descritivas em portugues
- Comece com verbo no imperativo: "Adiciona", "Corrige", "Atualiza"
- Exemplos:
  - `Adiciona suporte a arquivos .ods`
  - `Corrige erro de encoding em CSV`
  - `Atualiza documentacao do README`

## Estrutura do Projeto

```
excelmind-ai/
|-- src/excelmind_ai/
|   |-- core/           # Logica de negocios (analise, visualizacao)
|   |-- agents/         # Agentes de IA (LangGraph)
|   |-- llm/            # Provedores de LLM (Gemini, OpenAI, Claude)
|   |-- ui/             # Componentes de interface
|   +-- utils/          # Funcoes utilitarias
|-- tests/              # Testes automatizados
|-- docs/               # Documentacao adicional
|-- examples/           # Arquivos de exemplo
+-- scripts/            # Scripts auxiliares
```

## Codigo de Conduta

- Seja respeitoso com outros contribuidores
- Aceite feedback construtivo
- Foque em melhorar o projeto

---

Obrigado por contribuir!