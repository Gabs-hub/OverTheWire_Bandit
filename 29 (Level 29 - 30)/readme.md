# Nível 29 - 30 (OverTheWire: Bandit)

### 📌 Descrição do Desafio

There is a git repository at ssh://bandit29-git@bandit.labs.overthewire.org/home/bandit29-git/repo via the port 2220. The password for the user bandit29-git is the same as for the user bandit29.

---

### 🎯 Objetivo

Devemos fazer um `git clone` via `ssh` e pegar a senha do próximo nível.

---

### 🔍 Passo a Passo da Lógica

* Clonei o repositório:

```
git clone ssh://bandit29-git@bandit.labs.overthewire.org:2220/home/bandit29-git/repo
```

* Dentro do repositório, novamente tem um arquivo README, dentro dele tem:

```
# Bandit Notes
Some notes for bandit30 of bandit.

## credentials

- username: bandit30
- password: <no passwords in production!>
```

* Novamente, sem senha no arquivo, então qual a mágica dessa vez? Veja o log:

```less
commit b879c94bd4641ebb8b5470258b3a41debb25f7c2 (HEAD -> master, origin/master, origin/HEAD)
Author: Ben Dover <noone@overthewire.org>
Date:   Tue Oct 14 09:26:20 2025 +0000

    fix username

commit eb435001e0eb0219ee071219d1f16f1cd3941a3b (origin/dev)
Author: Morla Porla <morla@overthewire.org>
Date:   Tue Oct 14 09:26:20 2025 +0000

    add data needed for development

commit cb9aac552efdc646bdf4b0c5218c5b528cb47f2d (origin/sploits-dev)
Author: Morla Porla <morla@overthewire.org>
Date:   Tue Oct 14 09:26:20 2025 +0000

    add some silly exploit, just for shit and giggles

commit 358fb1e671f460043ff5bd372e8d87e228dc148d
Author: Ben Dover <noone@overthewire.org>
Date:   Tue Oct 14 09:26:20 2025 +0000

    initial commit of README.md

commit fac6c810c23f28a475c767df31ae4980252bdd5d
Author: Ben Dover <noone@overthewire.org>
Date:   Tue Oct 14 09:26:20 2025 +0000

    add gif2ascii
```

* Agora ficou melhor de entender né? Tem várias branches: 

``` less
git branch -a
* master
  remotes/origin/HEAD -> origin/master
  remotes/origin/dev
  remotes/origin/master
  remotes/origin/sploits-dev
```

* Usando a lógica da frase `<no passwords in production!>`, então deve estar na branch `dev`:

```
git checkout dev
branch 'dev' set up to track 'origin/dev'.
Switched to a new branch 'dev'
```

* Listando o repo agora, outros arquivos e nesse readme novo que está a senha:

```
ls
code  README.md
```
---

### ✔️ Resultado Final

Ao acessar o arquivo, a senha do usuário do próximo nível é revelada.

---

### 📚 Aprendizados do Nível

Aprendemos a trocar a branch de um repositório, muito bacana.

---

## 🔗 Próximo Nível

[Ir para o próximo nível](../30%20(Level%2030%20-%2031)/readme.md)