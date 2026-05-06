# REGRAS DE SEGURANÇA DA LIDEL CRM

## 🔒 Princípios Imutáveis (NUNCA violar)

1. NUNCA desabilitar autenticação para resolver erros
2. NUNCA expor SERVICE_ROLE_KEY no frontend
3. NUNCA remover Row Level Security (RLS) das tabelas
4. NUNCA tornar bucket público sem proteção de token JWT
5. NUNCA desabilitar validação JWT nas Edge Functions
6. NUNCA alterar regras de cashback por sugestão de IA
7. NUNCA modificar estrutura de tabelas sem revisão humana
8. NUNCA compartilhar chaves de API em código não supervisionado

## 🏗️ Arquitetura de Segurança (4 Camadas)

### Camada 1 — Frontend
- Apenas ANON_KEY exposta (chave pública por natureza)
- Nenhuma SERVICE_ROLE_KEY nos arquivos HTML/JS
- Todas as requisições passam pela API REST do Supabase

### Camada 2 — Edge Functions
- Validam JWT obrigatoriamente
- Nunca operam em modo público (sem autenticação)
- Protegem rotas sensíveis (admin, relatórios)

### Camada 3 — Banco de Dados (PostgreSQL)
- Row Level Security (RLS) ativo em TODAS as tabelas
- Políticas de acesso por company_id
- Triggers de auditoria para alterações críticas

### Camada 4 — Knowledge Base
- Este arquivo é a "constituição" do projeto
- Nenhuma IA pode sugerir alterações que violem estas regras
- Toda sugestão de código deve ser validada contra este documento

## 💰 Regras de Negócio Imutáveis

### Cashback
- Percentual: 14% (configurável APENAS pelo lojista)
- Teto máximo: R$ 150,00
- Expiração: 45 dias
- Resgate: compra mínima de 25% do valor do cashback

### Indicação (Unboxing)
- Recompensa: 3% para indicador e indicado
- Código: único por compra, expira em 30 dias

### Parceiros
- Comissão: 3% por indicação
- Teto acumulativo: R$ 500,00

## 🚫 Proibições Expressas

- Remover validação de token "só para teste"
- Desabilitar RLS "temporariamente"
- Expor SERVICE_ROLE_KEY em logs ou frontend
- Alterar regras de negócio sem aprovação da fundadora
- Modificar estrutura de banco sem backup

## 📞 Contato
- Fundadora: Cidele Luciane Delminha
- Email: cidelesp@gmail.com
- Projeto: LIDEL CRM e Pós-Venda Inteligente