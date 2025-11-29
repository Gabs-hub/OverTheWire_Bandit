# Nível 28 - 29 (OverTheWire: Bandit)

### 📌 Descrição do Desafio

There is a git repository at ssh://bandit28-git@bandit.labs.overthewire.org/home/bandit28-git/repo via the port 2220. The password for the user bandit28-git is the same as for the user bandit28.

---

### 🎯 Objetivo

Devemos fazer um `git clone` via `ssh` e pegar a senha do próximo nível.

---

### 🔍 Passo a Passo da Lógica

* Clonei o repositório:

```
git clone ssh://bandit28-git@bandit.labs.overthewire.org:2220/home/bandit28-git/repo
```

* Dentro do repositório, novamente tem um arquivo README, dentro dele tem a seguinte linha:

```
password: xxxxxxxx
```

* Ou seja, teóricamente a senha não pode ser revelada. Ou será que pode? e será que não tem um commit antigo com a senha? Rodei um `git log -p --all` para ver os registros:

``` less
set mark: ...skipping...
 - username: bandit29
-- password: <TBD>
-> master, origin/master, origin/HEAD)
Author: Morla Porla <morla@overthewire.org>
Date:   Tue Oct 14 09:26:24 2025 +0000

    fix info leak

diff --git a/README.md b/README.md
index d4e3b74..5c6457b 100644
--- a/README.md
+++ b/README.md
@@ -4,5 +4,5 @@ Some notes for level29 of bandit.
 ## credentials

 - username: bandit29
-- password: <A SENHA AQUI>
+- password: xxxxxxxxxx


commit 8b7c651b37ce7a94633b7b7b7c980ded19a16e4f
Author: Morla Porla <morla@overthewire.org>
Date:   Tue Oct 14 09:26:24 2025 +0000

    add missing data

diff --git a/README.md b/README.md
index 7ba2d2f..d4e3b74 100644                         -> master, origin/master, origin/HEAD)
Author: Morla Porla <morla@overthewire.org>
Date:   Tue Oct 14 09:26:24 2025 +0000

    fix info leak

diff --git a/README.md b/README.md
index d4e3b74..5c6457b 100644
--- a/README.md
+++ b/README.md

```

---

### ✔️ Resultado Final

Ao acessar o log, a senha do usuário do próximo nível é revelada.

---

### 📚 Aprendizados do Nível

Aprendemos a acessar os logs de um repositório git, com isso, vimos que é **MUITO IMPORTANTE**, não fazer besteirinha como jogar a chave da api e depois apagar, porque vai estar no log.

---

## 🔗 Próximo Nível

[Ir para o próximo nível](../28%20(Level%2028%20-%2029)/readme.md)