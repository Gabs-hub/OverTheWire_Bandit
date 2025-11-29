# Nível 21 - 22 (OverTheWire: Bandit)

### 📌 Descrição do Desafio

A program is running automatically at regular intervals from cron, the time-based job scheduler. Look in /etc/cron.d/ for the configuration and see what command is being executed.

---

### 🎯 Objetivo

Devemos acessar explorar e identificar os arquvios de /etc/cron.d/.

---


### 🔍 Passo a Passo da Lógica

* Ao entrar no servidor, listei os arquivos do diretório cron.d:

```
bandit21@bandit:~$ cd /etc/cron.d
bandit21@bandit:/etc/cron.d$ ls
behemoth4_cleanup  clean_tmp  cronjob_bandit22  cronjob_bandit23  cronjob_bandit24  e2scrub_all  leviathan5_cleanup  manpage3_resetpw_job  otw-tmp-dir  sysstat
```

* Pensando pela lógica do nível, o arquivo a ser visto é o cronjob_bandit_22:

```
bandit21@bandit:/etc/cron.d$ strings cronjob_bandit22
@reboot bandit22 /usr/bin/cronjob_bandit22.sh  &> /dev/null
* * * * * bandit22 /usr/bin/cronjob_bandit22.sh  &> /dev/null
```

* Achei um .sh em /usr/bin/cronjob_bandit22.sh e decidi ler o que estava dentro dele:

```
bandit21@bandit:/etc/cron.d$ strings /usr/bin/cronjob_bandit22.sh
#!/bin/bash
chmod 644 /tmp/t7O6lds9S0RqQh9aMcz6ShpAoZKF7fgv
cat /etc/bandit_pass/bandit22 > /tmp/t7O6lds9S0RqQh9aMcz6ShpAoZKF7fgv
```
* Objetivo concluído, achei o local onde está a senha 

---

### 📄 Arquivo/Local encontrado


```
/tmp/t7O6lds9S0RqQh9aMcz6ShpAoZKF7fgv
```

---

### ✔️ Resultado Final

Ao acessar o arquivo, a senha do usuário do próximo nível é revelada.

---

### 📚 Aprendizados do Nível

Aprendemos a explorar de modo mais avançado o sistema, e a interpretar shell script.

---

## 🔗 Próximo Nível

[Ir para o próximo nível](../22%20(Level%2022%20-%2023)/readme.md)