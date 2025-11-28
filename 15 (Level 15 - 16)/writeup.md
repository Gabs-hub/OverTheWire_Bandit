# Nível 15 - 16 (OverTheWire: Bandit)

### 📌 Descrição do Desafio

The password for the next level can be retrieved by submitting the password of the current level to port 30001 on localhost using SSL/TLS encryption.
---

### 🎯 Objetivo

Devemos acessar outro serviço, agora localizado na porta 30001.

---


### 🔍 Passo a Passo da Lógica

* Rodei novamente o nmap e tive uma surpresa, não tem nada rodando na porta 30001:

```
nmap localhost
Starting Nmap 7.94SVN ( https://nmap.org ) at 2025-11-26 15:14 UTC
Nmap scan report for localhost (127.0.0.1)
Host is up (0.00014s latency).
Not shown: 993 closed tcp ports (conn-refused)
PORT      STATE SERVICE
22/tcp    open  ssh
1111/tcp  open  lmsocialserver
1840/tcp  open  netopia-vo2
4321/tcp  open  rwhois
8000/tcp  open  http-alt
30000/tcp open  ndmps
50001/tcp open  unknown

Nmap done: 1 IP address (1 host up) scanned in 0.06 seconds
```
* Pensei que poderia haver algum erro nas instruções, e que na verdade o serviço roda na porta 50001. Fiz o seguinte teste:

```
bandit15@bandit:~$ nc localhost 50001
oi
Wrong! Please enter the correct current password.
```
* Ou seja, realmente o serviço estava na porta 50001, então só precisava realizar o mesmo passo no excercício anterior.
---

### ✔️ Resultado Final

Ao acessar o serviço e digitar a senha atual, a senha do usuário do próximo nível é revelada.

---

### 📚 Aprendizados do Nível

Aprendemos a importância de sabermos identificar onde os serviços estão rodando, para evitar problemas como as instruções erradas do desafio.

---

## 🔗 Próximo Nível

[Ir para o próximo nível](../Level%2016%20-%2017/writeup.md)