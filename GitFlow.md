### 📄 `GitFlow`

## 🧠 O que é o Git Flow?

O **Git Flow** é uma estratégia de trabalho com Git que organiza o desenvolvimento de software em diferentes **"fluxos" ou ramificações (branches)**, cada uma com uma finalidade específica.

Criado por **Vincent Driessen**, o Git Flow ajuda equipes a manter o projeto organizado, com versões de desenvolvimento, lançamento, correções e funcionalidades separadas.

---

## 🎯 Objetivo do Git Flow

> Separar de forma clara as diferentes etapas do desenvolvimento de um software.

Com o Git Flow, você tem:
- Um lugar para desenvolver novas funcionalidades ✅
- Um lugar para testar e preparar o código ✅
- Um lugar só com código pronto para ir para produção ✅
- Um lugar para corrigir erros críticos rapidamente ✅

---

## 🔁 Estrutura de Branches no Git Flow

### 1. `main`
- Contém o **código em produção**. O código em produção é onde o sistema está funcionando de verdade para os usuários finais. Quando você ainda está criando ou testando o app ou uma parte dele, esta parte está em **ambiente de desenvolvimento**. Quando já está pronta e publicada, está em **ambiente de produção**.
- **Nunca** desenvolva diretamente nela
- Toda versão lançada para os clientes, ou seja, já pronta, do sistema (ex: v1.0, v2.0) está aqui

### 2. `develop`
- Aqui acontece o **desenvolvimento ativo**. Aqui o código está sendo produzido, ou seja, é onde os programadores estão **mexendo agora** no código. É onde as novas ideias estão sendo implementadas.
- Novas funcionalidades são integradas nela
- Depois de testado, o código da `develop` vai para a `main`

---

## 🌱 Branches auxiliares do Git Flow

### 📌 `feature/*`
- Onde se desenvolvem **novas funcionalidades**. Cada nova funcionalidade (feature) que você vai programar, você cria uma branch separada, que começa com feature/.
Imagine que você está criando um sistema de cadastro de clientes. O projeto terá as seguintes funcionalidades:

  - Cadastro de usuário
  - Tela de login
  - Lista de produtos
  - Carrinho de compras

🔧 No Git Flow, cada uma dessas funcionalidades vai ter sua própria branch, como:

  - feature/cadastro-usuario
  - feature/login
  - feature/lista-produtos
  - feature/carrinho

Porque assim você:

✅ Trabalha de forma organizada, cada funcionalidade em um "espaço separado"
✅ Evita misturar códigos diferentes no mesmo lugar
✅ Pode testar e revisar uma funcionalidade por vez
✅ Facilita o trabalho em equipe — cada pessoa pode trabalhar numa feature diferente sem conflitos

**Criada a partir de:** `develop`  
**Destino final (merge):** `develop`


Sim! E você trouxe uma dúvida muito importante — porque esse é um dos pontos mais valiosos e organizados do Git Flow.

Vamos explicar **detalhadamente e de forma didática**:

---

## 🌱 O que são as branches `feature/*` no Git Flow?

### 💡 Resumo simples:

> **Cada nova funcionalidade (feature)** que você vai programar, você cria uma **branch separada**, que começa com `feature/`.

---

### 📌 Exemplo prático:

Você está criando um sistema de cadastro de clientes.
O projeto terá as seguintes funcionalidades:

* Cadastro de usuário
* Tela de login
* Lista de produtos
* Carrinho de compras

🔧 No Git Flow, **cada uma dessas funcionalidades vai ter sua própria branch**, como:

* `feature/cadastro-usuario`
* `feature/login`
* `feature/lista-produtos`
* `feature/carrinho`

---

### 🧱 Por que fazer isso?

Porque assim você:

✅ Trabalha **de forma organizada**, cada funcionalidade em um "espaço separado"
✅ Evita **misturar códigos diferentes** no mesmo lugar
✅ Pode **testar e revisar** uma funcionalidade por vez
✅ Facilita o trabalho em equipe — cada pessoa pode trabalhar numa feature diferente sem conflitos

---

### 📤 Como funciona na prática?

#### Passo a passo para criar uma nova funcionalidade no Git Flow:

1. Estar na branch `develop`:

   ```bash
   git checkout develop
   ```

2. Criar a branch da feature:

   ```bash
   git checkout -b feature/nome-da-feature
   ```

3. Trabalhar na feature normalmente:

   * Criar arquivos
   * Programar a lógica
   * Fazer commits

4. Quando a feature (funcionalidade) estiver pronta:

   * Volta para a `develop`:

     ```bash
     git checkout develop
     ```

   * Junta a branch da feature com a `develop`:

     ```bash
     git merge feature/nome-da-feature
     ```

5. Depois disso, pode excluir a branch da feature, se quiser.

---

### 🔁 Fluxo completo visual:

```plaintext
develop
   ├───> feature/cadastro-usuario
   ├───> feature/tela-login
   ├───> feature/busca-produtos
```

Cada uma dessas branches é criada **a partir de `develop`**
E depois de pronta, ela volta para `develop`.

---

### 🚨 Dica importante:

> **Nunca crie uma feature a partir da `main`!**
> A `main` é para código já testado e em produção.
> Sempre crie a branch de feature **a partir da `develop`**.


---

### 📌 `release/*`
- Preparação para um **novo lançamento**. A branch release/* serve para preparar uma nova versão do sistema que será lançada oficialmente (ou seja, que vai ainda para produção).
- Serve para ajustes finais, testes, pequenos bugs

**Criada a partir de:** `develop`  
**Destino final (merge):** `main` e `develop`

Excelente! Essa parte do Git Flow é muito importante para que os alunos entendam **como e quando preparar o sistema para ser lançado oficialmente**, com segurança e organização.

Aqui vai uma **explicação detalhada, didática e com exemplos**, sobre as branches `release/*`.

---

## 🚀 O que é a branch `release/*` no Git Flow?

### 💡 Resumo simples:

> A branch `release/*` serve para **preparar uma nova versão** do sistema que será **lançada oficialmente** (ou seja, que vai para produção).

---

### 📦 Por que ela existe?

Porque antes de lançar uma nova versão do sistema, você pode precisar:

* Ajustar textos ou ícones
* Corrigir pequenos bugs
* Fazer testes finais
* Atualizar arquivos como `README.md` ou `versão`

E tudo isso deve ser feito **sem interromper o desenvolvimento contínuo** na `develop`.

---

### 👇 Exemplo prático:

Você está desenvolvendo um site e, na `develop`, já terminou estas funcionalidades:

* Cadastro de clientes
* Lista de produtos
* Tela de login

Agora, **essas funcionalidades estão prontas para serem lançadas na produção**.

🔧 Você então cria uma branch `release/1.0.0`.

Nela, você:

* Faz ajustes finais
* Testa o sistema com mais calma
* Resolve pequenos detalhes

---

### 📤 Depois dos testes?

Quando tudo está **100% pronto para o lançamento**, você:

1. Faz o `merge` da branch `release/1.0.0` na `main`
   ✅ Isso envia o sistema para **produção** (versão oficial do sistema).

2. Também faz `merge` na `develop`
   ✅ Porque talvez a branch `release` tenha recebido **correções** ou ajustes finais que a `develop` ainda não tem.

---

### 🛠️ Passo a passo:

```bash
# Estar na branch develop
git checkout develop

# Criar a branch de release
git checkout -b release/1.0.0

# Fazer ajustes e testes finais
# Commitar mudanças...

# Voltar para main e fazer o merge (lançamento oficial)
git checkout main
git merge release/1.0.0

# Criar uma tag (opcional, para marcar a versão)
git tag -a v1.0.0 -m "Lançamento da versão 1.0.0"

# Voltar para develop e fazer o merge também
git checkout develop
git merge release/1.0.0

# (Opcional) Apagar a branch de release
git branch -d release/1.0.0
```

---

### 🔁 Fluxo visual:

```plaintext
develop
   ├───> release/1.0.0 (ajustes finais)
                 ├───> merge → main   (vai para produção)
                 └───> merge → develop (leva os ajustes de volta ao dev)
```

---

### 🧠 Por que fazer merge também na `develop`?

Imagine que na `release/1.0.0` você corrigiu um erro de ortografia no botão "Cadastrar"
Se não fizer `merge` de volta para a `develop`, esse erro pode voltar no futuro.

---

### ✅ Conclusão

| Termo              | Significado                                                   |
| ------------------ | ------------------------------------------------------------- |
| `release/*`        | Fase final antes do lançamento                                |
| Criada a partir de | `develop`                                                     |
| Merge final        | `main` e `develop`                                            |
| Usada para         | Testes finais, ajustes pequenos, preparação da versão oficial |


---

### 📌 `hotfix/*`
- Correções URGENTES de bugs encontrados em produção. A branch `hotfix/*` é usada para **corrigir erros graves (bugs)** que foram descobertos **depois que o sistema já foi lançado**, ou seja, **já está em produção (na `main`)**.

**Criada a partir de:** `main`  
**Destino final (merge):** `main` e `develop`

### 🧯 Quando usar?

Imagine que o site da sua empresa está no ar e funcionando para os usuários.
De repente, alguém descobre um **erro crítico**:

* Um botão que não funciona
* Um cálculo que dá resultado errado
* Um erro que impede o login

🚨 **Esse tipo de problema precisa ser corrigido imediatamente**.

Você **não pode esperar** que a equipe termine novas funcionalidades na `develop`, nem abrir uma release.

---

### 🚑 Solução: `hotfix`

Você cria uma branch chamada:

```bash
hotfix/erro-login
```

Ou:

```bash
hotfix/1.0.1
```

Essa branch **vem diretamente da `main`**, corrige o problema, e depois:

* Faz `merge` para a `main` (para resolver o problema na produção)
* Faz `merge` para a `develop` (para que o código corrigido também vá para o desenvolvimento)

---

### 📤 Passo a passo completo:

```bash
# Estar na main (o erro está no código em produção)
git checkout main

# Criar a branch do hotfix
git checkout -b hotfix/1.0.1

# Corrigir o erro
# Fazer commit da correção

# Voltar para main e fazer merge (lança a correção)
git checkout main
git merge hotfix/1.0.1

# Criar uma tag de versão corrigida (opcional)
git tag -a v1.0.1 -m "Correção urgente de bug"

# Voltar para develop e fazer merge também (para manter tudo atualizado)
git checkout develop
git merge hotfix/1.0.1

# (Opcional) Apagar a branch hotfix
git branch -d hotfix/1.0.1
```

---

### 🔁 Fluxo visual:

```plaintext
main
  ├───> hotfix/1.0.1 (corrigir bug urgente)
               ├───> merge → main   ✅ (correção já em produção)
               └───> merge → develop ✅ (para manter a base atualizada)
```

---

### 🧠 Por que fazer merge também na `develop`?

Porque:

* A `develop` é a base do futuro do sistema.
* Se você **corrigiu um bug na `main` mas esqueceu de corrigir na `develop`**, o erro pode voltar na próxima versão.

---

### ✅ Conclusão

| Termo              | Significado                                                                |
| ------------------ | -------------------------------------------------------------------------- |
| `hotfix/*`         | Correções de **urgência** feitas diretamente na produção                   |
| Criada a partir de | `main`                                                                     |
| Merge final        | `main` (para corrigir) e `develop` (para manter atualizado)                |
| Quando usar?       | Quando um erro grave **já foi lançado** e precisa de correção **imediata** |


---

## 🛠️ Como usar Git Flow na prática

Você pode usar o Git Flow manualmente ou com uma ferramenta.

### 📦 Instalação (opcional, para automatizar)
```bash
git flow init
````

Você será perguntado a nomear as branches:

* Nome da branch principal: `main`
* Nome da branch de desenvolvimento: `develop`
* Prefixo das outras: `feature/`, `release/`, `hotfix/`, `support/`

---

## 📘 Exemplo passo a passo: Criando uma funcionalidade

### 🧩 Etapa 1: Criar uma branch de funcionalidade

```bash
git checkout develop
git checkout -b feature/login-usuario
```

➡️ Cria a branch `feature/login-usuario` a partir da `develop`.

### 💻 Etapa 2: Trabalhar no código

* Adicione, edite e faça commits normalmente:

```bash
git add .
git commit -m "Adiciona tela de login"
```

### 🔁 Etapa 3: Finalizar a funcionalidade (merge)

```bash
git checkout develop
git merge feature/login-usuario
git branch -d feature/login-usuario
```

---

## 🎉 Criando uma versão para lançamento (release)

### 🚧 Etapa 1: Criar branch de release

```bash
git checkout develop
git checkout -b release/v1.0
```

### 🛠 Etapa 2: Ajustes e testes finais

```bash
git add .
git commit -m "Ajustes finais para v1.0"
```

### 🚀 Etapa 3: Finalizar a release

```bash
git checkout main
git merge release/v1.0
git tag -a v1.0 -m "Versão 1.0 lançada"

git checkout develop
git merge release/v1.0

git branch -d release/v1.0
```

---

## 🧯 Corrigindo um bug urgente com hotfix

### ⚠️ Etapa 1: Criar a branch de hotfix

```bash
git checkout main
git checkout -b hotfix/bug-login
```

### 🔧 Etapa 2: Corrigir o erro

```bash
git add .
git commit -m "Corrige bug de login em produção"
```

### ✅ Etapa 3: Finalizar o hotfix

```bash
git checkout main
git merge hotfix/bug-login
git tag -a v1.0.1 -m "Correção de bug de login"

git checkout develop
git merge hotfix/bug-login

git branch -d hotfix/bug-login
```

---

## 📌 Resumo visual do fluxo

```
main  -----------●------------●--------→ (v1.0, v1.1)
                 \           /
develop ----------●---------●---------→
                   \       / \
                      feature/  release/ 
                       login     v1.0

hotfixes ←─── corrigem a main e a develop simultaneamente
```

---

## 🧠 Dicas importantes

* Sempre **comece uma feature** a partir da branch `develop`
* Nunca edite diretamente `main` ou `develop`
* Sempre **teste** bem antes de fazer `merge` com `main`
* Use `pull` para manter seu código atualizado antes de começar algo novo

---

## ✅ Vantagens do Git Flow

* Organização clara das etapas de desenvolvimento
* Melhor controle de versões e lançamentos
* Isolamento de código para novas funcionalidades
* Correções rápidas sem afetar o desenvolvimento

---

## 🤔 Quando usar Git Flow?

✅ Projetos com múltiplos desenvolvedores
✅ Projetos com versões bem definidas (v1.0, v2.0 etc.)
❌ Não recomendado para projetos muito pequenos ou com entrega contínua rápida

---

**Hora de por a mão na massa**

---

## 🧪 Exercício: Trabalhando com Gitflow em um Projeto Web

### 🎯 Objetivo

Ensinar como utilizar o **Gitflow** em um projeto real. Os alunos vão:

* Criar um repositório local.
* Subir o repositório para o GitHub.
* Iniciar o fluxo Gitflow com `develop`, `feature`, `release` e `main`.
* Simular etapas do desenvolvimento de uma aplicação simples.

---

### 📦 Pré-requisitos

* Git instalado.
* Conta no GitHub.
* Visual Studio Code ou outro editor.
* Terminal Git Bash ou nativo do SO.

---

### 🚀 Etapas do Exercício

#### 1. 📁 Criação do Projeto

1. Abra o terminal e crie uma pasta para o projeto:

```bash
mkdir projeto-gitflow
cd projeto-gitflow
```

2. Crie um arquivo inicial `index.html` com o conteúdo abaixo:

```html
<!DOCTYPE html>
<html lang="pt-br">
<head>
  <meta charset="UTF-8" />
  <title>Meu Projeto Gitflow</title>
</head>
<body>
  <h1>Bem-vindo ao Projeto com Gitflow!</h1>
</body>
</html>
```

3. Inicialize um repositório Git:

```bash
git init
```

4. Faça o primeiro commit na branch `main`:

```bash
git add .
git commit -m "chore: commit inicial com index.html"
```

---

#### 2. ☁️ Criar o Repositório no GitHub

1. Acesse (https://github.com) e crie um novo repositório **sem README** com o nome `projeto-gitflow`.

2. Conecte o repositório local ao GitHub:

```bash
git remote add origin https://github.com/SEU_USUARIO/projeto-gitflow.git
```

3. Suba o código:

```bash
git branch -M main
git push -u origin main
```

---

#### 3. 🌱 Iniciando o Gitflow Manualmente

1. Crie a branch `develop` a partir da `main`:

```bash
git checkout -b develop
git push -u origin develop
```

---

#### 4. 🧩 Criando uma `feature`

Vamos adicionar um botão ao site:

1. Crie uma nova branch de feature:

```bash
git checkout -b feature/botao-contato
```

2. Edite o `index.html` e adicione:

```html
<button>Contato</button>
```

3. Faça o commit da feature:

```bash
git add .
git commit -m "feat: adiciona botão de contato"
```

4. Faça o push da branch:

```bash
git push -u origin feature/botao-contato
```

5. Abra um **Pull Request** da feature no GitHub, apontando para a `develop`.

6. Faça o **merge** no GitHub.

7. No terminal, atualize sua branch local `develop`:

```bash
git checkout develop
git pull origin develop
```

---

#### 5. 📦 Criando uma `release`

1. Crie uma nova branch de release:

```bash
git checkout -b release/v1.0.0
```

2. Altere o título da página no `index.html` para:

```html
<title>Projeto Gitflow v1.0.0</title>
```

3. Commit e push:

```bash
git add .
git commit -m "chore: prepara versão 1.0.0"
git push -u origin release/v1.0.0
```

4. Crie o **Pull Request** da `release/v1.0.0` para a `main` no GitHub e faça o merge.

5. Em seguida, faça o **merge da release na develop** também.

6. No terminal:

```bash
git checkout main
git pull origin main

git checkout develop
git pull origin develop
```

---

#### 6. 🐞 Criando uma `hotfix`

Imagine que o botão está com um erro de digitação.

1. Crie uma branch de hotfix a partir da main:

```bash
git checkout main
git checkout -b hotfix/corrige-botao
```

2. Corrija o botão no `index.html` (por exemplo, corrigir o texto para "Fale Conosco").

3. Commit e push:

```bash
git add .
git commit -m "fix: corrige texto do botão de contato"
git push -u origin hotfix/corrige-botao
```

4. Faça o Pull Request para `main` e depois para `develop`.



### 💡 Dica para 

> Você pode instalar a extensão **Git Graph** ou **GitLens** no VS Code para visualizar os branches e commits de forma mais intuitiva.

---

## 🙋 Dúvidas Comuns

| Pergunta                                  | Resposta                                       |
| ----------------------------------------- | ---------------------------------------------- |
| Posso editar direto na `main`?            | ❌ Não, use branches específicas               |
| Posso ter várias features ao mesmo tempo? | ✅ Sim, desde que cada uma tenha sua branch    |
| Quando deletar uma branch?                | Após o merge (para manter o repositório limpo)  |

---

## 📚 Referência

* Criador do Git Flow: [nvie.com](https://nvie.com/posts/a-successful-git-branching-model/)
* Ferramenta Git Flow: `git flow init`

---



