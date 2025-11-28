# Nível 18 - 19 (OverTheWire: Bandit)

### 📌 Descrição do Desafio

The password for the next level is stored in a file readme in the homedirectory. Unfortunately, someone has modified .bashrc to log you out when you log in with SSH.

---

### 🎯 Objetivo

Devemos acessar o arquivo readme mesmo sendo desconectados do ssh

---


### 🔍 Passo a Passo da Lógica

* O ssh tem uma função muito interessante, você pode passar comandos direto pela conexão. Então que tal dar um cat por ele?:

```
ssh bandit18@bandit.labs.overthewire.org -p 2220 "cat readme"
```
* Foi um sucesso.

---

### ✔️ Resultado Final

Ao acessar o arquivo, a senha do usuário do próximo nível é revelada.

---

### 📚 Aprendizados do Nível

Aprendemos a usar comandos no mesmo instante que conetamos pelo ssh, conhecimento muito valiso.

---

## 🔗 Próximo Nível

[Ir para o próximo nível](../Level%2019%20-%2020/writeup.md)