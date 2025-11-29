# Nível 4 - 5 (OverTheWire: Bandit)

### 📌 Descrição do Desafio

The password for the next level is stored in the only human-readable file in the inhere directory. Tip: if your terminal is messed up, try the “reset” command.

---

### 🎯 Objetivo

Devemos acessar o único arquivo "legível" no diretório "inhere".

---


### 🔍 Passo a Passo da Lógica

* Listando os arquivos no diretório, encontra-se o seguinte:

```
bandit4@bandit:~/inhere$ ls
-file00  -file01  -file02  -file03  -file04  -file05  -file06  -file07  -file08  -file09
```

* Para localizar o arquivo correto, usamos o comando "file" com a flag "-l":
```
bandit4@bandit:~/inhere$ file ./*
./-file00: data
./-file01: OpenPGP Public Key
./-file02: OpenPGP Public Key
./-file03: data
./-file04: data
./-file05: data
./-file06: data
./-file07: ASCII text
./-file08: data
./-file09: data
```
---

### 📄 Arquivo/Local encontrado


```
-file07
```

---

### ✔️ Resultado Final

Ao acessar o arquivo, a senha do usuário do próximo nível é revelada.

---

### 📚 Aprendizados do Nível

Aprendemos a listar e identificar o tipo dos arquivos em um diretório.

---

## 🔗 Próximo Nível

[Ir para o próximo nível](../05%20(Level%205%20-%206)/readme.md)