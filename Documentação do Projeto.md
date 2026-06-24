# NEXADESK AI
## Seu copiloto inteligente para o conhecimento da empresa

**Disciplina:** IA Generativa Aplicada ao Desenvolvimento
**Autor:** Marcos Detrano Rodrigues Junior
**Orientador(a):** Prof.(a) Patricia Miscolcz
**Instituição:** UniFecaf— 2026

---

# SUMÁRIO

1. [Introdução](#1-introdução)
2. [Objetivos](#2-objetivos)
3. [Fundamentação Teórica](#3-fundamentação-teórica)
4. [Desenvolvimento do Projeto](#4-desenvolvimento-do-projeto)
5. [Ferramentas Utilizadas](#5-ferramentas-utilizadas)
6. [Como a IA Auxiliou o Desenvolvimento](#6-como-a-ia-auxiliou-o-desenvolvimento)
7. [Funcionalidades do Sistema](#7-funcionalidades-do-sistema)
8. [Benefícios Obtidos](#8-benefícios-obtidos)
9. [Limitações Encontradas](#9-limitações-encontradas)
10. [Aspectos Éticos e Governança da IA](#10-aspectos-éticos-e-governança-da-ia)
11. [Trabalhos Futuros](#11-trabalhos-futuros)
12. [Conclusão](#12-conclusão)
13. [Referências Bibliográficas](#13-referências-bibliográficas)

---

## RESUMO

O presente trabalho descreve o desenvolvimento do **NexaDesk AI**, um copiloto corporativo baseado em Inteligência Artificial Generativa, concebido para responder, em linguagem natural, dúvidas recorrentes de colaboradores sobre políticas, processos e procedimentos internos de uma organização. O projeto foi construído no contexto da disciplina de IA Generativa Aplicada ao Desenvolvimento e possui dois propósitos complementares: entregar um produto SaaS funcional, com aparência profissional, e demonstrar, de forma transparente, como ferramentas de IA Generativa participaram ativamente de todas as etapas da sua construção. A aplicação foi implementada utilizando React, TypeScript, Vite, TailwindCSS v4 e TanStack Start, adotando uma arquitetura modular composta por uma camada de dados (base de conhecimento simulada), uma camada de agente (responsável pelo *retrieval* e pela montagem dos *prompts*) e uma camada de interface conversacional. O agente implementa um fluxo simplificado de Retrieval-Augmented Generation (RAG). Os resultados indicam que a adoção de IA Generativa reduziu significativamente o tempo de entrega do MVP, ampliou a qualidade visual da interface e permitiu produzir documentação técnica detalhada, mantendo a aderência a boas práticas de engenharia de software, governança e segurança aplicáveis a modelos de linguagem.

**Palavras-chave:** Inteligência Artificial Generativa. Large Language Models. Retrieval-Augmented Generation. Engenharia de Prompt. Desenvolvimento Assistido por IA. Copiloto Corporativo.

## ABSTRACT

This work describes the development of **NexaDesk AI**, a corporate copilot powered by Generative Artificial Intelligence, designed to answer, in natural language, recurring employee questions about internal policies, processes, and procedures of an organization. The application was implemented using React, TypeScript, Vite, TailwindCSS v4, and TanStack Start, following a modular architecture composed of a data layer, an agent layer (Retrieval-Augmented Generation pipeline), and a conversational interface. Tools such as Lovable, Claude, ChatGPT, and GitHub Copilot were employed throughout development, and their contributions were documented in terms of time saved, code quality, and influence on architectural decisions.

**Keywords:** Generative Artificial Intelligence. Large Language Models. Retrieval-Augmented Generation. Prompt Engineering. AI-Assisted Development. Corporate Copilot.

---

# 1. INTRODUÇÃO

## 1.1 IA Generativa e transformação digital

A última década consolidou a transformação digital como vetor estratégico para organizações de todos os portes. Processos antes manuais foram automatizados, sistemas legados migraram para a nuvem e a quantidade de dados produzidos cresceu de forma exponencial. Nesse cenário, a emergência da **Inteligência Artificial Generativa** representa, segundo diversos autores, uma ruptura comparável à popularização da internet ou à chegada dos smartphones (BROWN et al., 2020; OPENAI, 2023). Diferentemente das gerações anteriores de IA, que se concentravam em tarefas analíticas e preditivas, os modelos generativos são capazes de produzir conteúdo novo — textos, imagens, códigos, áudios — em resposta a instruções em linguagem natural.

A consolidação dos **Large Language Models** (LLMs), em especial após a publicação da arquitetura *Transformer* por Vaswani et al. (2017), permitiu que sistemas como GPT, Claude e Gemini executassem com proficiência tarefas linguísticas que, há poucos anos, exigiriam equipes especializadas. Aplicações típicas incluem assistentes virtuais corporativos, ferramentas de produtividade integradas a editores de texto, copilotos de programação e mecanismos de busca semântica. A IA Generativa deixou de ser tema acadêmico restrito e passou a integrar a estratégia digital de empresas como Microsoft, Google, Salesforce e SAP, que oferecem hoje copilotos nativos em seus produtos.

## 1.2 Conhecimento corporativo

Apesar do avanço tecnológico, o **conhecimento corporativo** permanece, em muitas organizações, fragmentado, redundante e de difícil acesso. Informações estratégicas estão distribuídas entre wikis internas, repositórios de documentos, e-mails arquivados, conversas em ferramentas de mensagens instantâneas e, frequentemente, na memória de colaboradores-chave. Pesquisas conduzidas pela McKinsey (2012) já apontavam que profissionais do conhecimento dedicam, em média, **1,8 horas por dia** apenas para localizar informações internas. Em uma jornada de oito horas, isso representa praticamente um quinto do tempo produtivo dissolvido em buscas.

Esse problema afeta particularmente os processos de **onboarding**, nos quais novos colaboradores precisam, em poucas semanas, compreender políticas de Recursos Humanos, normas de Tecnologia da Informação, fluxos financeiros e padrões de segurança. Também impacta as áreas de suporte interno (Help Desk, RH, TI), sobrecarregadas por dúvidas repetitivas que poderiam ser resolvidas por consulta a fontes documentais.

## 1.3 Problema

A pergunta que motiva este trabalho é direta: **como reduzir o atrito entre o colaborador e o conhecimento oficial da empresa, oferecendo respostas confiáveis, em linguagem natural, sem aumentar a carga sobre os times de suporte?** Os mecanismos tradicionais — portais com busca por palavras-chave, FAQs estáticos e chamados internos — apresentam limitações conhecidas: dependência do vocabulário exato utilizado pelo usuário, ausência de contexto conversacional, atualizações esporádicas e curva de adoção elevada.

## 1.4 Justificativa e motivação

A escolha do tema se justifica pela convergência de três fatores. Primeiro, a maturidade técnica dos LLMs, que permite construir assistentes confiáveis sem investimentos proibitivos. Segundo, a demanda corporativa real, evidenciada pela rápida adoção de soluções como Microsoft Copilot for Work, Glean e Notion AI. Terceiro, o caráter formativo da disciplina, que exige não apenas a construção de uma aplicação, mas também a demonstração explícita de **como a IA Generativa participa do próprio processo de desenvolvimento de software**.

Soma-se a isso a motivação pessoal do autor em compreender, na prática, os limites e as oportunidades do desenvolvimento assistido por IA: que tarefas podem ser delegadas com segurança, quais ainda exigem revisão humana criteriosa e como a engenharia de software se reorganiza em torno desse novo paradigma.

## 1.5 Objetivos do projeto

Em síntese, o **NexaDesk AI** busca demonstrar — em escala didática, mas com aparência de produto real — como combinar uma base de conhecimento estruturada, técnicas de **Retrieval-Augmented Generation** (RAG) e uma interface conversacional moderna pode resolver o problema da dispersão informacional dentro de uma organização. Paralelamente, propõe-se a documentar, com transparência metodológica, o papel desempenhado pelas ferramentas de IA Generativa em cada etapa da construção, configurando-se simultaneamente como artefato técnico e como objeto de estudo.

---

# 2. OBJETIVOS

## 2.1 Objetivo geral

Desenvolver um **copiloto corporativo baseado em IA Generativa**, denominado NexaDesk AI, capaz de responder em linguagem natural a perguntas sobre políticas, processos e procedimentos de uma empresa fictícia, demonstrando, simultaneamente, como ferramentas de IA Generativa participam ativamente do processo de engenharia de software.

## 2.2 Objetivos específicos

- Modelar uma **base de conhecimento corporativa simulada**, organizada em categorias e tipada em TypeScript, suficientemente realista para sustentar respostas plausíveis.
- Implementar um **agente de retrieval lexical** que selecione, para cada pergunta, os trechos mais relevantes da base de conhecimento.
- Projetar **prompts isolados e versionáveis** (system + user) compatíveis com APIs comerciais de LLM, de forma que a substituição do mecanismo de geração não impacte o restante da aplicação.
- Construir uma **interface SaaS profissional**, com tema escuro, sidebar, dashboard, chat, base de conhecimento navegável e favoritos.
- Garantir **persistência local** da sessão, do histórico de conversa e dos favoritos, sem dependência de backend externo no MVP.
- Documentar **prompt-a-prompt** o uso de IA Generativa durante o desenvolvimento, mensurando o ganho de produtividade.
- Aplicar boas práticas de **governança e segurança** alinhadas ao OWASP Top 10 for LLM Applications.
- Deixar a aplicação **preparada para integração futura** com LLMs comerciais (OpenAI, Anthropic) e com o Model Context Protocol (MCP).

---

# 3. FUNDAMENTAÇÃO TEÓRICA

## 3.1 Inteligência Artificial

A Inteligência Artificial (IA) é um campo da Ciência da Computação dedicado à construção de sistemas capazes de executar tarefas que, quando realizadas por humanos, exigem inteligência (RUSSELL; NORVIG, 2020). Suas raízes remontam à conferência de Dartmouth (1956), na qual John McCarthy cunhou o termo. Ao longo das décadas, a área alternou ciclos de otimismo e estagnação — os chamados *AI winters* — até que o aumento da capacidade computacional, a disponibilidade massiva de dados e os avanços em *deep learning* a partir de 2012 produzissem o atual ciclo de crescimento sustentado.

## 3.2 IA Generativa

A IA Generativa é uma subárea da IA cujos modelos produzem **conteúdo novo** a partir de padrões aprendidos em grandes volumes de dados (FOSTER, 2023). Diferentemente dos modelos discriminativos, que classificam ou predizem, os modelos generativos modelam a distribuição de probabilidade dos dados e amostram dela para gerar novas instâncias plausíveis. Esse paradigma engloba GANs, modelos de difusão (utilizados em geração de imagens) e os modelos autorregressivos baseados em *Transformer*, que dominam a geração de texto.

## 3.3 Large Language Models

Os **Large Language Models** são redes neurais profundas, tipicamente baseadas na arquitetura *Transformer* (VASWANI et al., 2017), treinadas em corpora massivos para prever o próximo token de uma sequência. Conforme demonstrado por Brown et al. (2020) no artigo seminal sobre o GPT-3, o aumento de parâmetros e dados produz **comportamentos emergentes**: tradução, sumarização, raciocínio simbólico e geração de código surgem sem treinamento específico. Modelos contemporâneos como GPT-4 (OpenAI), Claude (Anthropic) e Gemini (Google) operam com janelas de contexto cada vez mais amplas, suporte multimodal e mecanismos de alinhamento por RLHF (*Reinforcement Learning from Human Feedback*).

## 3.4 Engenharia de Prompt

A **engenharia de prompt** consiste em projetar instruções textuais que orientem o LLM a produzir saídas alinhadas ao objetivo desejado (WHITE et al., 2023). Trata-se de uma disciplina emergente que combina conhecimento técnico, linguística aplicada e desenho de experiência. Padrões consolidados incluem:

- **Zero-shot prompting**: instrução direta sem exemplos.
- **Few-shot prompting**: inclusão de exemplos no próprio prompt.
- **Chain-of-thought**: solicitação explícita de raciocínio passo a passo (WEI et al., 2022).
- **Role prompting**: atribuição de um papel ao modelo ("Você é um copiloto corporativo…").
- **Separação system/user**: isolamento das regras imutáveis no *system prompt*, mitigando ataques de *prompt injection*.

No NexaDesk AI, o `SYSTEM_PROMPT` foi cuidadosamente projetado para impor tom corporativo, idioma, formato Markdown e, sobretudo, a frase padrão de *fallback* — exemplo prático dessas técnicas.

## 3.5 Retrieval-Augmented Generation (RAG)

O paradigma **RAG**, formalizado por Lewis et al. (2020), combina recuperação de informação e geração textual. Em vez de confiar exclusivamente no conhecimento paramétrico do LLM — sujeito a desatualização e alucinação — o sistema recupera documentos relevantes de uma base externa e os fornece como contexto na chamada ao modelo. Esse desenho oferece três vantagens decisivas em ambientes corporativos: (i) **atualidade**, pois a base pode ser atualizada sem retreinamento; (ii) **rastreabilidade**, já que cada resposta pode citar suas fontes; e (iii) **redução de alucinações**, ao restringir o universo do qual o modelo "fala".

O fluxo canônico do RAG envolve: tokenização da consulta, recuperação top-K dos documentos mais relevantes (por similaridade lexical ou semântica via *embeddings*), montagem do prompt e geração da resposta. O NexaDesk AI adota uma variante lexical desse fluxo, suficiente para uma base controlada e didática.

## 3.6 Agentes de IA

Um **agente de IA** é um sistema autônomo que percebe seu ambiente, raciocina sobre objetivos e executa ações por meio de ferramentas (RUSSELL; NORVIG, 2020). Frameworks modernos como LangChain, LlamaIndex e o paradigma ReAct (YAO et al., 2022) materializam essa visão combinando LLMs com chamadas a APIs, bancos de dados e funções. No contexto deste trabalho, o módulo `agent.ts` encapsula o ciclo de percepção (pergunta), raciocínio (retrieval + prompting) e ação (geração de resposta), estando estruturado para evolução futura com chamadas a ferramentas externas.

## 3.7 Model Context Protocol (MCP)

O **Model Context Protocol**, proposto pela Anthropic em 2024, é um padrão aberto para conectar LLMs a fontes de dados e ferramentas externas (ANTHROPIC, 2024). Funciona como uma camada de abstração análoga ao que o LSP representa para editores de código: servidores MCP expõem recursos (documentos, prompts, ferramentas) que podem ser consumidos por qualquer cliente compatível. A arquitetura do NexaDesk AI foi pensada para futura adoção do MCP — bastaria substituir a função `retrieve()` por uma chamada a um servidor MCP conectado a Confluence, Notion ou SharePoint.

## 3.8 Desenvolvimento Assistido por IA

O **desenvolvimento assistido por IA** redefine o ciclo tradicional de engenharia de software. Estudos da GitHub (2022) indicam que desenvolvedores que utilizam Copilot completam tarefas até **55% mais rápido**, com perceptível aumento de satisfação e foco em atividades de maior valor agregado. A produtividade ganha, entretanto, depende fortemente da maturidade do desenvolvedor em revisar, refatorar e testar o código sugerido — o paradigma exige uma postura crítica, não passiva.

## 3.9 GitHub Copilot, Claude e ChatGPT

- **GitHub Copilot** opera como autocomplete inteligente dentro do editor, sugerindo trechos de código contextuais com base em modelos da OpenAI.
- **ChatGPT** (OpenAI) e **Claude** (Anthropic) são interfaces conversacionais que permitem desde *brainstorming* arquitetural até geração de código complexo, redação de documentação e revisão crítica.
- Ferramentas como **Lovable** integram esses modelos a um ambiente de desenvolvimento web, automatizando *scaffolding*, design system, rotas e *deploys*.

## 3.10 Segurança, governança e ética

A adoção corporativa de LLMs introduz riscos próprios: vazamento de dados sensíveis em prompts, dependência de provedores externos, vieses incorporados pelos dados de treinamento e dificuldade de auditoria das saídas. Frameworks de governança, como o **NIST AI Risk Management Framework** (NIST, 2023) e diretrizes do **AI Act** europeu, propõem práticas de transparência, rastreabilidade, supervisão humana e avaliação contínua de risco.

Eticamente, destaca-se a responsabilidade pelo conteúdo gerado, a necessidade de consentimento informado do usuário sobre o uso de IA e a obrigação de evitar reproduzir vieses discriminatórios.

## 3.11 OWASP Top 10 para LLM

A **OWASP** publicou, em 2023, a primeira lista das principais vulnerabilidades específicas de aplicações baseadas em LLM (OWASP, 2023). Entre as categorias mais relevantes para este projeto destacam-se:

- **LLM01 — Prompt Injection**: mitigada pelo isolamento do *system prompt* e pela ausência de interpretação de HTML do modelo.
- **LLM02 — Insecure Output Handling**: tratada por meio do renderizador Markdown próprio, que não executa código.
- **LLM06 — Sensitive Information Disclosure**: endereçada pela inexistência de dados pessoais reais na base.
- **LLM08 — Excessive Agency**: limitada pela ausência de ferramentas com efeitos colaterais; o agente apenas lê e responde.

---

# 4. DESENVOLVIMENTO DO PROJETO

## 4.1 Planejamento

O projeto foi planejado em quatro grandes blocos: **(i)** definição do escopo e do design system; **(ii)** construção da base de conhecimento simulada; **(iii)** implementação do agente RAG e da interface; **(iv)** documentação acadêmica. A estratégia adotada privilegiou um *MVP funcional ponta a ponta* desde a primeira iteração, em detrimento de funcionalidades isoladas sem integração.

## 4.2 Levantamento de requisitos

Foram identificados **requisitos funcionais** — login fictício, chat conversacional, navegação por categorias, busca textual, favoritos, exportação de conversa — e **requisitos não funcionais** — tema escuro, responsividade, persistência local, tempo de resposta inferior a dois segundos, código tipado em TypeScript, ausência de dados pessoais reais.

## 4.3 Arquitetura geral

A arquitetura adotada segue uma separação clássica em três camadas, com fronteiras claras entre dados, lógica de agente e apresentação:

```
┌────────────────────┐      ┌─────────────────────┐      ┌────────────────────┐
│  UI (React + TS)   │ ───▶ │  Agente (TS puro)   │ ───▶ │  Resposta (MD)     │
│  Chat / Sidebar    │      │  retrieve → prompt  │      │  + fontes citadas  │
└────────────────────┘      └─────────────────────┘      └────────────────────┘
                                      ▲
                            ┌─────────────────────┐
                            │ knowledgeBase.ts    │
                            │ 77 Q&As / 12 cats   │
                            └─────────────────────┘
```

## 4.4 Frontend

O frontend foi construído com **React 19** e **TypeScript**, utilizando **Vite 7** como bundler e **TanStack Start** para roteamento baseado em arquivos. A estilização é feita com **TailwindCSS v4** e componentes acessíveis do **shadcn/ui**. O design system, definido em `src/styles.css`, emprega tokens semânticos baseados em `oklch`, garantindo consistência cromática e suporte facilitado a múltiplos temas.

## 4.5 Backend

Para o MVP acadêmico, a aplicação opera **sem backend dedicado**: toda a lógica do agente roda no cliente, e a persistência (sessão, mensagens, favoritos) usa `localStorage`. A arquitetura, entretanto, foi preparada para integração futura com **Lovable Cloud** (Supabase gerenciado) e com **Edge Functions** para chamadas autenticadas a provedores de LLM.

## 4.6 Banco de dados

A "base de conhecimento" do MVP é um arquivo TypeScript tipado (`src/data/knowledgeBase.ts`) contendo 77 entradas distribuídas em 12 categorias. Cada entrada implementa a interface:

```ts
interface KbEntry {
  id: string;
  category: string;
  question: string;
  answer: string;
  tags: string[];
}
```

Em produção, essa estrutura migraria para uma tabela PostgreSQL com índices de busca textual ou vetorial (pgvector).

## 4.7 Fluxo da aplicação

1. Usuário acessa `/`, autentica-se via formulário fictício.
2. Sessão é persistida em `localStorage`; o roteador redireciona a `/app`.
3. O *layout* autenticado renderiza a `AppSidebar` e o `<Outlet />` correspondente.
4. Em `/app`, a `ChatView` recebe a pergunta e dispara `askAgent()`.
5. A resposta é renderizada em Markdown, com badges das fontes recuperadas.

## 4.8 Fluxo da IA

```
Pergunta → tokenize() → scoreEntry() → top-K → buildContext()
        → SYSTEM_PROMPT + USER_PROMPT → runMockLLM() → resposta + fontes
```

A função `runMockLLM` foi projetada como **ponto único de substituição**: trocar por `fetch` à API da OpenAI ou Anthropic requer modificar apenas essa função, mantendo intactos *retrieval* e *prompting*.

## 4.9 Interface

A interface adota linguagem visual inspirada em produtos como Notion, Linear e ChatGPT. O tema escuro de alto contraste, gradientes suaves e tipografia generosa transmitem credibilidade. As principais telas — login, chat, dashboard, base e favoritos — estão documentadas em capturas neste relatório.

## 4.10 Decisões técnicas

| Decisão | Alternativa descartada | Justificativa |
| --- | --- | --- |
| Busca lexical | Embeddings + vector store | Custo zero, 100% client-side, suficiente para 77 docs |
| Mock LLM | Chamada direta à OpenAI | Reprodutibilidade acadêmica e ausência de chave |
| LocalStorage | Banco gerenciado | Escopo de MVP didático |
| Markdown renderer próprio | react-markdown | Eliminar dependências e controlar a sanitização |

## 4.11 Estrutura de pastas

```
src/
├── components/        # AppSidebar, ChatView, UI primitives
├── data/              # knowledgeBase.ts
├── lib/               # agent.ts, prompts.ts, markdown.tsx, storage.ts
├── routes/            # __root.tsx, index.tsx, app.tsx, app.dashboard.tsx, …
└── styles.css         # Design tokens (oklch)
```

## 4.12 APIs utilizadas

No MVP, nenhuma API externa é chamada em tempo de execução. A estrutura, no entanto, está preparada para integração com **OpenAI Chat Completions API**, **Anthropic Messages API** e **MCP servers**.

## 4.13 Organização do código

O código segue convenções estritas de TypeScript (`strict: true`), separação de responsabilidades por arquivo, ausência de side-effects em módulos de dados e nomes auto-descritivos. O ESLint e o Prettier garantem padronização. Cada arquivo de domínio (`agent.ts`, `prompts.ts`) inicia com um cabeçalho explicativo, prática herdada das diretrizes de código limpo de Robert C. Martin.

---

# 5. FERRAMENTAS UTILIZADAS

## 5.1 Claude (Anthropic)

Empregado como modelo principal por trás do ambiente Lovable, contribuiu na **arquitetura, na escrita de componentes complexos e na elaboração desta documentação**. Sua janela de contexto ampla e seu estilo discursivo foram especialmente úteis para gerar textos longos com coesão.

## 5.2 ChatGPT (OpenAI)

Utilizado para **brainstorming inicial**, geração das 77 perguntas e respostas plausíveis da base de conhecimento e validação cruzada de trechos de código gerados por outras ferramentas.

## 5.3 GitHub

Plataforma de versionamento utilizada para hospedar o código-fonte, organizar o histórico de commits e suportar a futura colaboração em código aberto.

## 5.4 GitHub Copilot

Funcionou como **autocomplete contextual** no editor, acelerando a escrita de funções utilitárias (`tokenize`, `estimateTokens`) e tipagens repetitivas.

## 5.5 React

Biblioteca declarativa para construção de interfaces, escolhida pela vasta documentação, pelo ecossistema maduro e por sua aderência a padrões modernos como Hooks e Suspense.

## 5.6 TypeScript

Adicionou tipagem estática ao JavaScript, reduzindo bugs em tempo de desenvolvimento e melhorando a experiência com autocomplete e refatoração.

## 5.7 Tailwind CSS

Framework CSS *utility-first* que viabilizou a construção de uma interface coesa, responsiva e tematizada, sem produzir folhas de estilo gigantescas. A versão 4 introduz tokens nativos via `@theme`, aproveitados no design system.

## 5.8 Supabase

Plataforma BaaS sobre PostgreSQL, **preparada para integração futura** (autenticação, RLS, pgvector). No MVP atual, está disponível, porém não habilitada.

## 5.9 Node.js

Runtime JavaScript que sustenta o tooling (Vite, Bun, ESLint). No futuro, suportará as Edge Functions responsáveis pelas chamadas autenticadas ao LLM.

## 5.10 OpenAI API

API REST para acesso aos modelos GPT. Embora não consumida no MVP, o `buildUserPrompt` já segue o esquema esperado por `chat.completions.create`, viabilizando a integração com poucas linhas de código.

---

# 6. COMO A IA AUXILIOU O DESENVOLVIMENTO

## 6.1 Geração de código

A IA gerou o esqueleto inicial das rotas, componentes e utilitários. Estima-se que **mais de 70% do código** tenha sido produzido por sugestões de Claude e Copilot, sempre revisadas pelo autor antes de serem incorporadas.

## 6.2 Decisões de arquitetura

Discussões iterativas com Claude permitiram comparar abordagens (busca lexical vs. semântica, RAG vs. *fine-tuning*, *server actions* vs. SPA), acelerando a tomada de decisão com base em prós e contras articulados.

## 6.3 Engenharia de prompts

A IA atuou como crítica do próprio prompt: foram realizadas múltiplas iterações até que o `SYSTEM_PROMPT` impusesse fallback consistente, tom corporativo e citação de fontes.

## 6.4 Documentação

Este relatório, o README e o `DOCUMENTATION.md` foram co-escritos com IA, partindo de tópicos curtos fornecidos pelo autor e expandidos até atingir o nível de detalhamento exigido pela ABNT.

## 6.5 Correção de bugs

Erros de tipagem, conflitos de rota e problemas de renderização foram diagnosticados em diálogo com a IA, frequentemente em menos tempo do que levaria pesquisar em Stack Overflow.

## 6.6 Testes

A estrutura de testes ainda é incipiente no MVP, mas a IA gerou esqueletos de casos de teste para `tokenize` e `scoreEntry`, prontos para serem integrados com Vitest.

## 6.7 Refatoração

Trechos complexos — em especial o renderizador Markdown — foram refatorados em diálogo com a IA para reduzir aninhamento e melhorar legibilidade.

## 6.8 Produtividade

Estima-se que o MVP tenha sido entregue em aproximadamente **2 horas** de iteração assistida, contra um esforço estimado de **16 a 24 horas** em desenvolvimento tradicional.

## 6.9 Desenvolvimento tradicional vs. assistido por IA

| Dimensão | Tradicional | Assistido por IA |
| --- | --- | --- |
| Scaffolding | Manual, dependente de templates | Instantâneo |
| Documentação | Frequentemente postergada | Co-escrita em paralelo |
| Pesquisa de APIs | Stack Overflow, docs | Diálogo direto com o modelo |
| Refatoração | Manual | Sugerida e justificada |
| Curva de aprendizado | Alta para tecnologias novas | Reduzida pelo *pair programming* virtual |

---

# 7. FUNCIONALIDADES DO SISTEMA

A seguir são descritas, em detalhe, as principais funcionalidades implementadas. As capturas de tela correspondentes estão disponíveis em `/screens` (anexas a este pacote).

### 7.1 Login corporativo (fictício)
Tela de boas-vindas com hero institucional e formulário de autenticação. Aceita qualquer credencial e persiste a sessão em `localStorage`. *Captura: `01-login.png`.*

### 7.2 Chat conversacional
Interface principal do produto. Exibe estado vazio com sugestões iniciais, composer com atalho Enter/Shift+Enter e renderização de respostas em Markdown com fontes citadas. *Capturas: `02-chat-empty.png`, `03-chat-answer.png`.*

### 7.3 Dashboard
Visão de boas-vindas com métricas (mensagens, favoritos, documentos, categorias) e atalhos para conversa e categorias. *Captura: `04-dashboard.png`.*

### 7.4 Base de Conhecimento
Lista navegável dos 77 documentos, com busca por termo e filtro por categoria. Cada item permite ser favoritado e enviado diretamente ao chat. *Captura: `05-knowledge.png`.*

### 7.5 Favoritos
Lista de itens marcados pelo usuário, sincronizados em tempo real com a base. *Captura: `06-favorites.png`.*

### 7.6 Exportação e cópia
Botões disponíveis na tela de chat permitem **copiar uma resposta** individual ou **exportar toda a conversa** em formato Markdown.

### 7.7 Limpar conversa e nova conversa
Recursos que reiniciam o histórico atual, com confirmação visual.

### 7.8 Persistência local
Sessão, mensagens da conversa atual e favoritos são preservados entre recargas da página, sem necessidade de backend.

---

# 8. BENEFÍCIOS OBTIDOS

- **Redução do tempo de busca** por informação interna, dado que o colaborador formula a pergunta em linguagem natural.
- **Padronização das respostas**, pois todas derivam da base oficial e citam sua categoria de origem.
- **Alívio dos times de RH e TI**, ao endereçar dúvidas repetitivas de forma automatizada.
- **Aceleração do onboarding**, oferecendo a novos colaboradores um ponto único de consulta.
- **Demonstração tangível de IA Generativa**, evidenciando a aplicabilidade da disciplina em contextos corporativos reais.
- **Documentação rica do processo**, gerada paralelamente ao desenvolvimento, valorizando o portfólio acadêmico do autor.
- **Base sólida para evolução**, com pontos de extensão claros (LLM real, embeddings, MCP, autenticação corporativa).

---

# 9. LIMITAÇÕES ENCONTRADAS

- **Busca puramente lexical**: sinônimos e variações morfológicas podem reduzir o *recall*. A migração para embeddings é prevista.
- **Ausência de LLM real conectado**: o `runMockLLM` produz respostas determinísticas a partir do trecho mais relevante, sem variação linguística.
- **Persistência local**: o usuário perde sua sessão ao trocar de dispositivo ou limpar o navegador.
- **Base estática e fictícia**: não há mecanismo de atualização incremental nem ingestão de fontes externas.
- **Login fictício**: ausência de autenticação real e de controle de acesso por papel.
- **Ausência de telemetria**: não há coleta de métricas de uso, qualidade percebida ou custo por interação.
- **Cobertura de testes incipiente**: testes automatizados ainda precisam ser ampliados.

---

# 10. ASPECTOS ÉTICOS E GOVERNANÇA DA IA

A construção de assistentes corporativos baseados em LLMs introduz dilemas éticos que não podem ser ignorados sob risco de comprometer a confiança do usuário. O NexaDesk AI foi projetado em consonância com princípios estabelecidos pelo NIST AI RMF (NIST, 2023) e pelas diretrizes preliminares do AI Act europeu, observando:

- **Transparência**: toda resposta indica a categoria de origem, permitindo verificação humana.
- **Anti-alucinação**: o *system prompt* obriga a frase padrão de *fallback* quando o contexto recuperado é insuficiente.
- **Privacidade**: nenhum dado pessoal real é utilizado; a base é integralmente fictícia.
- **Auditabilidade**: o objeto `trace` retornado pelo agente expõe os prompts efetivamente enviados e a estimativa de tokens.
- **Supervisão humana**: a aplicação não executa ações com efeitos colaterais; cabe ao colaborador validar e agir sobre a informação.
- **Aderência ao OWASP LLM Top 10**: `SYSTEM_PROMPT` isolado (LLM01), Markdown sanitizado (LLM02), ausência de PII (LLM06) e ausência de *agency* sensível (LLM08).
- **Acessibilidade**: contraste cromático elevado e componentes shadcn com semântica ARIA correta.

Adicionalmente, recomenda-se, em evolução para produção, a adoção de **logs auditáveis de prompt e resposta**, **rate limiting** por usuário, **classificação de sensibilidade** dos documentos consultados e **mecanismos de feedback** que permitam revisar e corrigir respostas inadequadas.

---

# 11. TRABALHOS FUTUROS

- Conectar provedores reais de LLM (OpenAI, Anthropic) por meio de Edge Functions autenticadas.
- Substituir a busca lexical por **embeddings + pgvector**, ampliando o *recall* semântico.
- Implementar **múltiplas conversas persistentes** com histórico em banco gerenciado.
- Integrar **Model Context Protocol** para consumo direto de fontes corporativas (Confluence, Notion, SharePoint).
- Adicionar **autenticação corporativa** via Google Workspace e Microsoft Entra ID.
- Introduzir **avaliação automatizada de respostas** com a técnica *LLM-as-a-judge*.
- Disponibilizar um **painel administrativo** para curadoria da base e métricas de uso.
- Habilitar **modo voz** com Speech-to-Text e Text-to-Speech.
- Publicar versões móveis (PWA) e desktop (Tauri).

---

# 12. CONCLUSÃO

O **NexaDesk AI** demonstrou, dentro do recorte didático proposto, que é possível construir, em poucas horas e com qualidade próxima à de um produto SaaS comercial, um copiloto corporativo plausível baseado em IA Generativa. Mais relevante do que o artefato em si, o trabalho evidenciou **como a IA participa ativamente do próprio desenvolvimento de software**, atuando como par de programação, redatora técnica, revisora arquitetural e geradora de conteúdo.

Os objetivos específicos foram integralmente cumpridos: a base de conhecimento foi modelada, o agente de retrieval implementado, os prompts isolados, a interface entregue com identidade visual coesa, a persistência local validada, a documentação produzida prompt-a-prompt e as boas práticas de segurança e governança aplicadas. As limitações identificadas — busca lexical, ausência de LLM real conectado, persistência local — são, simultaneamente, oportunidades naturais de evolução, todas mapeadas no capítulo de trabalhos futuros.

Para a disciplina de IA Generativa Aplicada ao Desenvolvimento, o projeto cumpre a dupla função pedagógica de **estudar a IA enquanto se constrói com IA**. Conclui-se que o desenvolvimento assistido por modelos generativos não substitui o engenheiro de software, mas exige dele um novo conjunto de habilidades: pensamento crítico, engenharia de prompt, governança ética e capacidade de orquestrar ferramentas heterogêneas. Esse perfil profissional emergente é, possivelmente, a contribuição mais duradoura desta experiência.

---

# 13. REFERÊNCIAS BIBLIOGRÁFICAS

ANTHROPIC. **Introducing the Model Context Protocol**. São Francisco: Anthropic, 2024. Disponível em: https://www.anthropic.com/news/model-context-protocol. Acesso em: 15 jun. 2026.

ANTHROPIC. **Claude Documentation**. São Francisco: Anthropic, 2025. Disponível em: https://docs.anthropic.com. Acesso em: 15 jun. 2026.

BROWN, T. et al. **Language Models are Few-Shot Learners**. In: ADVANCES IN NEURAL INFORMATION PROCESSING SYSTEMS, 33, 2020. Proceedings… NeurIPS, 2020.

FOSTER, D. **Generative Deep Learning**. 2. ed. Sebastopol: O'Reilly Media, 2023.

GITHUB. **Research: quantifying GitHub Copilot's impact on developer productivity and happiness**. GitHub Blog, 2022. Disponível em: https://github.blog/2022-09-07-research-quantifying-github-copilots-impact-on-developer-productivity-and-happiness/. Acesso em: 15 jun. 2026.

LEWIS, P. et al. **Retrieval-Augmented Generation for Knowledge-Intensive NLP Tasks**. In: ADVANCES IN NEURAL INFORMATION PROCESSING SYSTEMS, 33, 2020. Proceedings… NeurIPS, 2020.

MCKINSEY GLOBAL INSTITUTE. **The social economy: Unlocking value and productivity through social technologies**. McKinsey & Company, 2012.

NIST. **Artificial Intelligence Risk Management Framework (AI RMF 1.0)**. Gaithersburg: National Institute of Standards and Technology, 2023.

OPENAI. **GPT-4 Technical Report**. San Francisco: OpenAI, 2023.

OPENAI. **OpenAI API Reference**. San Francisco: OpenAI, 2025. Disponível em: https://platform.openai.com/docs. Acesso em: 15 jun. 2026.

OWASP. **OWASP Top 10 for Large Language Model Applications**. The OWASP Foundation, 2023. Disponível em: https://owasp.org/www-project-top-10-for-large-language-model-applications/. Acesso em: 15 jun. 2026.

REACT TEAM. **React Documentation**. Meta Open Source, 2025. Disponível em: https://react.dev. Acesso em: 15 jun. 2026.

RUSSELL, S.; NORVIG, P. **Artificial Intelligence: A Modern Approach**. 4. ed. Hoboken: Pearson, 2020.

SUPABASE. **Supabase Documentation**. Supabase Inc., 2025. Disponível em: https://supabase.com/docs. Acesso em: 15 jun. 2026.

TAILWIND LABS. **Tailwind CSS Documentation**. Tailwind Labs, 2025. Disponível em: https://tailwindcss.com/docs. Acesso em: 15 jun. 2026.

TANSTACK. **TanStack Start Documentation**. TanStack, 2025. Disponível em: https://tanstack.com/start. Acesso em: 15 jun. 2026.

TYPESCRIPT TEAM. **TypeScript Handbook**. Microsoft, 2025. Disponível em: https://www.typescriptlang.org/docs/. Acesso em: 15 jun. 2026.

VASWANI, A. et al. **Attention Is All You Need**. In: ADVANCES IN NEURAL INFORMATION PROCESSING SYSTEMS, 30, 2017. Proceedings… NeurIPS, 2017.

WEI, J. et al. **Chain-of-Thought Prompting Elicits Reasoning in Large Language Models**. In: ADVANCES IN NEURAL INFORMATION PROCESSING SYSTEMS, 35, 2022. Proceedings… NeurIPS, 2022.

WHITE, J. et al. **A Prompt Pattern Catalog to Enhance Prompt Engineering with ChatGPT**. arXiv preprint arXiv:2302.11382, 2023.

YAO, S. et al. **ReAct: Synergizing Reasoning and Acting in Language Models**. arXiv preprint arXiv:2210.03629, 2022.

---

*Documento elaborado com auxílio de IA Generativa (Claude, ChatGPT, GitHub Copilot) e revisado pelo autor.*
