# Nível 0  (OverTheWire: Bandit)

### 📌 Descrição do Desafio

The goal of this level is for you to log into the game using SSH. The host to which you need to connect is bandit.labs.overthewire.org, on port 2220. The username is bandit0 and the password is bandit0. Once logged in, go to the Level 1 page to find out how to beat Level 1.

---

### 🎯 Objetivo

O objetivo é bem simples, iremos estabelecer uma conexão ssh com o servidor na porta 2220.

---


### 🔍 Passo a Passo da Lógica

* Acessar o terminal e digitar o comando:


```
ssh bandit0@bandit.labs.overthewire.org -p 2220
```
* O servidor irá perguntar:

```
Are you sure you want to continue connecting (yes/no/[fingerprint])?
```

* Digite "yes", e o servidor pedirá a senha:

```
bandit0@bandit.labs.overthewire.org's password:
```
* Digite a senha "bandit0" e finalmente conseguirá se conectar.

---


### 📚 Aprendizados do Nível

O level 0 é bem simples, apenas aprendemos à estabelecer uma conexão SSH. Esse comando vai ser essencial, pois cada nível do jogo está em um usuário diferente no servidor.

---

## 🔗 Próximo Nível

[Ir para o próximo nível](../00%20(Level%200%20-%201)/readme.md)