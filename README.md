Projeto de Integração Contínua com GitHub Actions e Act

Este projeto demonstra a criação de um pipeline de Integração Contínua (CI) utilizando GitHub Actions e a execução local dos workflows com act, utilizando Docker Desktop e Windows Subsystem for Linux (WSL).

O objetivo é simular um ambiente real de CI, executando os workflows localmente antes do envio para o GitHub.

Workflow 1 — Hello Local

Arquivo: .github/workflows/01-hello-local.yml

Este workflow simples foi criado para validar a execução local com o act.

Etapas executadas:
Exibir mensagem inicial
Verificar versão do Node
Exibir mensagem final
Execução local:
act -W .github/workflows/01-hello-local.yml

Esse teste comprovou que o Docker, WSL e act estavam configurados corretamente.

Workflow 2 — Pipeline Principal (DAG)

Arquivo: .github/workflows/02-pipeline-principal.yml

Este workflow representa um pipeline de CI mais completo, organizado em formato de DAG (Directed Acyclic Graph), com múltiplos jobs e dependências.

Estrutura do Pipeline
Estágio	Job	Função
0	setup-e-lint	Preparação do ambiente e lint
1	testes-unitarios	Execução de testes
1	scan-de-seguranca	Verificação de segurança
2	build-e-deploy	Build e simulação de deploy

Os jobs de estágio 1 executam em paralelo após o setup, e o deploy só ocorre após todos concluírem com sucesso.

Execução local do pipeline:

Listar os jobs:

act -l

Executar o pipeline:

act

Isso permite validar todo o fluxo de CI sem precisar subir código para o GitHub.

Conceitos aplicados:
Integração Contínua (CI)
GitHub Actions
Execução local com act
Uso de Docker para simular runners
Uso de WSL como ambiente Linux
Organização de pipeline em DAG
Versionamento com Git e GitHub
