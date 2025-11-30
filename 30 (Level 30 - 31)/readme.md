# Nível 30 - 31 (OverTheWire: Bandit)

### 📌 Descrição do Desafio

There is a git repository at ssh://bandit30-git@bandit.labs.overthewire.org/home/bandit30-git/repo via the port 2220. The password for the user bandit30-git is the same as for the user bandit30.

---

### 🎯 Objetivo

Devemos fazer um `git clone` via `ssh` e pegar a senha do próximo nível.

---

### 🔍 Passo a Passo da Lógica

* Clonei o repositório:

```
git clone ssh://bandit30-git@bandit.labs.overthewire.org:2220/home/bandit30-git/repo
```

* Dentro do repositório, novamente tem um arquivo README, dentro dele tem:

```
just an epmty file... muahaha
```

* Novamente, sem senha no arquivo, então olhei o que tinha dentro do diretório `.git`:

```
ls
branches  description  hooks  info  objects      refs
config    HEAD         index  logs  packed-refs
```

* Abrindo o arquivo packed-refs, vi algo interessante:

```
# pack-refs with: peeled fully-peeled sorted 
62152a9969c62cb647406aa88c1b5376dcf58968 refs/remotes/origin/master
84368f3a7ee06ac993ed579e34b8bd144afad351 refs/tags/secret
```

* Tem uma tag chamada secret, o que seŕa que tem dentro dela?

```
git show secret
```

---

### ✔️ Resultado Final

Ao acessar o secret, a senha do usuário do próximo nível é revelada.

---

### 📚 Aprendizados do Nível

Aprendemos a acessar tags no git.

---

## 🔗 Próximo Nível

[Ir para o próximo nível](../31%20(Level%2031%20-%2032)/readme.md)