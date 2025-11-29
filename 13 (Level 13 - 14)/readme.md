# Nível 13 - 14 (OverTheWire: Bandit)

### 📌 Descrição do Desafio

The password for the next level is stored in /etc/bandit_pass/bandit14 and can only be read by user bandit14. For this level, you don’t get the next password, but you get a private SSH key that can be used to log into the next level. Look at the commands that logged you into previous bandit levels, and find out how to use the key for this level.

---

### 🎯 Objetivo

Devemos acessar o arquivo de senha nos conectando via ssh com uma chave privada.

---


### 🔍 Passo a Passo da Lógica

* Ao entrar no servidor, nos deparamos com o arquivo:

```
./sshkey.private
```

* Abrindo o arquivo, localizamos a chave privada ssh, então só precisamos copiar para nossa máquina e usá-la para nos conectar ao usuário bandit14:

```
ssh -i suachavecopiada.key bandit14@bandit.labs.overthewire.org -p 2220

```

* Após nos conectamos, só precisamos acessar o arquivo:
```
/etc/bandit_pass/bandit14
```

---

### ✔️ Resultado Final

Ao acessar o arquivo, a senha do usuário do próximo nível é revelada.

---

### 📚 Aprendizados do Nível

Aprendemos a nos conectar via ssh por meio de uma chave privada.

---

## 🔗 Próximo Nível

[Ir para o próximo nível](../14%20(Level%2014%20-%2015)/readme.md)