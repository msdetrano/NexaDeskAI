<div align="center">

# 🤖 NexaDesk AI

### *Seu copiloto inteligente para o conhecimento da empresa*

[![Made with React](https://img.shields.io/badge/React-19-61DAFB?logo=react&logoColor=white)](https://react.dev)
[![TypeScript](https://img.shields.io/badge/TypeScript-5-3178C6?logo=typescript&logoColor=white)](https://www.typescriptlang.org/)
[![Vite](https://img.shields.io/badge/Vite-7-646CFF?logo=vite&logoColor=white)](https://vitejs.dev/)
[![TailwindCSS](https://img.shields.io/badge/Tailwind-v4-38B2AC?logo=tailwind-css&logoColor=white)](https://tailwindcss.com)
[![TanStack Start](https://img.shields.io/badge/TanStack-Start-FF4154?logo=react-router&logoColor=white)](https://tanstack.com/start)
[![License: MIT](https://img.shields.io/badge/License-MIT-yellow.svg)](#-licença)
[![AI Powered](https://img.shields.io/badge/AI-Generative-7c3aed)](#-fluxo-da-ia)
[![Status](https://img.shields.io/badge/status-MVP%20Acad%C3%AAmico-success)]()

![banner](./screens/banner-placeholder.png)

</div>

 ** Acesso a Demonstração -> ** https://nexa-copilot-ai.lovable.app/auth
---

## 📖 Descrição

**NexaDesk AI** é um copiloto corporativo construído com **IA Generativa**, projetado para responder, em linguagem natural, dúvidas recorrentes de colaboradores sobre políticas, processos e procedimentos internos de uma empresa fictícia (Nexa Corp).

O projeto foi desenvolvido para a disciplina **IA Generativa Aplicada ao Desenvolvimento** e tem dois propósitos:

1. **Entregar um produto SaaS plausível**, com UX moderno (Notion / Linear / ChatGPT) e tema escuro profissional.
2. **Demonstrar transparentemente** como ferramentas de IA Generativa participaram de cada etapa da construção — decisões, prompts e ganhos documentados.

## 🎯 Objetivo

Reduzir o atrito entre o colaborador e o conhecimento oficial da empresa, oferecendo respostas confiáveis em segundos, sem aumentar a carga sobre os times de RH e TI.

<img width="1280" height="720" alt="04-dashboard" src="https://github.com/user-attachments/assets/c3091149-a290-4ec2-a379-36ca83e2d797" />

<img width="1280" height="720" alt="05-knowledge" src="https://github.com/user-attachments/assets/0ecc46a9-6d45-49ee-be72-bd0d2b132ee0" />


## ✨ Funcionalidades

- 🔐 **Login corporativo** fictício com persistência em `localStorage`
- 💬 **Chat conversacional** com indicador "pensando…", sugestões iniciais e scroll automático
- 📚 **Base de conhecimento** com 77 documentos em 12 categorias, busca e filtros
- 📊 **Dashboard** com métricas e atalhos
- ⭐ **Favoritos** sincronizados
- 📥 **Exportar conversa** em Markdown e **copiar respostas**
- 🧹 **Limpar / Nova conversa**
- 🎨 **Tema escuro** de alto contraste com tokens `oklch`
- 📱 **Responsivo** em desktop, tablet e mobile
- 🛡 Aderente ao **OWASP Top 10 for LLM Applications**

## 🛠️ Tecnologias

| Camada | Stack |
| --- | --- |
| **Frontend** | React 19 · TypeScript · Vite 7 · TanStack Router & Start |
| **UI** | TailwindCSS v4 · shadcn/ui · lucide-react · sonner |
| **Estado** | `localStorage` (sessão, conversa, favoritos) |
| **IA** | Estrutura RAG pronta para **OpenAI** ou **Anthropic Claude** |
| **Backend** | Lovable Cloud (opcional, não habilitado no MVP) |
| **Tooling** | Bun · ESLint · Prettier |

## 🧠 Arquitetura

```text
┌────────────────────┐      ┌─────────────────────┐      ┌────────────────────┐
│  UI (React + TS)   │ ───▶ │  Agente (TS puro)   │ ───▶ │  Resposta (MD)     │
│  - Chat            │      │  1. retrieve()       │      │  + fontes citadas  │
│  - Sidebar         │      │  2. buildContext()   │      └────────────────────┘
│  - Dashboard       │      │  3. buildPrompt()    │
└────────────────────┘      │  4. runMockLLM()     │
                            │  (substituível por   │
                            │   OpenAI/Claude API) │
                            └─────────────────────┘
                                      ▲
                            ┌─────────────────────┐
                            │ knowledgeBase.ts    │
                            │ 77 Q&As / 12 cats   │
                            └─────────────────────┘
```

## 📁 Estrutura de pastas

```
src/
├── components/
│   ├── AppSidebar.tsx       # Navegação principal
│   ├── ChatView.tsx         # Composer + mensagens
│   └── ui/                  # Primitives shadcn
├── data/
│   └── knowledgeBase.ts     # 77 Q&As em 12 categorias
├── lib/
│   ├── agent.ts             # Retrieval + agente
│   ├── prompts.ts           # SYSTEM_PROMPT + buildUserPrompt
│   ├── markdown.tsx         # Renderizador Markdown leve
│   └── storage.ts           # Sessão, mensagens, favoritos
├── routes/
│   ├── __root.tsx           # Shell + meta tags
│   ├── index.tsx            # Login
│   ├── app.tsx              # Layout autenticado
│   ├── app.index.tsx        # /app  → Chat
│   ├── app.dashboard.tsx
│   ├── app.knowledge.tsx
│   └── app.favorites.tsx
└── styles.css               # Design tokens oklch
```

## 🚀 Como instalar

```bash
git clone https://github.com/<seu-usuario>/nexadesk-ai.git
cd nexadesk-ai
bun install
```

> Também funciona com `npm install` ou `pnpm install`.

## ▶️ Como executar

```bash
bun run dev
```

Acesse `http://localhost:3000`. **Qualquer e-mail/senha funciona** no login (fictício).

## 🔐 Variáveis de ambiente (`.env.example`)

```bash
# === Provedor de LLM (opcional, para conectar IA real) ===
OPENAI_API_KEY=sk-...
ANTHROPIC_API_KEY=sk-ant-...

# === Lovable Cloud / Supabase (opcional) ===
VITE_SUPABASE_URL=
VITE_SUPABASE_PUBLISHABLE_KEY=
SUPABASE_SECRET_KEY=
```

## 📜 Scripts

| Script | Ação |
| --- | --- |
| `bun run dev` | Inicia o servidor de desenvolvimento |
| `bun run build` | Gera o build de produção |
| `bun run preview` | Pré-visualiza o build |
| `bun run lint` | Executa o ESLint |

## 🔄 Fluxo da IA

```
Pergunta → tokenize() → scoreEntry() → top-K trechos
       → buildContext() → SYSTEM_PROMPT + USER_PROMPT
       → runMockLLM()  ←  (trocar por OpenAI/Claude)
       → resposta Markdown + fontes citadas
```

Para **conectar um LLM real**, substitua `runMockLLM()` em `src/lib/agent.ts` por uma chamada `fetch` ao provedor desejado. Toda a estrutura de prompts já está pronta.

## 🤖 Ferramentas de IA utilizadas

| Ferramenta | Uso no projeto |
| --- | --- |
| **Lovable (Claude Sonnet)** | Scaffolding, design system, componentes complexos |
| **ChatGPT (GPT-5)** | Brainstorm das categorias e Q&As da base |
| **GitHub Copilot** | Autocomplete de utilitários TypeScript |
| **Claude** | Engenharia de prompts e redação acadêmica |

## 🧑‍💻 Participação da IA no desenvolvimento

- **Geração de código**: ~70% do código inicial gerado por IA, revisado pelo autor.
- **Arquitetura**: comparação de alternativas (RAG vs. fine-tuning, lexical vs. semântico) em diálogo com Claude.
- **Engenharia de prompts**: iterações até estabilizar `SYSTEM_PROMPT` com tom corporativo, fallback e citação de fontes.
- **Documentação**: README e relatório acadêmico co-escritos com IA, revisão final humana.
- **Refatoração**: trechos críticos (renderer Markdown, scoring) reescritos com sugestões da IA.
- **Produtividade**: MVP entregue em ~2h, contra estimativa de 16–24h em desenvolvimento tradicional.

## 📸 Capturas de tela

| Login | Chat |
| --- | --- |
| ![login](./screens/01-login.png) | ![chat](./screens/03-chat-answer.png) |

| Dashboard | Base de Conhecimento |
| --- | --- |
| ![dashboard](./screens/04-dashboard.png) | ![knowledge](./screens/05-knowledge.png) |

| Favoritos | Estado inicial do Chat |
| --- | --- |
| ![favorites](./screens/06-favorites.png) | ![chat-empty](./screens/02-chat-empty.png) |

## 🗺️ Roadmap

- [ ] Conectar OpenAI / Anthropic via Edge Function
- [ ] Substituir busca lexical por **embeddings + pgvector**
- [ ] Múltiplas conversas persistentes
- [ ] Integração real com **Model Context Protocol** (Notion, Confluence)
- [ ] Login com **Google Workspace / Microsoft Entra ID**
- [ ] Painel administrativo (curadoria + métricas)
- [ ] **LLM-as-a-judge** para avaliação automática
- [ ] PWA + apps desktop (Tauri)

## 📄 Licença

Distribuído sob a licença **MIT**. Veja o arquivo [`LICENSE`](./LICENSE) para detalhes.

```
MIT License

Copyright (c) 2026 Nexa Corp

Permission is hereby granted, free of charge, to any person obtaining a copy
of this software and associated documentation files (the "Software"), to deal
in the Software without restriction, including without limitation the rights
to use, copy, modify, merge, publish, distribute, sublicense, and/or sell
copies of the Software, and to permit persons to whom the Software is
furnished to do so, subject to the following conditions: …
```

## 👤 Autor

**Marcos Detrano**
🎓 Disciplina: *IA Generativa Aplicada ao Desenvolvimento*


## 🙏 Agradecimentos

- À **Anthropic, OpenAI, GitHub e Lovable** pelas ferramentas que tornaram este projeto possível.
- À comunidade **React / TanStack / Tailwind**, pela documentação de excelência.
- Ao(à) Prof.(a) **Patricia Miscolcz** pela condução da disciplina.


---

<div align="center">

*Feito com ❤️ e 🤖 — Nexa Corp, 2026*

</div>
