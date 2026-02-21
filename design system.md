# Design System WhatsSell AI

## 1. Fundamentos de Design

### 1.1 Princípios de UX
- **Simplicidade**: Interface intuitiva para PMEs sem expertise técnica
- **Velocidade**: Onboarding <10min, respostas <3s visíveis
- **Confiança**: Transparência em decisões da IA, métricas claras
- **Contextualização**: Sempre mostrar status do agente e conversas ativas
- **Ação Facilitada**: CTAs claros, fluxos no-code sem fricção

### 1.2 Persona do Usuário
- Proprietário PME, 35-55 anos, mobile-first user
- Baixa tolerância a complexidade, alta demanda por resultados
- Busca autonomia 24/7 com suporte humano disponível
- Valida decisões via métricas simples e visuais

---

## 2. Arquitetura Visual

### 2.1 Sistema de Cores

#### Paleta Principal
```
Cor Primária: #0EA5E9 (Sky Blue)
├─ Light: #E0F2FE (bg-sky-50)
├─ Base: #0EA5E9 (buttons, highlights)
└─ Dark: #0369A1 (hover states)

Cor Secundária: #10B981 (Emerald - Sucesso)
├─ Light: #D1FAE5
├─ Base: #10B981
└─ Dark: #047857

Cor Alerta: #F59E0B (Amber - Atenção)
├─ Light: #FEF3C7
└─ Dark: #D97706

Cor Erro: #EF4444 (Red - Bloqueio)

Neutros:
├─ Texto: #1F2937 (gray-800)
├─ Secundário: #6B7280 (gray-500)
├─ Bordas: #E5E7EB (gray-200)
└─ Fundo: #FFFFFF / #F9FAFB (gray-50)
```

**Justificativa**: Sky Blue projeta confiança tech, Emerald reforça sucesso (conversões), cores quentes para urgência.

### 2.2 Tipografia

```
Font Stack: Inter (sans-serif primária), JetBrains Mono (código)

Escalas:
├─ Heading 1 (H1): 32px / 40px (bold) - Títulos página
├─ Heading 2 (H2): 24px / 32px (semibold) - Seções
├─ Heading 3 (H3): 18px / 28px (semibold) - Subsções
├─ Body Large: 16px / 24px - CTA, labels importantes
├─ Body Regular: 14px / 22px - Texto corpo
├─ Body Small: 12px / 18px - Helpers, timestamps
└─ Caption: 11px / 16px - Notas, badges

Line Height: 1.5x para leitura, 1.25x para headlines
Letter Spacing: +0.5% para headlines, normal para corpo
```

### 2.3 Espaçamento (8px base)

```
xs: 4px (micro spacing)
sm: 8px (componentes internos)
md: 16px (padding padrão)
lg: 24px (seção spacing)
xl: 32px (major sections)
2xl: 48px (page margins)
```

### 2.4 Sombras e Elevação

```
Elevation 1 (Cards, modals): 0 1px 3px rgba(0,0,0,0.1)
Elevation 2 (Floating actions): 0 4px 6px rgba(0,0,0,0.1)
Elevation 3 (Dropdowns, tooltips): 0 10px 15px rgba(0,0,0,0.1)
Focus: Outline 2px #0EA5E9 com offset 2px
```

---

## 3. Componentes Core

### 3.1 Buttons

```
Variantes:
├─ Primary (Sky): Ações principais, CTAs
│  ├─ Resting: bg-sky-500, text-white
│  ├─ Hover: bg-sky-600, shadow-elevation2
│  └─ Active: bg-sky-700
├─ Secondary (Outline): Ações secundárias
│  ├─ Border: 2px solid sky-500, text-sky-600
│  └─ Hover: bg-sky-50
├─ Success (Emerald): Confirmar, próximo passo
│  └─ bg-emerald-500
├─ Danger (Red): Delete, logout
│  └─ bg-red-500
└─ Ghost: Links, ações baixa prioridade
   └─ text-sky-600, no background

Tamanhos:
├─ sm: px-3 py-1.5, text-12px (ações secundárias)
├─ md: px-4 py-2.5, text-14px (padrão)
└─ lg: px-6 py-3, text-16px (CTAs principais)

Estados:
├─ Normal: cursor-pointer
├─ Hover: elevation + 0.5 escala
├─ Active: sombra interna
├─ Disabled: opacity-50, cursor-not-allowed
└─ Loading: spinner + text "Processando..."
```

### 3.2 Inputs e Forms

```
Componentes:
├─ Text Input
│  ├─ Border: 1px solid gray-200, radius 6px
│  ├─ Padding: 10px 12px (16/14px altura)
│  ├─ Focus: border-sky-500, ring-2 ring-sky-100
│  └─ Placeholder: text-gray-400, italic
│
├─ Select / Dropdown
│  ├─ Trigger: Button-like, chevron icon à direita
│  ├─ Menu: max-height 300px, scroll interno
│  └─ Highlight: bg-sky-50 no hover
│
├─ Checkbox & Radio
│  ├─ 16x16px checked mark
│  ├─ Checked: bg-sky-500
│  └─ Label adjacente, clickable
│
├─ Toggle Switch
│  ├─ Width: 44px, Height: 24px
│  ├─ Off: bg-gray-300, On: bg-emerald-500
│  └─ Animated: transition 200ms

└─ Textarea
   ├─ Min-height: 80px
   ├─ Resize: vertical only
   └─ Mesma estilização input
```

### 3.3 Cards e Containers

```
Card Base:
├─ Border: 1px solid gray-200
├─ Radius: 8px
├─ Padding: 16px / 24px
├─ Shadow: elevation-1
├─ Hover: elevation-2 (opcional)
└─ Background: white

Variantes:
├─ Elevated: shadow-elevation2, hover elevate
├─ Flat: sem shadow, outline apenas
├─ Interactive: cursor-pointer, hover effect
└─ Alert Card
   ├─ Border-left: 4px solid (color by severity)
   ├─ bg-color-50 (light tint)
   └─ icon + message inline

Layouts:
├─ Grid: 1-4 cols (responsive), gap-16px
├─ List: stacked cards, dividers
└─ Panel: single dominant card, full width
```

### 3.4 Badges e Labels

```
Tamanho: sm (12px text, 4px padding), md (14px text, 6px padding)

Tipos:
├─ Status
│  ├─ Active: bg-emerald-100, text-emerald-800
│  ├─ Inactive: bg-gray-100, text-gray-800
│  ├─ Pending: bg-amber-100, text-amber-800
│  └─ Error: bg-red-100, text-red-800
│
├─ Qualificação Lead
│  ├─ Frio: bg-blue-100, text-blue-800
│  ├─ Morno: bg-amber-100, text-amber-800
│  └─ Quente: bg-emerald-100, text-emerald-800
│
└─ Features
   ├─ Novo: bg-sky-100, text-sky-800, "New" badge
   └─ Pro: bg-purple-100, text-purple-800
```

### 3.5 Tables / Data Display

```
Estrutura:
├─ Header: bg-gray-50, font-semibold, sticky top
├─ Rows: 44px height, alternating bg (none/gray-50)
├─ Cells: 12px padding horizontal, 8px vertical
├─ Borders: 1px solid gray-200 (horizontal)
└─ Last row: com bottom border

Features:
├─ Sorting: Click header, chevron up/down
├─ Filtering: Input acima table, filtra real-time
├─ Pagination: "1-20 de 150" + prev/next buttons
├─ Row actions: Menu icon (⋮) no hover, dropdown
└─ Row selection: Checkbox first column, bulk actions

Responsivo:
├─ < 768px: Esconde colunas menos críticas
├─ Stack em cartões: Label + valor, 1 coluna
└─ Horizontal scroll com "Swipe para ver mais"
```

### 3.6 Modals e Dialogs

```
Backdrop: rgba(0, 0, 0, 0.5), fade-in
Container:
├─ Width: max 600px (sm), 800px (lg)
├─ Radius: 12px
├─ Shadow: elevation-3
├─ Padding: 24px
└─ Close button: X (top-right, grayish)

Estrutura interna:
├─ Header: title (H2), close X
├─ Body: conteúdo, scroll se > 70vh
├─ Footer: buttons (Cancel, Action)
   ├─ Cancel: Secondary button (gray)
   └─ Action: Primary button (sky-blue)

Animação:
├─ Enter: scale 0.95 → 1, fade 0 → 1 (300ms)
└─ Exit: fade 1 → 0 (200ms)
```

### 3.7 Navigation

#### Top Navigation (Header)
```
Height: 64px
Background: white, border-bottom 1px gray-200

Layout:
├─ Left: Logo + product name "WhatsSell AI"
├─ Center: (vazio em admin, raro uso)
├─ Right:
│  ├─ Notifications bell (com badge vermelha se >0)
│  ├─ User avatar (32x32px, initial ou image)
│  └─ Dropdown menu (settings, logout)

Responsive:
└─ < 768px: Logo menor, icon-only buttons
```

#### Sidebar (Dashboard)
```
Width: 256px (desktop), slide-out modal (mobile)
Background: white, border-right 1px gray-200
Sticky: position fixed

Items (Navigation Links):
├─ Icon (24px) + Label (14px)
├─ Padding: 12px 16px
├─ Hover: bg-gray-50
├─ Active: bg-sky-50, border-left 4px sky-500, bold label
└─ Submenus: indented, collapse/expand

Footer sidebar:
└─ User info mini (avatar 32x32, name, "Sair" link)

Sections:
├─ Conversas (Main)
├─ Leads
├─ Analytics
├─ Agente (Config)
├─ Integrações
└─ Configurações
```

---

## 4. Padrões de Interface

### 4.1 Onboarding Wizard

```
Container: Modal OR full-screen, 600px max-width

Estrutura:
├─ Progress bar: 0-100%, cores step atual (sky-500)
├─ Step title: H2, descritivo
├─ Step description: Body small, contexto
├─ Form elements: 1 foco por step
└─ Actions: Back (gray), Next (sky-primary), Skip (ghost)

Fluxo de 5 steps:
1. Conectar WhatsApp (QR code scanner ou token)
2. Definir Persona (dropdown: roupas, serviços, e-commerce + custom)
3. Configurar Catálogo (upload CSV ou manual)
4. Fluxo Qualificação (builder visual: 3-5 perguntas)
5. Review & Ativar (confirmação, botão "Começar Vendas")

UX Details:
├─ Salvar progresso (localStorage)
├─ Volta ao passo anterior sem perder dados
├─ Animação suave entre steps (fade + slide)
└─ Toast success ao finalizar: "Agente ativo! Pronto para vendas 🎉"
```

### 4.2 Dashboard Principal

```
Layout: 3-column grid (desktop), 1-column (mobile)

Grid Principais:
├─ COL 1 (40%):
│  ├─ Card Status Agente
│  │  ├─ Dot indicator: Verde (ativo), Amarelo (paused), Cinza (off)
│  │  ├─ Tempo ativo hoje
│  │  └─ Quick toggle: "Pausar Agente" button
│  │
│  └─ Card Conversas Ativas
│     ├─ Mini-list: últimas 5 conversas
│     ├─ Avatar + nome cliente + preview mensagem
│     └─ Click → abre conversation modal

├─ COL 2 (30%):
│  ├─ KPI Cards (vertical stack)
│  ├─ Leads qualificados: número grande + "↑ 12%" (verde)
│  ├─ Taxa resposta: percentual + trend
│  └─ Vendas hoje: R$ valor em verde

└─ COL 3 (30%):
   ├─ Quick Actions (vertical, botões cheios)
   ├─ "Editar Agente" → settings
   ├─ "Ver Relatórios" → analytics
   ├─ "Integrar CRM" → integrações
   └─ "Suporte" → help (chat ou link)
```

### 4.3 Conversations View

```
Layout: Split-view
├─ Left (40%): Conversation list
│  ├─ Search input (filter por nome/phone)
│  ├─ Filter badges: "Todas", "Quentes", "Pendentes"
│  └─ Stacked list items:
│     ├─ Avatar (initials ou imagem)
│     ├─ Name + phone
│     ├─ Last message preview (truncado)
│     ├─ Timestamp (relativo: "5m")
│     └─ Status badge (frio/morno/quente)
│        Hover: bg-gray-50, cursor-pointer
│        Selected: bg-sky-50, border-left sky-500
│
└─ Right (60%): Conversation detail
   ├─ Header:
   │  ├─ Name + phone
   │  ├─ Qualification score
   │  ├─ Menu actions (assign human, archive)
   │  └─ Close button (X)
   │
   ├─ Messages feed (scrollable):
   │  ├─ Message bubbles:
   │  │  ├─ Bot (left): bg-gray-100, radius full
   │  │  ├─ User (right): bg-sky-500, white text
   │  │  ├─ Timestamp (gray-400, 12px)
   │  │  └─ Avatar (left only)
   │  │
   │  └─ Contextual info:
   │     ├─ "Agente sugeriu: Link pagamento"
   │     └─ Card com button inline
   │
   └─ Action bar (bottom):
      ├─ Text input (white, border sky-200)
      ├─ File upload icon
      ├─ Emoji icon (opcional)
      └─ Send button (paper plane, sky-500)
```

### 4.4 Leads Table

```
Colunas (personalizáveis):
├─ Nome (16px text, avatar pequeno)
├─ Telefone (12px, copyable)
├─ Qualificação (badge: frio/morno/quente + %)
├─ Empresa/Serviço
├─ Último contato (timestamp relativo)
├─ Valor estimado (R$ em bold)
└─ Ações (⋮ menu: detalhes, atribuir, arquivar)

Funcionalidades:
├─ Sort: clicável header, chevron asc/desc
├─ Filter: dropdown por qualificação
├─ Bulk actions: checkbox, "Atribuir a X", "Enviar proposta"
├─ Pagination: "1-50 de 2.547 leads"
└─ Export: Botão "Baixar CSV"

Row interativa:
├─ Hover: subtle bg-gray-50
├─ Click: abre modal com detalhes (histórico, notas)
└─ Mobile: card-based layout
```

### 4.5 Analytics / Reports

```
Seção: Relatórios (tab no sidebar)

Cards KPI (1-4 cols grid):
├─ Título (14px, bold)
├─ Número grande (32px, bold)
├─ Trend (↑ 15% / ↓ 5% em verde/vermelho)
├─ Período seletor (dropdown: "Última semana", "Mês", "Custom")
└─ Sparkline chart (mini gráfico inline, opcional)

Gráficos (Charts):
├─ Conversas/dia (line chart, 7 dias)
├─ Funil vendas (bar chart: prospects → conversão)
├─ ROI (área chart: revenue vs spend)
└─ Taxa resposta por hora (heatmap: horas do dia)

Tabelas analíticas:
├─ Integrações: Stripe links enviados, cliques, conversões
├─ Top produtos: mais recomendados, CTR
└─ Perguntas falhas: respostas que causaram drop-off

Export:
└─ Botão: "Baixar relatório" (PDF ou CSV)
```

### 4.6 Agent Configuration

```
Seção: Agente (settings)

Abas:
├─ Identidade (Persona)
│  ├─ Tipo vendedor: dropdown (roupas, serviços...)
│  ├─ Tom de voz: buttons (formal, amigável, técnico)
│  ├─ Descrição custom: textarea (instruções base)
│  └─ Avatar: upload imagem ou emoji
│
├─ Conhecimento (RAG)
│  ├─ Upload catálogo: drag-drop CSV/PDF
│  ├─ Adicionar FAQ: form para Q&A
│  └─ Base conhecimento: lista de docs
│
├─ Fluxos Prontos
│  ├─ Boas-vindas: ativar/desativar + customizar texto
│  ├─ Qualificação: visualizar 3-5 perguntas
│  ├─ Follow-up: timing (24h default)
│  └─ Recuperação carrinho: trigger rules
│
├─ Funções (Function Calling)
│  ├─ Qualificar lead: on/off toggle
│  ├─ Enviar pagamento: integração (Stripe/PagSeguro)
│  ├─ Agendar: integração (Calendly/Google)
│  └─ Handoff: ativar chat com humano
│
└─ Integrações
   ├─ CRM: HubSpot/Pipedrive (conectar)
   ├─ Analytics: GA4 pixel
   └─ Webhook custom: URL + eventos

Salvar: Botão "Atualizar agente" (verde), toast "Mudanças salvas"
```

### 4.7 Notifications & Alerts

```
Toast (bottom-right):
├─ Success: bg-emerald-500, icon ✓, fade out 4s
├─ Error: bg-red-500, icon ✗, persist
├─ Info: bg-sky-500, icon ℹ, fade out 6s
└─ Warning: bg-amber-500, icon ⚠, fade out 5s

Texto: 14px, white, padding 12px 16px, radius 6px

Bell Notification (Header):
├─ Dropdown: lista de notificações
├─ Item: icon + mensagem (14px) + timestamp
├─ Max 5 visíveis, "Ver todas" link
└─ Mark as read: clica item

In-App Alerts (inline):
├─ Info banner: bg-sky-50, border-left sky-500
├─ Alert card: icon + mensagem + "Dismiss" X
└─ Status change: "Agente foi pausado por limite de API"
```

---

## 5. Fluxos e Comportamentos

### 5.1 Responsividade

```
Breakpoints:
├─ Mobile (< 640px): stack 1 col, sidebar collapse
├─ Tablet (640-1024px): 2 colunas, sidebar icon-only
└─ Desktop (> 1024px): 3+ cols, sidebar full

Adaptações:
├─ Navigation: hamburger menu (mobile), full sidebar (desktop)
├─ Tables: scroll horizontal (mobile), grid normal (desktop)
├─ Modals: fullscreen (mobile), centered (desktop)
├─ Fonts: -2px (mobile), normal (desktop)
└─ Spacing: -50% (mobile), normal (desktop)
```

### 5.2 Estados de Loading

```
Full page: skeleton loaders
├─ Cards: shimmer effect (gradiente animado)
├─ Tables: 5 empty rows, alternating cinza
└─ Duração: aparência < 3s real

Inline: spinner + text
├─ Button: disabled + spinner icon inside
├─ Input: disabled state, spinner à direita
└─ Text: "Carregando...", "Salvando..."

Delayed: mostrar after 300ms (evita flicker rápido)
```

### 5.3 Validação e Erros

```
Campo-level:
├─ Borda vermelha (1px border-red-500)
├─ Mensagem erro: 12px, text-red-500, below input
├─ Icon error: ✗ red
└─ Real-time (após blur ou typing pause)

Form-level:
├─ Alert card no topo do form
├─ Listar todos os erros com links (jump to field)
└─ Disable submit button

Exemplos:
├─ Email: "Email inválido"
├─ Senha: "Min. 8 caracteres, 1 maiúscula, 1 número"
├─ WhatsApp token: "Token inválido. Tente reconectar"
└─ Período: "Data fim deve ser após data início"
```

### 5.4 Confirmações Críticas

```
Destrutuivo actions (delete, archive, logout):
├─ Modal com:
│  ├─ Título: "Tem certeza?"
│  ├─ Descrição: contexto e consequência
│  ├─ Botão confirmar: vermelho (danger), requer click
│  └─ Botão cancelar: gray
│
└─ Undo possível (após ação): "Lead arquivado. Desfazer?"
```

### 5.5 Animações e Transições

```
Duração padrão: 200ms (cubic-bezier(0.4, 0, 0.2, 1))

Uso:
├─ Hover state: elevation + color shift
├─ Modal entrada: scale + fade
├─ Mensagens: slide-in da lateral
├─ Toast: slide-in bottom-right
├─ Toggle: rotate indicator icon
└─ Menu open: scale + fade

Princípio: suave mas não distração; speed feedback
```

---

## 6. Padrões de Conteúdo

### 6.1 Microcopy

```
Botões:
├─ "Conectar WhatsApp" (CTA claro)
├─ "Próximo" (wizard progresso)
├─ "Salvar mudanças" (confirma ação)
├─ "Concluir onboarding" (motivacional)
└─ "Desfazer" (reversão)

Labels:
├─ "Qualificação do lead" (descritivo)
├─ "Ativar agente 24/7" (benefit language)
├─ "Tempo resposta médio: 0.8s" (métrica crua)
└─ "Próximas ações para XYZ" (contextual)

Erros:
├─ "Email já cadastrado. Faça login ou use outro email."
├─ "WhatsApp offline. Reconectar?" (acionável)
├─ "Limite API atingido hoje. Upgrade para Pro." (orientação)
└─ "Algo deu errado. Tente novamente ou contate suporte."

Helpers:
├─ "💡 Dica: Use tom amigável para melhor engajamento"
├─ "ℹ Seu agente processou 234 mensagens hoje"
└─ "🎯 1 lead novo esperando qualificação"
```

### 6.2 Ícones

```
Sistema: Heroicons (outline) ou Feather
Tamanho padrão: 20px (headers), 24px (buttons), 16px (inline)

Ícones chave:
├─ Dashboard: house
├─ Conversas: message-circle
├─ Leads: users
├─ Analytics: bar-chart-2
├─ Configurações: settings
├─ Integrações: plug
├─ WhatsApp: (logo)
├─ Sucesso: check-circle
├─ Erro: alert-circle
├─ Alerta: alert-triangle
├─ Carregando: loader (spinner)
├─ Menu: menu / x (close)
└─ More: more-vertical (⋮)

Cor padrão: inherit text color, muda com estado
```

### 6.3 Mensagens de Status

```
Agente ativo:
├─ "Agente online · Pronto para vendas · Último lead: 5m"

Sem conversas:
├─ Ilustração vazia (minimal)
├─ "Sem conversas no período"
├─ CTA: "Começar a vender"

Qualificações:
├─ Lead frio: "Sem fit imediato. Seguir em 7 dias"
├─ Lead morno: "Interesse. Enviar proposta"
├─ Lead quente: "Alto potencial. Priorizar handoff"

Sistema limitado:
├─ "Agente pausado: limite diário atingido"
├─ "Upgrade para plano Pro para remover limite"
```

---

## 7. Acessibilidade

### 7.1 WCAG 2.1 AA Compliance

```
Cores:
├─ Contraste min. 4.5:1 (texto normal), 3:1 (large text)
├─ Não usar cor como único indicador (+ ícone/texto)
└─ Paleta colorblind-friendly

Navegação:
├─ Keyboard-only: Tab > focus outline visível (2px sky)
├─ Ordem lógica: top-to-bottom, left-to-right
├─ Skip links: "Pular para conteúdo" (header)
└─ Focus trap em modals

Conteúdo:
├─ Alt text: imagens descritivas (ex: "Avatar do usuário João")
├─ Form labels: <label> associado via id
├─ Heading hierarchy: h1 → h2 → h3 (sem pulos)
└─ Aria labels: role, aria-label (onde necessário)

Mobile:
├─ Touch targets: min. 44x44px (botões, inputs)
├─ Zoom: 200% sem horizontal scroll
└─ Motion: respeitar prefers-reduced-motion
```

### 7.2 Internacionalização

```
Idiomas suportados:
├─ PT-BR (primário)
├─ EN-US
└─ ES (roadmap)

Implementação:
├─ i18n lib: next-i18next (Next.js)
├─ Arquivos JSON por idioma
├─ Selector de idioma (footer ou settings)
└─ RTL support (future, se ES agrega)

Contexto cultural:
├─ Moeda: R$ (BR), $ (US/ES)
├─ Datas: DD/MM/YYYY (BR), MM/DD/YYYY (US)
├─ Telefone: +55 (11) 99999-9999 (BR)
└─ Fusos: BRT (-3), auto-detect
```

---

## 8. Tokens de Design (CSS/Tailwind)

```css
/* tailwind.config.js */

module.exports = {
  theme: {
    colors: {
      sky: { 50: '#E0F2FE', 500: '#0EA5E9', 600: '#0284C7', 700: '#0369A1' },
      emerald: { 100: '#D1FAE5', 500: '#10B981', 700: '#047857' },
      amber: { 100: '#FEF3C7', 500: '#F59E0B', 700: '#D97706' },
      red: { 100: '#FEE2E2', 500: '#EF4444' },
      gray: { 50: '#F9FAFB', 100: '#F3F4F6', 200: '#E5E7EB', 500: '#6B7280', 800: '#1F2937' },
    },
    spacing: {
      xs: '4px', sm: '8px', md: '16px', lg: '24px', xl: '32px', '2xl': '48px'
    },
    borderRadius: { sm: '6px', md: '8px', lg: '12px', full: '9999px' },
    fontSize: { 11: '11px', 12: '12px', 14: '14px', 16: '16px', 18: '18px', 24: '24px', 32: '32px' },
    boxShadow: {
      'elevation-1': '0 1px 3px rgba(0,0,0,0.1)',
      'elevation-2': '0 4px 6px rgba(0,0,0,0.1)',
      'elevation-3': '0 10px 15px rgba(0,0,0,0.1)',
    },
  }
}
```

---

## 9. Motion & Micro-interactions

```
Hover states:
├─ Button: elevation+1, color shift (-50 hue)
├─ Card: elevation-1 → elevation-2
├─ Link: underline + color change
└─ Icon: rotation +5deg (opcional)

Click feedback:
├─ Button: brief shadow interna (active state)
├─ Checkbox: scale 1 → 0.95 → 1
├─ Toggle: swipe animation + color
└─ Drag: visual placeholder

Loading:
├─ Spinner: rotate 360deg (linear, infinite)
├─ Skeleton: shimmer animation (1s loop)
├─ Progress bar: smooth fill (cubic-bezier)

Entrada de página:
├─ Fade in (opacity 0 → 1)
├─ Slide down (transform translateY -20px → 0)
└─ Duração: 300ms
```

---

## 10. Componentes Específicos do Domínio

### 10.1 WhatsApp Message Bubble

```
User message (right-aligned):
├─ Background: sky-500
├─ Text: white
├─ Radius: 12px, bottom-right 4px
├─ Padding: 10px 14px
├─ Max-width: 70% (desktop), 85% (mobile)
└─ Timestamp: 11px gray-300, bottom-right

Bot message (left-aligned):
├─ Background: gray-100
├─ Text: gray-800
├─ Radius: 12px, bottom-left 4px
├─ Avatar: 32x32px circle, left side
└─ Timestamp: 11px gray-400, below

Suggested actions (após mensagem bot):
├─ Inline buttons: pill-shaped, border sky, text sky
├─ Onclick: envia texto + atualiza mensagem
└─ Max 3 sugestões
```

### 10.2 Lead Qualification Score

```
Visual: Donut chart ou progress bar

Escala:
├─ 0-33%: Frio (blue) - Sem fit evidente
├─ 34-66%: Morno (amber) - Interessado, precisa nurture
├─ 67-100%: Quente (emerald) - Alto potencial, fechar

Detalhes (hover tooltip):
├─ Critérios: interesse (10%), budget (20%), timeline (15%), etc.
├─ Score total: fórmula clara
└─ Recomendação: "Próxima ação: enviar proposta"
```

### 10.3 Integration Status Cards

```
Card por integração:
├─ Logo integration (40x40px)
├─ Nome: "Stripe", "HubSpot", etc.
├─ Status: "Conectado" (verde dot) ou "Não conectado" (cinza)
├─ Last sync: timestamp relativo
├─ Actions: "Reconectar" ou "Desconectar" button
└─ Teste: "Fazer teste" button (verde)

Não conectado:
├─ Cinza-out design
├─ CTA: "Conectar agora"
└─ Descrição: "Sincronize leads automaticamente com HubSpot"
```

---

## 11. Guia de Implementação

### 11.1 Stack Recomendado
- **Frontend**: Next.js 15 + Tailwind CSS + Shadcn/ui
- **Icons**: Heroicons ou Feather Icons
- **Componentes**: Radix UI (unstyled) + custom Tailwind
- **Form**: React Hook Form + Zod validation
- **Charts**: Recharts ou Chart.js
- **i18n**: next-i18next
- **Animations**: Framer Motion (uso moderado)

### 11.2 Arquitetura de Componentes
```
/components
├─ /ui (primitivos Shadcn)
│  ├─ Button.tsx, Input.tsx, Modal.tsx
│  └─ Table.tsx, Badge.tsx, Card.tsx
├─ /domain (específicos WhatsSell)
│  ├─ AgentStatusCard.tsx
│  ├─ ConversationBubble.tsx
│  ├─ LeadQualificationBadge.tsx
│  ├─ OnboardingWizard.tsx
│  └─ IntegrationStatusCard.tsx
├─ /layout
│  ├─ Header.tsx
│  ├─ Sidebar.tsx
│  └─ DashboardLayout.tsx
└─ /icons (custom SVGs)
```

### 11.3 Página Checklist
- [ ] Heading structure (h1 > h2 > h3)
- [ ] Color contrast (4.5:1 padrão, 3:1 large)
- [ ] Focus visible (2px sky outline)
- [ ] Form labels <label> com id
- [ ] Alt text em imagens
- [ ] Keyboard navigation funcional
- [ ] Responsive testar 3 breakpoints
- [ ] Loading states (skeleton/spinner)
- [ ] Error states com mensagens claras
- [ ] Toast/notifications testadas
- [ ] Microcopy consistente PT-BR

---

## 12. Conclusão

Este Design System prioriza:
1. **Simplicidade**: UI intuitiva, sem poluição, foco em ação
2. **Performance**: < 2s resposta, visuais leves (fonts, shadows moderados)
3. **Confiança**: Transparência via badges/status, erros claros
4. **Conversão**: CTAs proeminentes, fluxos rápidos (<5min), feedback imediato
5. **Escalabilidade**: Tokens reutilizáveis, componentes modulares, fácil manutenção

**Próximos passos**: Implementar Figma library com componentes, criar storybook, validar com usuários reais (PMEs).
