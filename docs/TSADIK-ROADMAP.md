# Tsadik OmniHub — Plano de fundação

> Documento de planejamento do fork pessoal de OmniGet. Nome de trabalho: Tsadik OmniHub. O núcleo original permanece identificável e preservado; personalizações devem ser modulares.

## Estado verificado em 2026-11-20

- Fork público: https://github.com/alexbri27/omniget
- Repositório upstream: https://github.com/tonhowtf/omniget
- Branch padrão: main
- Comparação main do fork vs tonhowtf:main: idêntica (0 commits à frente/atrás).
- Branch de trabalho criada: feature/tsadik-foundation.
- Stack declarada: Tauri 2, Rust, SvelteKit/Svelte 5, MCP local.
- Toolchain Rust fixada em 1.97.0; pnpm 10.29.3; Node 22.17+ ou 24+.
- Licença declarada: GPL-3.0.
- Skills: o parser exige SKILL.md com frontmatter YAML contendo name e description; nome minúsculo, números e hífens, até 64 caracteres. O instalador copia para uma pasta de skills, verifica conteúdo e pode estacionar skills de alto risco para confirmação.
- Issues estão desativadas neste fork (GitHub API responde 410); backlog fica versionado em docs até habilitar Issues ou escolher outro tracker.

## Objetivo

Evoluir o OmniGet para um ambiente pessoal de trabalho assistido por agentes, conteúdo, biblioteca e operações comerciais, sem comprometer segurança, estabilidade, compatibilidade upstream ou direitos de terceiros.

## Princípios arquiteturais

1. **Upstream-first:** manter main sincronizada com upstream/main; desenvolver em branches próprias.
2. **Extensão antes de alteração:** preferir Skills, configurações, prompts e módulos isolados a mudanças no núcleo.
3. **Core-first:** quando uma funcionalidade realmente exigir código, implementar lógica de domínio em omniget-core e expor interfaces finas via Tauri/MCP, seguindo ARCHITECTURE.md.
4. **Permissões mínimas:** separar leitura, escrita e ações externas; usar tokens individuais e aprovações humanas.
5. **Dados segregados:** separar dados de ministério/conteúdo, afiliados, comercial e conhecimento; não misturar credenciais ou bases.
6. **Rastreabilidade:** cada tarefa tem responsável, branch, testes, critérios de aceite e evidências.
7. **Compatibilidade:** não quebrar builds Windows/macOS/Linux para atender apenas Fedora.
8. **GPL e atribuição:** manter avisos, licença e histórico do upstream; identificar claramente alterações próprias. Não presumir que a licença autoriza uso de marcas/logos de terceiros.

## Visão funcional

### A. Estúdio de conteúdo e ministério
- Projetos de eBooks, estudos, cursos, vídeos, roteiros, PDFs e materiais de ensino.
- Modelos editoriais, revisão bíblica/referencial e controle de versões.
- Fluxo: ideia → pesquisa/fontes → estrutura → rascunho → revisão → arte/exportação → publicação aprovada.
- Nunca publicar ou enviar conteúdo em nome do usuário sem confirmação.

### B. Estúdio de afiliados
- Organização de campanhas, produtos, links, códigos, criativos, calendário e métricas.
- Separar programas Temu, Shopee e Amazon por regras e termos próprios.
- Verificar políticas vigentes antes de produzir alegações, descontos ou CTAs.
- Não automatizar spam, comentários, avaliações falsas, burlar políticas ou usar marcas/palavras-chave de modo proibido.

### C. Gestão comercial B2B
- CRM de empresas/clientes, contatos, vendedores, regiões, pipeline e agenda.
- Registro de visitas, propostas, pedidos, acompanhamento e indicadores.
- Acesso por perfil; trilha de auditoria; exportações controladas.
- Não criar integração com dados reais antes de definir fonte, base legal, acesso e backup.

### D. Biblioteca de conhecimento
- Indexar arquivos próprios autorizados: PDFs, DOCX, planilhas, notas, transcrições e referências.
- Metadados, tags, pesquisa semântica e links de origem.
- Não copiar conteúdo protegido de plataformas sem autorização.

### E. Orquestração de agentes
- Um agente líder decompõe tarefas e delega subtarefas isoladas.
- Especialistas: arquitetura, skills, conteúdo, afiliados, comercial, integração e QA/segurança.
- Cada agente recebe objetivo, contexto mínimo, arquivos permitidos, proibições e formato de entrega.
- Agente não aprova a própria ação; operações externas e destrutivas aguardam confirmação humana.

## Arquitetura-alvo

- **Camada 0 — Upstream OmniGet:** base original, atualizada separadamente.
- **Camada 1 — Tsadik Foundation:** documentação, skills e configuração pessoal sem alteração de runtime.
- **Camada 2 — Domínios:** conteúdo, afiliados, comercial, biblioteca.
- **Camada 3 — Integrações:** MCP, OpenCode e outros agentes após compatibilidade comprovada.
- **Camada 4 — Interface:** dashboards e experiências próprias apenas quando requisitos e pontos de extensão estiverem validados.

Não acoplar o projeto a Commander/OpenCode/OpenBot por suposição: confirmar protocolos, ferramentas e versões no ambiente real.

## Backlog inicial

| ID | Épico / tarefa | Prioridade | Dependência | Critério de aceite |
|---|---|---:|---|---|
| TSH-001 | Auditoria da arquitetura, módulos e riscos | P0 | — | Relatório técnico e mapa de pontos de extensão |
| TSH-002 | Diagnóstico do ambiente Fedora (Node, pnpm, Rust, libs) | P0 | TSH-001 | Relatório de versões e comandos reproduzíveis |
| TSH-003 | Política de branches e sincronização upstream | P0 | — | main preservada; feature branch isolada |
| TSH-004 | Validar instalação e scanner de Skills | P0 | TSH-001 | Skill de teste validada sem risco alto |
| TSH-005 | Instalar e testar skill tsadik-omniget-workflow | P0 | TSH-004 | Skill reconhecida e instruções acionáveis |
| TSH-010 | Inventário MCP, scopes, tokens e aprovações | P0 | TSH-001 | Matriz ferramenta × permissão × risco |
| TSH-011 | Inventário Canvas, Lead Mode e jobs | P1 | TSH-001 | Fluxo de agentes documentado |
| TSH-020 | Prova de build Fedora em perfil isolado | P1 | TSH-002 | pnpm verify e pnpm tauri dev documentados |
| TSH-030 | Especificar Estúdio de Conteúdo | P1 | TSH-005 | Requisitos, modelos e fluxo editorial |
| TSH-040 | Especificar Estúdio de Afiliados | P1 | TSH-005 | Requisitos e matriz de políticas por programa |
| TSH-050 | Especificar CRM B2B | P1 | TSH-005 | ERD, papéis, pipeline e critérios de aceite |
| TSH-060 | Especificar Biblioteca de Conhecimento | P1 | TSH-005 | Fontes, indexação, permissões e retenção |
| TSH-070 | Protocolo de orquestração multiagente | P1 | TSH-010, TSH-011 | Contrato de tarefa, handoff e relatório |
| TSH-080 | QA, testes, segurança e release checklist | P0 | Todos | pnpm verify sem regressões e aprovação humana |

## Delegação proposta

| Papel | Missão | Entregável |
|---|---|---|
| Supervisor (ChatGPT) | Planejar, decompor, revisar evidências e controlar escopo | Decisões, critérios de aceite, revisão |
| Líder/orquestrador local | Distribuir tarefas e consolidar estado | Quadro de tarefas e relatório diário |
| Arquiteto Rust/Tauri | Mapear core, comandos, eventos e integração MCP | ADRs e mapa técnico |
| Especialista Skills | Criar, validar e testar Skills | SKILL.md + testes |
| Especialista frontend | Avaliar SvelteKit, stores, i18n e UX | Protótipos e mudanças isoladas |
| Especialista de domínio | Requisitos de conteúdo/afiliados/CRM/biblioteca | PRDs, fluxos e modelos |
| QA/segurança | Testes, permissões, dados, dependências e regressões | Relatório de QA e riscos |

A delegação só é considerada executada quando o gerenciador de agentes real recebe a tarefa e devolve evidência. A disponibilidade do Commander/OpenCode/OpenBot ainda precisa ser confirmada no computador.

## Fluxo de trabalho

1. Supervisor define tarefa e critérios.
2. Líder escolhe agente e cria branch/worktree isolada.
3. Agente lê instruções e limita-se ao escopo.
4. Agente entrega diff, testes, riscos e evidências.
5. QA revisa e executa checks pertinentes.
6. Supervisor aprova ou solicita correções.
7. Usuário autoriza merge, publicação, instalação ou ação externa.

## Definition of Done

- Escopo e arquivos afetados identificados.
- Código/documentação revisados e sem segredos.
- Testes apropriados executados e resultados informados.
- Licenças e políticas respeitadas.
- Sem alterações não relacionadas.
- Aprovação humana para merge, release, instalação ou operações externas.

## Próximo passo

Executar TSH-001 e TSH-002 localmente. Antes disso, não modificar o runtime nem instalar dependências no Fedora. O fork ainda está idêntico ao upstream; a branch de fundação é o primeiro espaço isolado de trabalho.
