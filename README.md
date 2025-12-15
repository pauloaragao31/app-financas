# PRD - Aplicativo de Finanças Pessoais Baseado em Chat
# Product Requirements Document

================================================================================
VISÃO GERAL
================================================================================

Objetivo: Criar um aplicativo de finanças pessoais que permite ao usuário 
registrar despesas, receitas e investimentos através de conversas naturais, 
com classificação automática e relatórios simples.

================================================================================
REQUISITOS PRINCIPAIS
================================================================================

1. INTERFACE PRINCIPAL EM FORMATO DE CHAT
   - Tela principal com interface conversacional
   - Mensagens do usuário e do assistente diferenciadas visualmente
   - Campo de entrada de texto para envio de mensagens
   - Ações rápidas para consultas comuns

2. REGISTRO VIA LINGUAGEM NATURAL
   - Despesas: "gastei 30 reais no mercado"
   - Receitas: "recebi 5000 de salário"
   - Investimentos: "investi 1000 em ações"
   - Classificação automática de categoria

3. VISUALIZAÇÃO DE DADOS
   - Saldo geral (receitas - despesas)
   - Total de despesas
   - Total de receitas
   - Total investido

4. META FINANCEIRA SIMPLES
   - Criar meta com valor alvo
   - Acompanhar progresso
   - Visualização de percentual atingido

5. RELATÓRIO CONSOLIDADO
   - Resumo financeiro geral
   - Lista de transações recentes
   - Design minimalista e claro

================================================================================
COMPORTAMENTO ESPERADO
================================================================================

ENTRADA DO USUÁRIO          | AÇÃO DO SISTEMA
----------------------------|------------------------------------------------
"gastei 30 reais no mercado"| Registra despesa de R$30 na categoria mercado
"recebi 5000 de salário"    | Registra receita de R$5000 na categoria salário
"investi 1000 em ações"     | Registra investimento de R$1000 em ações
"meu saldo"                 | Retorna saldo atual
"minhas despesas"           | Retorna total e lista de despesas
"minhas receitas"           | Retorna total e lista de receitas
"meus investimentos"        | Retorna total e lista de investimentos
"meta de 10000 para carro"  | Cria meta de R$10.000 chamada "carro"

================================================================================
ESTRUTURA DO PROJETO
================================================================================

/src
├── components/
│   ├── cards/
│   │   ├── GoalCard.tsx         # Cartão de meta
│   │   ├── InvestmentCard.tsx   # Cartão de investimento
│   │   ├── SummaryCard.tsx      # Cartão de resumo
│   │   └── TransactionCard.tsx  # Cartão de transação
│   ├── chat/
│   │   ├── ChatBubble.tsx       # Bolha de mensagem
│   │   ├── ChatInput.tsx        # Campo de entrada
│   │   └── QuickActions.tsx     # Ações rápidas
│   └── layout/
│       ├── BottomNav.tsx        # Navegação inferior
│       └── Header.tsx           # Cabeçalho
├── lib/
│   ├── financeParser.ts         # Interpretador de linguagem natural
│   └── utils.ts                 # Utilitários
├── pages/
│   ├── Chat.tsx                 # Tela principal de chat
│   ├── Goals.tsx                # Tela de metas
│   ├── Investments.tsx          # Tela de investimentos
│   └── Report.tsx               # Tela de relatório
├── store/
│   └── financeStore.ts          # Gerenciamento de estado (Zustand)
└── types/
    └── finance.ts               # Tipos TypeScript

================================================================================
MODELOS DE DADOS
================================================================================

TRANSACTION {
  id: string
  type: 'income' | 'expense' | 'investment'
  amount: number
  category: TransactionCategory
  description: string
  date: Date
}

GOAL {
  id: string
  name: string
  targetAmount: number
  currentAmount: number
  deadline?: Date
}

INVESTMENT {
  id: string
  name: string
  type: 'stocks' | 'crypto' | 'fixed' | 'funds' | 'other'
  amount: number
  date: Date
}

CHAT_MESSAGE {
  id: string
  content: string
  sender: 'user' | 'assistant'
  timestamp: Date
  transaction?: Transaction
}

================================================================================
CATEGORIAS DE TRANSAÇÃO
================================================================================

- alimentação (food)
- transporte (transport)
- moradia (housing)
- saúde (health)
- educação (education)
- lazer (entertainment)
- compras (shopping)
- serviços (utilities)
- salário (salary)
- freelance
- investimento (investment)
- outros (other)

================================================================================
DESIGN E UX
================================================================================

PRINCÍPIOS:
- Simplicidade e clareza
- Acessibilidade
- Foco em informação
- Tema escuro padrão

CORES SEMÂNTICAS:
- Income (receita): Verde (#22c55e)
- Expense (despesa): Vermelho (#ef4444)
- Investment (investimento): Azul (#3b82f6)

NAVEGAÇÃO:
- 4 abas principais: Chat, Relatório, Metas, Investimentos
- Navegação inferior fixa
- Cabeçalho com título da seção

================================================================================
TECNOLOGIAS UTILIZADAS
================================================================================

- React 18
- TypeScript
- Vite
- Tailwind CSS
- Shadcn/UI
- Zustand (gerenciamento de estado)
- React Router DOM (navegação)
- Lucide React (ícones)

================================================================================
PRÓXIMOS PASSOS (ROADMAP)
================================================================================

1. Integração com Lovable Cloud/Supabase para persistência
2. Autenticação de usuários
3. IA real para interpretação de mensagens (Gemini/GPT)
4. Gráficos visuais (pizza, barras)
5. Filtros por data e categoria
6. Orçamento mensal por categoria
7. Exportação PDF/CSV
8. Notificações e alertas

================================================================================
<img width="886" height="498" alt="image" src="https://github.com/user-attachments/assets/50306a00-b602-411d-8017-a9ccaad92b1f" />
<img width="886" height="498" alt="image" src="https://github.com/user-attachments/assets/33d4cd6b-00a4-4594-a78c-7051a72d7235" />
<img width="886" height="498" alt="image" src="https://github.com/user-attachments/assets/6c20c9cf-4b27-48f0-8592-36900a4e80d6" />



•	Uma breve reflexão sobre o processo:
o	O que funcionou bem?
Os menus iniciais 
o	O que não funcionou como o esperado?
 Ser mais especifico ao colocar os valores de entrada e saída
o	O que aprendeu sobre conversar com IAs?
o	São ferramentas uteis, mas não substituem o trabvalho como um todo, podem ajudar e ganhar tempo mas não dá para confiar cegamente neslas devido a questão de alucinação delas e precisa no mínimo ter noção do que está pedindo e fazendo para ter uma base para criticar e modificar se necessário a entrega da IA.




