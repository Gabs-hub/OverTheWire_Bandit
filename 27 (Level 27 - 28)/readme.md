# Nível 27 - 28 (OverTheWire: Bandit)

### 📌 Descrição do Desafio

There is a git repository at ssh://bandit27-git@bandit.labs.overthewire.org/home/bandit27-git/repo via the port 2220. The password for the user bandit27-git is the same as for the user bandit27.

Clone the repository and find the password for the next level.

---

### 🎯 Objetivo

Devemos fazer um `git clone` via `ssh` e pegar a senha do próximo nível.

---

### 🔍 Passo a Passo da Lógica

* Para clonar o repositório com ssh, deve-se usar o seguinte comando:

```
git clone ssh://bandit27-git@bandit.labs.overthewire.org:2220/home/bandit27-git/repo
```

* Digita-se a senha do usuário bandit27-git (mesma do bandit27) e assim o repositório é clonado.

* Com o repositório baixado, basta acessar o arquivo `repo/README`.

---

### ✔️ Resultado Final

Ao acessar o arquivo, a senha do usuário do próximo nível é revelada.

---

### 📚 Aprendizados do Nível

Aprendemos a clonar um repositório com git clone e ssh.

---

## 🔗 Próximo Nível

[Ir para o próximo nível](../28%20(Level%2028%20-%2029)/writeup.md)