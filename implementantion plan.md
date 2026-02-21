# Plano de Implementação: WhatsSell AI

Este documento detalha as etapas técnicas, arquitetura e marcos para o desenvolvimento do WhatsSell AI, conforme definido no PRD e Design System.

---

## 🏗️ 1. Arquitetura do Sistema

Utilizaremos um **Monorepo** para gerenciar todas as partes da aplicação com eficiência e compartilhamento de tipos/código.

| Camada              | Tecnologia                                             | Objetivo                                         |
| :------------------ | :----------------------------------------------------- | :----------------------------------------------- |
| **Monorepo**        | [Turborepo](https://turbo.build/)                      | Orquestração de builds e cache.                  |
| **Marketing UI**    | [Astro](https://astro.build/)                          | Landing Page focada em SEO e performance.        |
| **Dashboard/App**   | [VITE REact \_ React Router](https://vitejs.dev/)      | Painel administrativo e onboarding (App Router). |
| **Backend API**     | [Hono](https://hono.dev/) ou Express                   | API leve para webhooks e lógica de IA.           |
| **Banco de Dados**  | [Supabase](https://supabase.com/)                      | PostgreSQL + pgvector (RAG) + Auth.              |
| **ORM**             | [Prisma](https://www.prisma.io/)                       | Modelagem e type-safety.                         |
| **WhatsApp Engine** | [Baileys](https://github.com/WhiskeySockets/Baileys)   | Conexão via WhatsApp Web (multi-device).         |
| **IA Engine**       | [LangChain](https://www.langchain.com/)                | Orquestração de agentes e ferramentas.           |
| **IA Model**        | [Vertex AI Gemini](https://cloud.google.com/vertex-ai) | Processamento de linguagem natural.              |

---

## 🛠️ 2. Fases de Desenvolvimento

### Fase 1: Fundação e Setup (Semana 1)

- [ ] Configuração do Turborepo com workspaces: `apps/web`, `apps/dashboard`, `apps/api`, `packages/ui`, `packages/db`.
- [ ] Setup do **Astro** para a Landing Page (priorizando SEO).
- [ ] Setup do **VITE REact \_ React Router** com Tailwind e Shadcn UI para o Dashboard.
- [ ] Modelagem do banco de dados (Prisma):
  - `Tenant`: Dados da empresa e plano.
  - `Agent`: Persona, tom de voz e instruções.
  - `Lead`: Dados capturados, score e status.
  - `Conversation`: Histórico de mensagens.
  - `Product`: Catálogo de produtos para RAG.

### Fase 2: WhatsApp Gateway & Messaging (Semana 2)

- [ ] Implementação do serviço de conexão WhatsApp usando **Baileys**.
- [ ] Sistema de gestão de sessões Multi-tenant (armazenar `auth_state` no Supabase por tenant).
- [ ] Fluxo de pareamento via QR Code no Dashboard.
- [ ] Webhook para captura de mensagens recebidas e envio de respostas.
- [ ] Sistema de fila (BullMQ/Redis) para garantir que nenhuma mensagem seja perdida.

### Fase 3: IA Sales Agent (LangChain + Vertex AI Gemini) (Semana 3)

- [ ] Implementação do Agente de Vendas com Vertex AI Gemini.
- [ ] **Tools & Functions** integradas ao LangChain:
  - `qualify_lead(data)`: Avalia se o lead é quente/morno/frio e atualiza o DB.
  - `search_catalog(query)`: Busca semântica no catálogo (RAG com pgvector).
  - `create_payment_link(amount, product)`: Integração com Stripe/PagSeguro.
  - `book_meeting()`: Integração com Calendly.
  - `transfer_to_human()`: Pausa o agente para intervenção manual.
- [ ] Prompt System Dinâmico: Injecão da persona configurada pelo usuário no prompt inicial.

### Fase 4: Onboarding & Dashboard (Semana 4)

- [ ] Construção do **Wizard Onboarding** (5 passos conforme Design System):
  1. Conectar WhatsApp (QR).
  2. Definir Persona (Dropdowns e prompt builder).
  3. Upload de Catálogo (CSV/Excel → Embeddings pgvector).
  4. Definir Fluxos (Perguntas de qualificação).
  5. Ativar Agente.
- [ ] Dashboard de Métricas: Gráficos de conversão, leads qualificados e ROI.
- [ ] Interface de Conversas Ativas: Visualização em tempo real e handoff manual.

### Fase 5: Refinamento e Áudio (Semana 5)

- [ ] Integração de áudio:
  - Transcrição de áudio recebido (**Whisper**).
  - Síntese de voz para respostas (ElevenLabs ou similar).
- [ ] Testes E2E com Playwright.
- [ ] Otimizações de performance e tratamento de erros (rate limits da Anthropic).
- [ ] Deploy em produção (Vercel para apps, Railway/Supabase para API/DB).

---

## 🎯 3. Métodos e Ações do Agente (LangChain)

Para que o agente venda efetivamente, ele operará sob os seguintes comportamentos programados:

1. **Escuta Ativa**: Identificar dores e necessidades do cliente antes de oferecer produtos.
2. **Qualificação Progressiva**: Fazer perguntas de qualificação diluídas na conversa (não parecer um formulário).
3. **Recomendação Baseada em Contexto**: Usar RAG para sugerir o produto exato que resolve a dor do cliente.
4. **Tratamento de Objeções**: Baseado na lista de FAQ enviada pelo usuário no onboarding.
5. **Fechamento Ágil**: Detectar intenção de compra e disparar o link de pagamento imediatamente.

---

## 🔒 4. Segurança e Compliance

- **Isolamento de Dados**: Utilização de Row Level Security (RLS) no Supabase para garantir que um tenant nunca veja dados de outro.
- **LGPD**: Fluxo de consentimento no WhatsApp e criptografia de dados sensíveis.
- **Rate Limiting**: Proteção contra spam no WhatsApp para evitar banimento de números.

---

## 🚀 5. Próximos Passos Imediatos

1. Iniciar o Monorepo e Shared UI.
2. Implementar o esqueleto do Wizard de Onboarding.
3. Validar a conexão básica de um número WhatsApp via Baileys no ambiente de dev.
