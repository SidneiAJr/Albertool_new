# 🛠️ CommitToolsBR | Ferramenta de Ajuda com Commits Github

> **Gerador de mensagens de commit padronizadas para times brasileiros.**  
> Chega de mensagens genéricas ou fora do padrão. Seus commits organizados e profissionais com poucos cliques.

---

## 📋 Sobre o Projeto

O **CommitToolsBR** é uma CLI interativa desenvolvida em **Bash** que ajuda devs a criar mensagens de commit padronizadas seguindo o estilo **Conventional Commits**, com campos personalizados para chamados, módulos e descrições detalhadas.

Ele gera arquivos `.md` prontos para copiar, colar e commitar — ou você pode executar o commit direto pelo script.

🇧🇷 Feito no Brasil, focado em produtividade e organização.

---

## ✨ Funcionalidades

- ✅ Geração de mensagens para:
  - 🐛 **FIX** – Correção de bugs
  - ✨ **FEAT** – Novas funcionalidades
  - 💄 **STYLE** – Formatação e estilo
  - ♻️ **REFACTOR** – Refatoração de código
  - 📚 **DOCS** – Documentação
  - 🧪 **TEST** – Testes
  - ⚡ **PERF** – Performance
  - 🔧 **CHORE** – Tarefas
  - 🚀 **DEPLOY** – Deploy
  - 🔙 **REVERT** – Reversão

- ✅ Campos personalizados:
  - Número do chamado / tarefa
  - Descrição resumida
  - Módulo do projeto
  - Detalhes técnicos

- ✅ Geração automática de:
  - Data e hora
  - Autor (via git config)
  - Arquivos `.md` organizados por tipo

- ✅ Estatísticas de uso
- ✅ Menu interativo colorido
- ✅ Lista de mensagens prontas para copiar

---

### 1️⃣ Crie um arquivo de texto

### 2️⃣ Cole o código abaixo.

### 3️⃣ Salve como:

gerar_docs.sh

### Rode com git

```bash
#!/bin/bash

echo "======================================"
echo "   📝 GERADOR DE MENSAGENS DE COMMIT"
echo "======================================"
echo ""

# Define pasta base (se não existir, cria)
BASE_DIR="./commits_padrao"
mkdir -p "$BASE_DIR"

# ============================================
# FUNÇÃO: Correção (FIX)
# ============================================
gerador_fix(){
    local arquivo="$BASE_DIR/fix_$(date +%Y%m%d_%H%M%S).md"
    
    read -p "Número do chamado (opcional): " chamado
    [ -z "$chamado" ] && chamado="Não informado"
    
    read -p "Descrição resumida: " descricao
    read -p "Módulo (ex: Login, API, UI): " modulo
    
    cat <<EOF > "$arquivo"
# 🐛 FIX: $descricao

📌 Chamado: $chamado
📦 Módulo: $modulo
📅 Data: $(date '+%d/%m/%Y %H:%M')
👤 Autor: $(git config user.name 2>/dev/null || echo "Não identificado")

## 📝 Detalhes
- **Problema:** [descrever o problema]
- **Solução:** [descrever a solução]
- **Testes:** [testes realizados]
EOF

    echo "✅ Arquivo gerado: $arquivo"
}

# ============================================
# FUNÇÃO: Funcionalidade (FEAT)
# ============================================
gerador_feat(){
    local arquivo="$BASE_DIR/feat_$(date +%Y%m%d_%H%M%S).md"
    
    read -p "Número da tarefa (opcional): " tarefa
    [ -z "$tarefa" ] && tarefa="Não informado"
    
    read -p "Descrição da feature: " descricao
    read -p "Módulo (ex: Login, API, UI): " modulo
    
    cat <<EOF > "$arquivo"
# ✨ FEAT: $descricao

📌 Tarefa: $tarefa
📦 Módulo: $modulo
📅 Data: $(date '+%d/%m/%Y %H:%M')
👤 Autor: $(git config user.name 2>/dev/null || echo "Não identificado")

## 📝 Implementação
- **O que foi criado:** [descrever a nova funcionalidade]
- **Como funciona:** [explicar comportamento]
- **Arquivos alterados:** [listar principais arquivos]
EOF

    echo "✅ Arquivo gerado: $arquivo"
}

# ============================================
# FUNÇÃO: Estilo (STYLE)
# ============================================
gerador_style(){
    local arquivo="$BASE_DIR/style_$(date +%Y%m%d_%H%M%S).md"
    
    read -p "Descrição da mudança de estilo: " descricao
    read -p "Módulo: " modulo
    
    cat <<EOF > "$arquivo"
# 💄 STYLE: $descricao

📦 Módulo: $modulo
📅 Data: $(date '+%d/%m/%Y %H:%M')
👤 Autor: $(git config user.name 2>/dev/null || echo "Não identificado")

## 📝 Alterações
- **O que foi ajustado:** [formatação, espaçamento, etc]
- **Arquivos afetados:** [listar]
EOF

    echo "✅ Arquivo gerado: $arquivo"
}

# ============================================
# FUNÇÃO: Refatoração (REFACTOR)
# ============================================
gerador_refactor(){
    local arquivo="$BASE_DIR/refactor_$(date +%Y%m%d_%H%M%S).md"
    
    read -p "Descrição da refatoração: " descricao
    read -p "Módulo: " modulo
    
    cat <<EOF > "$arquivo"
# ♻️ REFACTOR: $descricao

📦 Módulo: $modulo
📅 Data: $(date '+%d/%m/%Y %H:%M')
👤 Autor: $(git config user.name 2>/dev/null || echo "Não identificado")

## 📝 Mudanças
- **O que foi melhorado:** [estrutura, legibilidade, etc]
- **Motivo:** [explicar por que refatorou]
- **Impacto:** [performance, manutenibilidade]
EOF

    echo "✅ Arquivo gerado: $arquivo"
}

lista_mensagem_commit(){
    local arquivo="$BASE_DIR/lista_mensagem_$(date +%Y%m%d_%H%M%S).md"
    cat <<EOF > "$arquivo"
    ## 🐛 **FIX (Correções)**
- fix(auth): corrige validação de email no login
- fix(api): ajusta status code 500 para 400 em requisições inválidas
- fix(ui): corrige overflow em mobile na tela de dashboard
- fix(database): resolve erro de conexão timeout
- fix(2fa): corrige validação de token expirado
- fix(login): ajusta mensagem de erro para credenciais inválidas
- fix(token): corrige renovação automática de JWT
- __________________________

## ✨ **FEAT (Funcionalidades)**
- feat(auth): implementa login com Google OAuth
- feat(api): adiciona rota de recuperação de senha
- feat(ui): cria componente de notificação toast
- feat(database): adiciona índice para consulta rápida
- feat(2fa): implementa autenticação de dois fatores
- feat(relatório): gera PDF com histórico de acessos
- feat(dashboard): adiciona gráfico de métricas em tempo real
- __________________________

## 💄 **STYLE (Formatação)**
- style(ui): padroniza espaçamento entre cards
- style(css): remove arquivos não utilizados
- style(login): centraliza formulário na tela
- style(código): aplica prettier em toda base
- style(cores): ajusta paleta para modo escuro
- __________________________

## ♻️ **REFACTOR (Refatoração)**
- refactor(auth): extrai lógica de validação para service
- refactor(api): padroniza nomes de rotas RESTful
- refactor(database): separa conexão em arquivo próprio
- refactor(2fa): simplifica verificação de código
- refactor(utils): cria helpers para funções repetidas
- __________________________

## 📚 **DOCS (Documentação)**
- docs(readme): atualiza instruções de instalação
- docs(api): adiciona exemplos de requisição no swagger
- docs(contributing): atualiza guia de contribuição
- docs(license): adiciona licença MIT
- docs(changelog): documenta versão 1.2.0
- __________________________

## 🧪 **TEST (Testes)**
- test(auth): adiciona testes para validação de email
- test(api): cobre rotas de usuário com 90% de cobertura
- test(2fa): testa códigos inválidos e expirados
- test(utils): adiciona testes unitários para helpers
- __________________________

## ⚡ **PERF (Performance)**
- perf(api): adiciona cache em consultas frequentes
- perf(banco): otimiza queries com índices
- perf(frontend): lazy loading em rotas pesadas
- perf(imagens): comprime assets não otimizados
- __________________________

## 🔧 **CHORE (Tarefas)**
- chore(deps): atualiza dependências de segurança
- chore(ci): configura pipeline de deploy automático
- chore(env): padroniza variáveis de ambiente
- chore(git): adiciona .gitignore para arquivos temporários
- __________________________

## 🚀 **DEPLOY**
- deploy(prod): sobe versão 1.2.0 para produção
- deploy(homolog): atualiza ambiente de testes
- deploy(rollback): reverte para versão estável 1.1.5
- __________________________

## 🔙 **REVERT**
- revert: desfaz alterações na rota de login (instabilidade)
- revert: volta versão do banco para 1.0.0
- __________________________

EOF
}


# ============================================
# MENU PRINCIPAL
# ============================================
while true; do
    echo ""
    echo "======================================"
    echo "   📋 ESCOLHA O TIPO DE COMMIT"
    echo "======================================"
    echo "1) 🐛 Fix (correção)"
    echo "2) ✨ Feat (funcionalidade)"
    echo "3) 💄 Style (formatação)"
    echo "4) ♻️ Refactor (refatoração)"
    echo "5) Lista de Commit | Para Usar !"
    echo "0) ❌ Sair"
    echo "======================================"
    read -p "Opção: " opcao
    
    case $opcao in
        1) clear; gerador_fix ;;
        2) clear; gerador_feat ;;
        3) clear; gerador_style ;;
        4) clear; gerador_refactor ;;
        5) clear; lista_mensagem_commit ;;
        0) echo "Até mais!"; exit 0 ;;
        *) echo "❌ Opção inválida"; sleep 1 ;;
    esac
    
    echo ""
    read -p "Enter pra continuar..."
    clear
done
```
