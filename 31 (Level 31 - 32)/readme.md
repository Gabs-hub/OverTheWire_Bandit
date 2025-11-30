# Nível 31 - 32 (OverTheWire: Bandit)

### 📌 Descrição do Desafio

There is a git repository at ssh://bandit31-git@bandit.labs.overthewire.org/home/bandit31-git/repo via the port 2220. The password for the user bandit31-git is the same as for the user bandit31.

---

### 🎯 Objetivo

Devemos fazer um `git clone` via `ssh` e pegar a senha do próximo nível.

---

### 🔍 Passo a Passo da Lógica

* Clonei o repositório:

```
git clone ssh://bandit31-git@bandit.labs.overthewire.org:2220/home/bandit31-git/repo
```

* Dentro do repositório, novamente tem um arquivo README, dentro dele tem:

```
This time your task is to push a file to the remote repository.

Details:
    File name: key.txt
    Content: 'May I come in?'
    Branch: master
```

* Novamente, sem senha no arquivo, mas agora com instruções para criar e dar push em um arquivo. Antes disso, vamos ver o `.gitignore`?

```
ls -la
total 20
drwxrwxr-x  3 gabs gabs 4096 nov 30 11:00 .
drwxr-xr-x 12 gabs gabs 4096 nov 30 10:59 ..
drwxrwxr-x  8 gabs gabs 4096 nov 30 11:00 .git
-rw-rw-r--  1 gabs gabs    6 nov 30 11:00 .gitignore
-rw-rw-r--  1 gabs gabs  147 nov 30 11:00 README.md

cat .gitignore
*.txt
```

* Interessante, ele quer que enviemos o arquivo key.txt, mas tá ignorando qualquer txt KKKKKKKKKKKKKKKK. Vamos lá resolver.

* Forcei com `git add -f` e depois fiz o commit:

```
git add -f key.txt

git commit -a
[master 46242bd] acho que consegui ein
 1 file changed, 1 insertion(+)
 create mode 100644 key.txt
```

* Agora sim, hora do push:

```
git push
                         _                     _ _ _   
                        | |__   __ _ _ __   __| (_) |_ 
                        | '_ \ / _` | '_ \ / _` | | __|
                        | |_) | (_| | | | | (_| | | |_ 
                        |_.__/ \__,_|_| |_|\__,_|_|\__|
                                                       

                      This is an OverTheWire game server. 
            More information on http://www.overthewire.org/wargames

backend: gibson-0
bandit31-git@bandit.labs.overthewire.org's password: 
Enumerating objects: 4, done.
Counting objects: 100% (4/4), done.
Delta compression using up to 8 threads
Compressing objects: 100% (2/2), done.
Writing objects: 100% (3/3), 328 bytes | 328.00 KiB/s, done.
Total 3 (delta 0), reused 0 (delta 0), pack-reused 0
remote: ### Attempting to validate files... ####
remote: 
remote: .oOo.oOo.oOo.oOo.oOo.oOo.oOo.oOo.oOo.oOo.
remote: 
remote: Well done! Here is the password for the next level:
remote: <A SENHA VAI ESTAR AQUI>
```

---

### ✔️ Resultado Final

Conseguindo dar o push, a senha do próximo nível é revelada.

---

### 📚 Aprendizados do Nível

Aprendemos a fazer um push no repositório e a "burlar" o gitignore.

---

## 🔗 Próximo Nível

[Ir para o próximo nível](../32%20(Level%2032%20-%2033)/readme.md)