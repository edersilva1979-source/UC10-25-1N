### 📄 Trabalho 01 - Git / GitHub



## 🎯 Objetivo: Avaliar o Conhecimeto adquirido até agora

> Criar Reposistórios Local e Online, fazer uma aplicação com versionamento e documentação.


## 🧠 Dicas importantes

* Sempre **comece uma feature** a partir da branch `develop`
* Nunca edite diretamente `main` ou `develop`
* Sempre **teste** bem antes de fazer `merge` com `main`
* Use `pull` para manter seu código atualizado antes de começar algo novo

---

**Iniciando o Trabalho - Hora de por a mão na massa**

---

## 🧪 Exercício: Trabalhando com Gitflow em um Projeto Web

### 🎯 Objetivo

Utilizando o **Gitflow** em um projeto real.

* Criar um repositório local.
* Subir o repositório para o GitHub.
* Iniciar o fluxo Gitflow com `develop`, `feature`, `release` e `main`.
* Simular etapas do desenvolvimento de uma aplicação simples.

---


### 🚀 Etapas do Exercício

#### 1. 📁 Criação do Projeto

1. Abra o terminal e crie uma pasta para o projeto:

```
 trabalho01
 ```

2. Crie um arquivo inicial `index.html` com o conteúdo abaixo:

```html

  <title>Trabalho 01 - UC10 - Git&GitHub</title>

  <h1>Bem-vindo ao Projeto Git!</h1>

```

3. Inicialize um repositório Git:



4. Faça o primeiro commit na branch `main`:



#### 2. ☁️ Criar o Repositório no GitHub

1. Acesse (https://github.com) e crie um novo repositório **sem README** com o nome `trabalho01-git`.

2. Conecte o repositório local ao GitHub:


#### 3. 🌱 Iniciando o Gitflow Manualmente

1. Crie a branch `develop` a partir da `main`:



#### 4. 🧩 Criando uma `feature`


1. Crie uma nova branch de feature: feature/botao-sobremim


2. Edite o `index.html` e adicione o botão:



3. Faça o commit da feature:


4. Faça o push da branch:


5. Abra um **Pull Request** da feature no GitHub, apontando para a `develop`.

6. Faça o **merge** no GitHub.

7. No terminal, atualize sua branch local `develop`:



#### 5. 📦 Criando uma `release`

1. Crie uma nova branch de release: release/v1.0.0

2. Altere o título da página no `index.html` para:  
   Trabalho01 Git v1.0.0

3. Commit e push:


4. Crie o **Pull Request** da `release/v1.0.0` para a `main` no GitHub e faça o merge.

5. Em seguida, faça o **merge da release na develop** também.

6. No terminal atualize a main e o develop:


#### 6. 🐞 Criando uma `hotfix`


1. Crie uma branch de hotfix a partir da main:

 hotfix/corrige-botao

2. Corrija o botão no `index.html`:
  ``+ Sobre Mim``

3. Commit e push:


4. Faça o Pull Request para `main` e depois para `develop`.


### 💡 Dica para 


| Pergunta                                  | Resposta                                       |
| ----------------------------------------- | ---------------------------------------------- |
| Posso editar direto na `main`?            | ❌ Não, use branches específicas               |
| Posso ter várias features ao mesmo tempo? | ✅ Sim, desde que cada uma tenha sua branch    |
| Quando deletar uma branch?                | Após o merge (para manter o repositório limpo)  |



