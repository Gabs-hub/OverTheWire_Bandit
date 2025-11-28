# Nível 0 - 1 (OverTheWire: Bandit)

### 📌 Descrição do Desafio

The password for the next level is stored in a file called readme located in the home directory. Use this password to log into bandit1 using SSH. Whenever you find a password for a level, use SSH (on port 2220) to log into that level and continue the game.

---

### 🎯 Objetivo

Devemos acessar o arquivo readme, localizado no diretório home.

---


### 🔍 Passo a Passo da Lógica

* Ao entrar no servidor, já estamos no diretório home, portanto, basta apenas digitar o comando:

```
cat readme
```

---

### ✔️ Resultado Final

Ao acessar o arquivo, a senha do usuário do próximo nível é revelada.

---

### 📚 Aprendizados do Nível

Aprendemos a usar o comando cat, ferramenta básica mas fundamental para acessar arquivos no terminal.

---

## 🔗 Próximo Nível

[Ir para o próximo nível](../Level%201%20-%202/writeup.md)