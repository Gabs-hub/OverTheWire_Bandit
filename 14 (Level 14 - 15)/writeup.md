# Nível 14 - 15 (OverTheWire: Bandit)

### 📌 Descrição do Desafio

The password for the next level can be retrieved by submitting the password of the current level to port 30000 on localhost.

---

### 🎯 Objetivo

Devemos acessar um serviço na porta 300, colocar a senha do nível anterior e o serviço retornará a senha.

---


### 🔍 Passo a Passo da Lógica

* Ao entrar no servidor usei o nmap (só por garantia), para localizar as portas:

```
bandit14@bandit:~$ nmap localhost
Starting Nmap 7.94SVN ( https://nmap.org ) at 2025-11-26 15:05 UTC
Nmap scan report for localhost (127.0.0.1)
Host is up (0.00016s latency).
Not shown: 992 closed tcp ports (conn-refused)
PORT      STATE SERVICE
22/tcp    open  ssh
1111/tcp  open  lmsocialserver
1840/tcp  open  netopia-vo2
4321/tcp  open  rwhois
8000/tcp  open  http-alt
9999/tcp  open  abyss
30000/tcp open  ndmps
50001/tcp open  unknown

Nmap done: 1 IP address (1 host up) scanned in 0.06 seconds
```
* Após isso, me conectei ao serviço com o netcat e digitei a senha:

```
bandit14@bandit:~$ nc localhost 30000
```

---

### ✔️ Resultado Final

Ao acessar o serviço e digitar a senha atual, a senha do usuário do próximo nível é revelada.

---

### 📚 Aprendizados do Nível

Aprendemos a identificar portas com nmap e estabelecer uma conexão via netcat.

---

## 🔗 Próximo Nível

[Ir para o próximo nível](../Level%2015%20-%2016/writeup.md)