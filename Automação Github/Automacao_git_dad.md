# Automação | Git DAD:

> **O pai dos devs preguiçosos!** 👨‍👦  
> Automatize suas tarefas Git com um script simples e eficiente.

## 📋 Sobre o Projeto

O **GIT DAD** nasceu da preguiça sagrada de um desenvolvedor que cansou de digitar os mesmos comandos Git toda santa vez. Por que fazer na mão se dá pra automatizar? 🤔

Com ele você:
- ✅ Clona repositórios sem sair do terminal
- ✅ Cria múltiplas branches de uma só vez
- ✅ Visualiza status e logs rapidamente
- ✅ Troca de branches sem decorar nomes
- ✅ Faz commit + pull + push com uma mensagem personalizada
- ✅ E muito mais!

---

## 🛠️ Funcionalidades

| # | Comando | Descrição |
|---|---------|-----------|
| 1 | 📥 Clonar | Clona qualquer repositório direto no Desktop |
| 2 | 🌿 Criar branches | Cria várias branches de uma vez (só digitar os nomes) |
| 3 | 📊 Status | Mostra o status atual do repositório |
| 4 | 📝 Logs | Exibe os últimos 10 commits de forma resumida |
| 5 | 🔄 Trocar branch | Lista as branches e troca com segurança |
| 6 | 🏗️  Criar repo | Cria repositório do zero com README e commit inicial |
| 7 | 🚀 Send all | Commit + Pull + Push (modo preguiçoso total) |
| 0 | ❌ Sair | Sai do programa |

---

### 1️⃣ Crie um arquivo de texto

### 2️⃣ Cole o código abaixo.

### 3️⃣ Salve como:

gerar_docs.sh

### Rode com git

### Siga O menu

<img width="556" height="341" alt="image" src="https://github.com/user-attachments/assets/f23a7c0c-1154-4b0f-a851-664f96a474c6" />

---

```bash
#!/bin/bash

# Cores (opcional)
RED='\033[0;31m'
GREEN='\033[0;32m'
NC='\033[0m'

# Banner
echo "╔════════════════════════════════════════════════════════════╗"
echo "║         🚀 GIT DAD | PRO DEV PREGUIÇOSO 🚀                ║"
echo "║              CRIADO POR UM DEV com Preguiça!               ║"
echo "╚════════════════════════════════════════════════════════════╝"


# Função 1: Clonar repositório
clonar_repo(){
    echo "📥 Informe o link do repositório para clonar:"
    read repo_link
    
    cd ~/Desktop/ || { echo "❌ Desktop não encontrado"; return 1; }
    
    git clone $repo_link || { echo "❌ Falha no clone"; return 1; }
    
    # Entra na pasta clonada
    repo_name=$(basename $repo_link .git)
    cd $repo_name
    
    echo "✅ Repositório clonado com sucesso!"
}

# Função 2: Criar branches
create_branch(){
    # Verifica se tá num repo
    if [ ! -d ".git" ]; then
        echo "❌ Não está num repositório Git!"
        return 1
    fi
    
    echo "🌿 Digite os nomes das branches (separados por espaço):"
    read -a branches
    
    for branch in "${branches[@]}"; do
        echo "Criando: $branch"
        git checkout -b $branch 2>/dev/null || echo "⚠️ Branch $branch já existe"
    done
    
    echo "✅ Branches criadas:"
    git branch
}

# Função 3: Verificar status
verify_git(){
    if [ ! -d ".git" ]; then
        echo "❌ Não está num repositório Git!"
        return 1
    fi
    
    echo "📊 Status do repositório:"
    git status
}

# Função 4: Ver logs
log_git(){
    if [ ! -d ".git" ]; then
        echo "❌ Não está num repositório Git!"
        return 1
    fi
    
    echo "📝 Últimos commits:"
    git log --oneline -10
}

# Função 5: Trocar de branch
switch_branch(){
    if [ ! -d ".git" ]; then
        echo "❌ Não está num repositório Git!"
        return 1
    fi
    
    echo "📌 Branches disponíveis:"
    git branch
    
    echo "🔄 Digite o nome da branch para trocar:"
    read target_branch
    
    git switch $target_branch 2>/dev/null || git checkout $target_branch
    
    echo "✅ Agora você está em: $(git branch --show-current)"
}

# Função 6: Criar repositório do zero
create_repo(){
    echo "🏗️  Nome do novo projeto:"
    read project_name
    
    mkdir -p ~/Desktop/$project_name
    cd ~/Desktop/$project_name
    
    git init
    echo "# $project_name" > README.md
    git add .
    git commit -m "chore: inicializa projeto"
    
    echo "✅ Repositório criado em: $(pwd)"
}

send_all(){
    # Verifica se tá no repo
    if [ ! -d ".git" ]; then
        echo "❌ Não está num repositório Git!"
        return 1
    fi
    
    # Mostra o que vai ser commitado
    echo "📂 Arquivos modificados:"
    git status -s
    
    echo "📝 Mensagem do commit:"
    read commit_msg
    
    git add .
    git commit -m "$commit_msg"
    git pull origin $(git branch --show-current)
    git push origin $(git branch --show-current)
}

# Menu principal
menu(){
    while true; do
        echo ""
        echo "════════════════════════════════════════════════════"
        echo "🚀 MENU PRINCIPAL"
        echo "════════════════════════════════════════════════════"
        echo "1) 📥 Clonar repositório"
        echo "2) 🌿 Criar branches"
        echo "3) 📊 Verificar status"
        echo "4) 📝 Ver logs"
        echo "5) 🔄 Trocar de branch"
        echo "6) 🏗️ Criar repositório do zero"
        echo "7) 📨 Enviar Tudo pro servidor"
        echo "0) ❌ Sair"
        echo "════════════════════════════════════════════════════"
        echo "Escolha uma opção:"
        read opcao
        
        case $opcao in
            1) clonar_repo ;;
            2) create_branch ;;
            3) verify_git ;;
            4) log_git ;;
            5) switch_branch ;;
            6) create_repo ;;
            7) send_all ;;
            0) echo "👋 Até mais!"; exit 0 ;;
            *) echo "❌ Opção inválida!" ;;
        esac
        
        echo ""
        echo "Pressione Enter para continuar..."
        read
    done
}

# Chama o menu
menu
````
