# Causal_QA.PT

Este repositório contém o projeto Causal_QA.PT.

## Instalação

Para instalar as dependências do projeto:

```bash
pip install -r requirements.txt
```

**Nota:** Após instalar, você também precisará executar `python -m spacy download pt_core_news_sm` para baixar o modelo em português do spaCy.

## Configuração

### Variáveis de Ambiente

O projeto utiliza APIs externas que requerem chaves de autenticação. Para configurar:

1. Copie o arquivo de exemplo:
   ```bash
   cp .env.example .env
   ```

2. Edite o arquivo `.env` e adicione suas chaves de API:
   ```
   OPENAI_API_KEY=sua-chave-da-openai-aqui
   ```

3. O arquivo `.env` está no `.gitignore` e **nunca** será versionado por segurança.

### Notebooks

Os notebooks carregarão automaticamente as variáveis do arquivo `.env` usando a biblioteca `python-dotenv`.
