# 🧩 Integração Contínua (CI) e GitHub Actions

## 📌 O que é Integração Contínua (CI)?

A **Integração Contínua** (em inglês, *Continuous Integration* ou **CI**) é uma **prática de desenvolvimento de software** onde o código produzido pelos desenvolvedores é **integrado ao repositório principal com frequência** (várias vezes ao dia). Essa prática é amplamente utilizada no dia a dia das empresas — especialmente em times profissionais de desenvolvimento de software. Ela é considerada uma boa prática essencial e fundamental na rotina de desenvolvimento de software profissional, tanto em empresas grandes quanto em startups. Utilizá-la corretamente reduz erros, melhora a qualidade do código e aumenta a velocidade de entrega de novos recursos aos clientes.

Cada vez que o código é enviado (push), o projeto passa automaticamente por **verificações automáticas**, como:

- Execução de testes automatizados;
- Verificação de erros;
- Compilação do código;
- Geração de builds;
- Envio de alertas, se algo falhar.

---

## 🧠 Por que usar CI?

### Vantagens:

✅ Detecta erros rapidamente;  
✅ Automatiza tarefas repetitivas;  
✅ Garante mais segurança e qualidade;  
✅ Ajuda a manter o projeto funcionando a cada mudança.

### Exemplo prático:

Imagine uma equipe trabalhando em um site. Cada pessoa faz alterações diferentes. Sem CI, é possível que uma mudança de um colega **quebre o site inteiro**. Com CI, cada mudança é testada automaticamente e o problema é detectado **antes de chegar ao cliente**.

---

## ⚙️ GitHub Actions: Integração Contínua no GitHub

O **GitHub Actions** é a ferramenta de CI/CD do próprio GitHub. Ela permite criar **workflows automatizados** para executar tarefas sempre que algo acontece no repositório, como:

- Push de código;
- Criação de Pull Request;
- Criação de uma nova tag;
- Agendamento por data/hora (cron).

---

## ⚙️ O que dá para fazer com o GitHub Actions?

O **GitHub Actions** é a ferramenta de CI/CD do próprio GitHub. Ela permite criar **workflows automatizados** para executar tarefas sempre que algo acontece no repositório, como:

- Testes Automatizados: Executar testes toda vez que alguém faz um push, abre uma pull request, faz merge em uma branch.
- Builds Automáticos: Compilar, empacotar ou transformar seu código automaticamente.
- Deploy automático: Publicar seu site ou app automaticamente quando você faz push na branch main.
- Agendamento por data/hora (cron).

---

## 🏗️ Estrutura do GitHub Actions

Um workflow (fluxo de trabalho) do GitHub Actions é um arquivo `.yml` que fica no seguinte caminho:

```

.github/workflows/nome-do-arquivo.yml

````
O .yml ou .yaml é um arquivo de texto simples usado para organizar dados em formato hierárquico, de forma clara e legível.
YAML significa *YAML Ain't Markup Language* (YAML não é uma linguagem de marcação).
É muito utilizado para configurações de sistemas e automação
Esse arquivo define:

- **Quando o fluxo será executado** (gatilhos);
- **Em qual sistema** será executado (Linux, Windows ou macOS);
- **Quais passos serão seguidos** (ex: instalar dependências, rodar testes etc).

---

##✍️ Exemplo Completo e Comentado de CI com GitHub Actions##

```yaml
# Nome do workflow (aparece na aba "Actions" do GitHub)
name: CI - Testes Automatizados

# Gatilho: esse fluxo será executado quando ocorrer um push na branch "main"
on:
  push:
    branches: [ main ]

# Definindo os "jobs" (tarefas) que serão executadas
jobs:
  build:
    # Ambiente do servidor onde o CI será executado
    runs-on: ubuntu-latest

    # Etapas da tarefa
    steps:
      # Etapa 1: Baixar o código do repositório
      - name: Clonar código do repositório
        uses: actions/checkout@v3

      # Etapa 2: Instalar o Node.js na versão 16
      - name: Instalar Node.js
        uses: actions/setup-node@v3
        with:
          node-version: '16'

      # Etapa 3: Instalar dependências com npm
      - name: Instalar dependências
        run: npm install

      # Etapa 4: Executar testes com npm
      - name: Rodar testes
        run: npm test
````

---

## 🔍 Explicando Cada Parte

### `name:`

Nome que será exibido no painel de "Actions" do GitHub.

### `on:`

Define os **gatilhos** que ativam esse workflow. Exemplo:

* `push`: ao fazer um push
* `pull_request`: ao abrir um pull request
* `schedule`: em horário agendado
* `workflow_dispatch`: manual

### `jobs:`

Um **job** é uma tarefa que será executada.

### `runs-on:`

Define o sistema operacional que o GitHub vai usar para executar o código.

* `ubuntu-latest`: Linux Ubuntu
* `windows-latest`: Windows
* `macos-latest`: macOS

### `steps:`

Cada job tem vários **passos (steps)** que serão executados em sequência.

### `uses:`

Executa uma **ação pronta** do GitHub (como clonar o repositório ou configurar o Node).

### `run:`

Executa um **comando de terminal**, como se estivesse digitando no terminal do computador.

---



## ✅ Conclusão

* A **Integração Contínua (CI)** ajuda a manter o código funcionando corretamente a cada mudança.
* O **GitHub Actions** é uma ferramenta poderosa e gratuita para automatizar tarefas no seu repositório.
* Você pode configurar CI para **rodar testes, validar código, compilar, fazer deploy e muito mais**.
* Dominar CI é um passo importante para se tornar um desenvolvedor profissional.

---

## 🧑‍💻 Exercício Proposto

# Passo a passo: Criar repositório + site + CI para publicar no GitHub Pages

---

## 1. Criar um repositório no GitHub

1. Acesse [github.com](https://github.com) e faça login.
2. Clique no botão **New** (novo repositório).
3. Defina:

   * Nome do repositório: `meu-site-exemplo` (ou outro nome que quiser)
   * Visibilidade: Público (pode ser privado também, mas Pages funcionam melhor público)
4. Marque a opção para criar um README (opcional)
5. Clique em **Create repository**

---

## 2. Clonar o repositório no seu computador

No terminal, rode:

```bash
git clone https://github.com/<seu-usuario>/meu-site-exemplo.git
cd meu-site-exemplo
```

(Substitua `<seu-usuario>` pelo seu usuário do GitHub)

---

## 3. Criar os arquivos do site

Dentro da pasta do projeto, crie a pasta `docs`:

```bash
mkdir docs
```

Crie o arquivo `index.html` dentro da pasta `docs`:

`docs/index.html`:

```html
<!DOCTYPE html>
<html lang="pt-br">
<head>
  <meta charset="UTF-8" />
  <meta name="viewport" content="width=device-width, initial-scale=1" />
  <title>Meu Site Exemplo</title>
  <link rel="stylesheet" href="style.css" />
</head>
<body>
  <h1>Olá, mundo!</h1>
  <p>Este é um site publicado com GitHub Pages e GitHub Actions.</p>
</body>
</html>
```

Crie o arquivo `style.css` dentro da pasta `docs`:

`docs/style.css`:

```css
body {
  font-family: Arial, sans-serif;
  background-color: #f2f2f2;
  color: #333;
  padding: 2rem;
  text-align: center;
}

h1 {
  color: #0078d7;
}
```

---

## 4. Commitar e enviar para o GitHub

```bash
git add docs/index.html docs/style.css
git commit -m "Adiciona site estático na pasta docs"
git push origin main
```

---

## 5. Criar o workflow do GitHub Actions

Crie a pasta para workflows:

```bash
mkdir -p .github/workflows
```

Crie o arquivo `.github/workflows/deploy.yml` com o conteúdo:

```yml
name: Deploy GitHub Pages
# Nome do workflow, que aparece na aba "Actions" do GitHub.
# Aqui diz que é o fluxo para fazer o deploy (publicação) no GitHub Pages.

on:
  push:
    branches:
      - main
# Define o gatilho para rodar esse workflow:
# Sempre que houver um "push" (envio de código) na branch "main",
# o workflow será executado automaticamente.

jobs:
  deploy:
    runs-on: ubuntu-latest
    # Define o "job" chamado "deploy".
    # O job vai rodar em um ambiente virtual (runner) com sistema operacional Ubuntu na última versão disponível.

    steps:
    - name: Checkout do código
      uses: actions/checkout@v4
    # Primeiro passo: baixa o código do repositório para o ambiente do runner.
    # Isso permite que os comandos seguintes acessem o código atualizado enviado.

    - name: Publicar no GitHub Pages
      uses: peaceiris/actions-gh-pages@v4
      with:
        github_token: ${{ secrets.GITHUB_TOKEN }}
        publish_dir: ./docs
    # Segundo passo: usa uma ação pronta chamada "actions-gh-pages" para publicar os arquivos no GitHub Pages.
    # github_token é uma variável secreta automática que permite à ação fazer alterações no repositório (criar branch gh-pages).
    # publish_dir especifica qual pasta será publicada — no caso, a pasta "docs".

```

---

## 6. Commitar e enviar o workflow

```bash
git add .github/workflows/deploy.yml
git commit -m "Adiciona workflow para deploy no GitHub Pages"
git push origin main
```

---

## 7. Configurar o GitHub Pages no repositório

1. Vá no seu repositório no GitHub.
2. Clique em **Settings** (Configurações).
3. No menu lateral, clique em **Pages**.
4. Em **Source**, escolha:

   * Branch: `gh-pages`
   * Folder: `/ (root)`
5. Clique em **Save**.

---

## 8. Testar

* Aguarde alguns minutos após o push do workflow.
* Seu site estará disponível em:

```
https://<seu-usuario>.github.io/meu-site-exemplo/


---

## 📚 Referências

* [Guia Oficial GitHub Actions](https://docs.github.com/pt/actions)
* [O que é Integração Contínua](https://www.atlassian.com/br/continuous-delivery/continuous-integration)
* [HTMLHint](https://htmlhint.com/)

