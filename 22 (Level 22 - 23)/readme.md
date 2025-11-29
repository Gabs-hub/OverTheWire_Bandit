# Nível 22 - 23 (OverTheWire: Bandit)

### 📌 Descrição do Desafio

A program is running automatically at regular intervals from cron, the time-based job scheduler. Look in /etc/cron.d/ for the configuration and see what command is being executed.
NOTE: Looking at shell scripts written by other people is a very useful skill. The script for this level is intentionally made easy to read. If you are having problems understanding what it does, try executing it to see the debug information it prints.

---

### 🎯 Objetivo

Devemos explorar e identificar os arquvios de /etc/cron.d/, agora com outro arquivo

---


### 🔍 Passo a Passo da Lógica

* Ao entrar no servidor, entrei novamente em /etc/cron.d/, lendo agora o cronjob_bandit23:

```
bandit22@bandit:/etc/cron.d$ strings cronjob_bandit23
@reboot bandit23 /usr/bin/cronjob_bandit23.sh  &> /dev/null
* * * * * bandit23 /usr/bin/cronjob_bandit23.sh  &> /dev/null
```
* Mais uma vez leva à um arquivo .sh:

```
bandit22@bandit:/etc/cron.d$ strings /usr/bin/cronjob_bandit23.sh
#!/bin/bash
myname=$(whoami)
mytarget=$(echo I am user $myname | md5sum | cut -d ' ' -f 1)
echo "Copying passwordfile /etc/bandit_pass/$myname to /tmp/$mytarget"
cat /etc/bandit_pass/$myname > /tmp/$mytarget
Copying passwordfile /etc/bandit_pass/$mytarget to /tmp/8ca319486bfbbc3663ea0fbe81326349
```
* Interpretando, pode-se perceber que ele pega o arquivo de senha do usuário atual e coloca no diretório /tmp/8ca319486bfbbc3663ea0fbe81326349 mas o que acontece se mudar "myname=$(whoami)" por "myname=bandit23" e jogar no terminal?

```
bandit22@bandit:/etc/cron.d$ #!/bin/bash

myname=bandit23
mytarget=$(echo I am user $myname | md5sum | cut -d ' ' -f 1)

echo "Copying passwordfile /etc/bandit_pass/$myname to /tmp/$mytarget"

cat /etc/bandit_pass/$myname > /tmp/$mytarget
Copying passwordfile /etc/bandit_pass/bandit23 to /tmp/8ca319486bfbbc3663ea0fbe81326349
```

* Agora a senha de bandit23 que foi copiada
---

### 📄 Arquivo/Local encontrado


```
/tmp/8ca319486bfbbc3663ea0fbe81326349
```

---

### ✔️ Resultado Final

Agora acessar o arquivo, a senha do usuário do próximo nível é revelada.

---

### 📚 Aprendizados do Nível

Potencializamos o entendimento em shell script, com uma análise mais aprofundada.

---

## 🔗 Próximo Nível

[Ir para o próximo nível](../23%20(Level%2023%20-%2024)/readme.md)