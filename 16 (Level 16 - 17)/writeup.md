# Nível 16 - 17 (OverTheWire: Bandit)

### 📌 Descrição do Desafio

The credentials for the next level can be retrieved by submitting the password of the current level to a port on localhost in the range 31000 to 32000. First find out which of these ports have a server listening on them. Then find out which of those speak SSL/TLS and which don’t. There is only 1 server that will give the next credentials, the others will simply send back to you whatever you send to it.

---

### 🎯 Objetivo

Devemos descobrir a portas e qual o serviço correto está rodando entre as portas para podermos pegar a chave ssh do próximo nível.

---


### 🔍 Passo a Passo da Lógica

* Rodei o nmap com a flag -p para identificar as portas:

```
bandit16@bandit:~$ nmap -p31000-32000 localhost
Starting Nmap 7.94SVN ( https://nmap.org ) at 2025-11-26 15:23 UTC
Nmap scan report for localhost (127.0.0.1)
Host is up (0.00016s latency).
Not shown: 996 closed tcp ports (conn-refused)
PORT      STATE SERVICE
31046/tcp open  unknown
31518/tcp open  unknown
31691/tcp open  unknown
31790/tcp open  unknown
31960/tcp open  unknown
```
* Após isso, me conectei em cada uma para tentar identificar qual respondia com a chave

```
bandit16@bandit:~$ openssl s_client -connect localhost:<uma porta por vez> -quiet
```

---

### 📄 Arquivo/Local encontrado

* Colocando a senha na porta 31518, o servidor respondeu com a chave
```
bandit16@bandit:~$ openssl s_client -connect localhost:31518 -quiet
```

---

### ✔️ Resultado Final

Consegui a chave ssh e para conectar, só usar o comando:

```
ssh -i sua_chave.key bandit17@bandit.labs.overthewire.org -p 2220
```

---

### 📚 Aprendizados do Nível

Aprendemos a usar o nmap com a flag de portas e aprendemos a nos conectarvia openssl.

---

## 🔗 Próximo Nível

[Ir para o próximo nível](../Level%2017%20-%2018/writeup.md)