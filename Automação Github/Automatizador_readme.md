# 🚀 Automação – Gerador de README para GitHub

Este projeto é um **gerador automático de README.md**, pensado para facilitar a criação de documentações iniciais para projetos no GitHub.

A ideia é simples:  
👉 **rodar o script**  
👉 **copiar e colar o README gerado**  
👉 **ganhar tempo e manter padrão nos projetos**

---

## 🧠 Objetivo

- Automatizar a criação de README
- Evitar começar projetos com README vazio
- Padronizar documentação entre repositórios
- Ajudar iniciantes e agilizar o fluxo de devs mais experientes

---

## ⚙️ O que o script faz?

O script gera automaticamente:

- 📌 Título do projeto  
- 📄 Descrição  
- 🛠️ Tecnologias utilizadas  
- ▶️ Como executar o projeto  
- 📁 Estrutura básica de pastas  

Tudo pronto para **copiar e colar no GitHub**.

---

### 📚 Como Usar
- Crie uma pasta no seu computador.
- Dentro dela, crie um arquivo de texto comum.
- Cole o script completo fornecido no GitHub.
- Salve com a extensão:
- setup.sh
- Clique com botão direito → Executar com Git Bash
- Escolha as opções no menu e deixe a CLI trabalhar sozinha.

---

## Script:

```bash
#!/bin/bash

BASE_DIR="$(pwd)/Projeto Readme"
mkdir -p "$BASE_DIR"

# Funções para gerar READMEs
gerador_readme_projeto_simples(){
cat <<EOF > "$BASE_DIR/Readme.md"
# Projeto Nome : [Insira Aqui]
Esse projeto foi desenvolvido para ser um sistema ou ferramenta.
## Por que o sistema foi desenvolvido?
Este sistema foi desenvolvido para ajudar pequenas equipes a gerenciar tarefas sem depender de planilhas complexas ou softwares pagos.
## Tecnologias Usadas:
- [Ex: Node.js, HTML, CSS]
## Bibliotecas Usadas:
- [Ex: Axios, Lodash]
## Nome Equipe : [Insira Aqui]
- [Coloque o nome do time ou dos desenvolvedores]
## Como rodar o projeto
- [Instruções]
## Como contribuir
- [Instruções]
## Contato
- [Email/GitHub]
EOF
}

gerador_readme_projeto_ts(){
cat <<EOF > "$BASE_DIR/Readme.md"
# Projeto Nome : [Insira Aqui]
Esse projeto foi desenvolvido para ser um sistema ou ferramenta.
## Por que o sistema foi desenvolvido?
Este sistema foi desenvolvido para ajudar pequenas equipes a gerenciar tarefas sem depender de planilhas complexas ou softwares pagos.
## Tecnologias Usadas:
- Backend TypeScript com libs
- SQL
## Bibliotecas Usadas:
- [Ex: Express, TypeORM]
## Nome Equipe : [Insira Aqui]
- [Coloque o nome do time ou dos desenvolvedores]
## Como rodar o projeto
- [Instruções]
## Como contribuir
- [Instruções]
## Contato
- [Email/GitHub]
EOF
}

gerador_readme_projeto_js(){
cat <<EOF > "$BASE_DIR/Readme.md"
# Projeto Nome : [Insira Aqui]
Esse projeto foi desenvolvido para ser um sistema ou ferramenta.
## Por que o sistema foi desenvolvido?
Este sistema foi desenvolvido para ajudar pequenas equipes a gerenciar tarefas sem depender de planilhas complexas ou softwares pagos.
## Tecnologias Usadas:
- Backend JavaScript com libs
- SQL
## Bibliotecas Usadas:
- [Ex: Express, Axios]
## Nome Equipe : [Insira Aqui]
- [Coloque o nome do time ou dos desenvolvedores]
## Como rodar o projeto
- [Instruções]
## Como contribuir
- [Instruções]
## Contato
- [Email/GitHub]
EOF
}

gerador_readme_projeto_cs(){
cat <<EOF > "$BASE_DIR/Readme.md"
# Projeto Nome : [Insira Aqui]
Esse projeto foi desenvolvido para ser um sistema ou ferramenta.
## Por que o sistema foi desenvolvido?
Este sistema foi desenvolvido para ajudar pequenas equipes a gerenciar tarefas sem depender de planilhas complexas ou softwares pagos.
## Tecnologias Usadas:
- Backend C# com libs
- SQL
## Bibliotecas Usadas:
- [Ex: Entity Framework]
## Nome Equipe : [Insira Aqui]
- [Coloque o nome do time ou dos desenvolvedores]
## Como rodar o projeto
- [Instruções]
## Como contribuir
- [Instruções]
## Contato
- [Email/GitHub]
EOF
}

gerador_readme_projeto_java(){
cat <<EOF > "$BASE_DIR/Readme.md"
# Projeto Nome : [Insira Aqui]
Esse projeto foi desenvolvido para ser um sistema ou ferramenta.
## Por que o sistema foi desenvolvido?
Este sistema foi desenvolvido para ajudar pequenas equipes a gerenciar tarefas sem depender de planilhas complexas ou softwares pagos.
## Tecnologias Usadas:
- Backend Java com libs
- SQL
## Bibliotecas Usadas:
- [Ex: Hibernate, Spring]
## Nome Equipe : [Insira Aqui]
- [Coloque o nome do time ou dos desenvolvedores]
## Como rodar o projeto
- [Instruções]
## Como contribuir
- [Instruções]
## Contato
- [Email/GitHub]
EOF
}

# Menu interativo
echo "=============================="
echo " Gerador de README para projetos"
echo "=============================="
echo "Escolha o tipo de projeto:"
echo "1) Simples"
echo "2) TypeScript"
echo "3) JavaScript"
echo "4) C#"
echo "5) Java"
read -p "Digite a opção (1-5): " OPCAO

case $OPCAO in
  1) gerador_readme_projeto_simples ;;
  2) gerador_readme_projeto_ts ;;
  3) gerador_readme_projeto_js ;;
  4) gerador_readme_projeto_cs ;;
  5) gerador_readme_projeto_java ;;
  *) echo "Opção inválida! Saindo..." ; exit 1 ;;
esac

echo "README gerado em $BASE_DIR/Readme.md ✅"
```



## 🛠️ Tecnologias Utilizadas

- Bash / Shell Script 

