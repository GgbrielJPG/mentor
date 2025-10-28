
📈 Roadmap de Desenvolvimento

🧩 Fase 1 — MVP (funcional)

Objetivo: fazer o modelo entender prompts e gerar código + explicação.

1. [ ] Configurar ambiente e dependências (ollama, pandas, requests).


2. [ ] Criar classe LlamaInterface para comunicação com LLaMA.


3. [ ] Implementar DataMentor.explain_and_propose(df, prompt):

Converter DataFrame em resumo (colunas, tipos, amostra).

Montar prompt estruturado para o LLaMA.

Retornar JSON {code, explanation}.



4. [ ] Criar função mentor.execute(df, code) com exec() seguro.


5. [ ] Adicionar exemplo prático em examples/.




---

🧩 Fase 2 — Versão Educacional

Objetivo: transformar em mentor explicativo.

1. [ ] Melhorar o prompt base para forçar o modelo a gerar comentários passo a passo.


2. [ ] Adicionar múltiplas abordagens (“pandas vs sklearn”).


3. [ ] Criar modo “verbose” para incluir justificativas detalhadas.


4. [ ] Implementar exportação da resposta em Markdown.




---

🧩 Fase 3 — Segurança e UX

Objetivo: permitir uso seguro e interativo.

1. [ ] Implementar sandbox.py com RestrictedPython para executar código com segurança.


2. [ ] Adicionar logs coloridos (rich) e CLI (typer).


3. [ ] Adicionar opção execute=False para só exibir código.


4. [ ] Adicionar testes unitários básicos com pytest.




---

🧩 Fase 4 — Evolução

Objetivo: tornar o projeto digno de portfólio profissional.

1. [ ] Publicar no PyPI (llama-data-mentor).


2. [ ] Criar notebook interativo no examples/ com Streamlit.


3. [ ] Adicionar suporte a “chains” (tratamentos sequenciais).


4. [ ] Documentar com docstrings + gerar docs com mkdocs.


