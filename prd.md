PRD: WhatsSell AI - SaaS Agente Vendedor WhatsApp
Visão do Produto
WhatsSell AI é uma plataforma SaaS multi-tenant que permite a PMEs criar e gerenciar agentes de IA autônomos para vendas no WhatsApp, usando Claude AI para conversas naturais, qualificação de leads e fechamentos automáticos. O foco é simplicidade no-code, com onboarding em minutos, para escalar vendas 24/7 sem equipes grandes.

Público-Alvo
PMEs no Brasil (e-commerce, serviços locais em Curitiba/PR).

Proprietários de negócios com WhatsApp Business, sem expertise técnica.

Necessidades: qualificar leads, recuperar carrinhos, agendar vendas, integrações básicas (pagamentos, CRM).

Requisitos Funcionais
Onboarding e Configuração
Cadastro via email/Google, integração WhatsApp Cloud API via QR ou token Meta (multi-contas).
​

Wizard no-code: definir persona do vendedor (ex: "vendedor amigável de roupas"), FAQs, produtos/serviços, objeções comuns, fluxos de qualificação (3-5 perguntas).

Treinamento inicial com Claude: upload catálogo/produtos, prompts personalizáveis.

Agente de Vendas Core
Recebe mensagens via webhook WhatsApp → envia para Claude (com histórico contexto + instruções business).

Funcionalidades Claude function calling: qualificar lead (pontuação fria/quente), recomendar produtos, enviar links pagamento (Stripe/PagSeguro), agendar via Calendly/Google Calendar, handoff humano.
​
​

Suporte áudio/texto/imagens: transcreve áudio com Whisper, responde em texto/áudio gerado.

Fluxos prontos: boas-vindas, qualificação, upsell, follow-up (24h sem resposta), recuperação carrinho.

Dashboard Admin
Visão unificada: conversas ativas, leads qualificados (tabela com pontuação/telefone), métricas (conversões, taxa resposta).

Editar agente: ajustar prompts, adicionar conhecimentos (base RAG simples via Supabase/Vector DB).

Relatórios: ROI vendas, mensagens/dia, integrações export CSV/Zapier.

Integrações
Pagamentos: Stripe, PagSeguro (gerar links).

CRM: HubSpot, Pipedrive (push leads).

Analytics: Google Analytics, WhatsApp Insights.
​

Requisitos Não-Funcionais
Performance: <2s resposta, 1000+ conversas/dia/tenant (auto-scale).

Segurança: Multi-tenant isolado (PostgreSQL row-level), GDPR/LGPD, criptografia mensagens.

Escalabilidade: Serverless (Vercel/AWS Lambda).

Uptime: 99.9%, monitoring Sentry.

Idioma: PT-BR prioritário, suporte EN/ES.
​

Arquitetura Técnica (para Claude Code)
Estrutura modular para implementação iterativa com Claude:

text
Monorepo (Turborepo/Nx)
├── frontend/ (Next.js 15 App Router)
│ ├── /app: dashboard, wizard onboarding
│ ├── /components: UI (Shadcn/Tailwind)
│ └── /lib: auth (NextAuth/Clerk)
├── backend/ (Node.js/Express ou Hono)
│ ├── /routes: API (webhooks WhatsApp, Claude proxy)
│ ├── /services: claude.js (Anthropic SDK), whatsapp.js (Meta API)
│ ├── /db: Prisma + Supabase/Postgres (tenants, conversas, leads)
│ └── /ai: prompts.ts, functions (function calling)
├── shared/ (types, utils)
└── deploy: Vercel (frontend/backend), Railway/Supabase (DB)
Fluxo Principal:

Webhook WhatsApp → backend → enriquecer contexto (DB query tenant/lead) → Claude API (prompt system + function tools).

Claude retorna action/text → execute function (ex: createLead) → responda WhatsApp.

Banco: Tables: tenants, agents, conversations (JSON history), leads (score, stage).

Claude Integration: Use Anthropic SDK, models claude-3.5-sonnet/haiku, tools para functions (ex: {"name": "qualify_lead", "parameters": {...}}).
​

Dev Setup: npm init, npx create-next-app, Prisma migrate, env vars (ANTHROPIC_API_KEY, META_WHATSAPP_TOKEN).

User Flows (MVP)
Onboarding: Sign-up → conectar WhatsApp → config wizard (5min) → teste agente.

Venda Típica: Cliente msg → agente qualifica → envia proposta → confirma pagamento → handoff.

Monitor: Dashboard real-time, editar prompt, analytics.

Métricas de Sucesso (KPIs)
Métrica Meta Inicial Como Medir
Tempo Onboarding <10min Analytics funnel
Taxa Conversão Leads 20% qualificados Leads criados/vendas
Tempo Resposta <3s Logs
Retenção MRR 80% mês 1 Stripe churn
NPS >8 Survey pós-onboard
​
Roadmap MVP (4-6 Semanas)
Semana 1: Setup monorepo, auth, DB schema.

Semana 2: WhatsApp webhook + Claude basic chat.

Semana 3: Wizard config, functions (qualify/pay).

Semana 4: Dashboard MVP, testes E2E (Playwright).

Pós-MVP: Áudio, RAG avançado, white-label.
​

Riscos e Dependências
Depend: API Keys Claude/Anthropic (gratuito tier), Meta WhatsApp approval.

Riscos: Rate limits Claude (mitigar cache), compliance WhatsApp (só opt-in).

Custos: ~$0.01/1k tokens Claude, hospedagem $20/mês init.
​
