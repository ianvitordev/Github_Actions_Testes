# 🚀 Workflow de Demonstração: Build Simples

Este projeto é um exemplo mínimo (Hello World) de um **GitHub Actions Workflow** que é executado automaticamente sempre que um novo código é enviado (evento push) ao repositório. O objetivo é demonstrar a estrutura básica do GitHub Actions e como sua automação é portável.

## 🎯 Objetivo do Workflow

O workflow é extremamente simples e tem dois propósitos principais:
- Fazer o checkout do código do repositório.
- Executar um comando simples de shell (`echo`) que imprime uma mensagem no log da ação.

## ⚙️ Estrutura do Workflow

O arquivo de configuração está localizado em:  
`.github/workflows/build-simples.yml`

```yaml
name: Build Simples
on: [push]
jobs:
  build:
    runs-on: ubuntu-latest
    steps:
      - uses: actions/checkout@v4
      - name: Hello World
        run: echo "O workflow foi executado!"
```

| Componente                | Descrição                                                                 |
|---------------------------|---------------------------------------------------------------------------|
| `name`                    | O nome do workflow que aparece na aba "Actions" do GitHub.                |
| `on: [push]`              | Define o evento que dispara o workflow: qualquer envio de código (push).   |
| `runs-on: ubuntu-latest`  | Especifica o Runner (máquina virtual) que executará o job.                |
| `actions/checkout@v4`     | Baixa o código do repositório atual no runner.                            |
| `run: echo ...`           | Executa um comando simples de shell, exibindo uma mensagem no log.        |

---

## 🛠️ Como Baixar, Reproduzir e Testar o Workflow

Para que o GitHub Actions seja executado com sucesso, você deve enviar o código (push) para um repositório que pertence à sua própria conta e onde você tem permissão de escrita.

Como alternativa ao Fork, você pode "importar" o código para um repositório novo na sua conta seguindo os passos abaixo:

### Passo 1: Clonar e Preparar a Pasta Local

Primeiro, baixe o código e apague o histórico Git do repositório original para começar um novo projeto.

```bash
git clone https://github.com/LUCASRENAA/Github_Actions_Example.git
cd Github_Actions_Example
rm -rf .git  # No Linux/macOS
# rmdir /s .git  # No Windows, pode ser necessário mostrar pastas ocultas
```

Inicie um novo repositório Git local a partir do zero:

```bash
git init
```

### Passo 2: Criar e Ligar ao Seu Repositório GitHub

1. Crie um novo repositório vazio na sua conta do GitHub (sem README, .gitignore ou licença).
2. Copie o link HTTPS ou SSH desse novo repositório.
3. Ligue o seu repositório local ao repositório remoto:

```bash
# Substitua [LINK_DO_SEU_NOVO_REPOSITORIO] pelo link que você copiou
git remote add origin [LINK_DO_SEU_NOVO_REPOSITORIO]
```

### Passo 3: Fazer o Primeiro Push e Disparar o Workflow

Faça uma alteração simples (por exemplo, adicione uma linha neste README para que o Git detecte algo para enviar).

```bash
git add .
git commit -m "Setup inicial do meu novo repositorio"
git push -u origin main  # Ou master, dependendo do GitHub
```

O comando `git push -u origin main` define o seu repositório remoto como o destino principal.

### Passo 4: Verificação da Execução

Após o `git push`, o GitHub Actions será disparado automaticamente no seu novo repositório:

1. Vá para o seu novo repositório no GitHub.
2. Clique na aba **Actions**.
3. Você verá a execução do workflow "Build Simples" iniciada pelo seu commit.
4. Clique no nome do commit para ver os detalhes e confirme que a etapa "Hello World" foi executada com sucesso!"# Github_Actions_Testes" 
