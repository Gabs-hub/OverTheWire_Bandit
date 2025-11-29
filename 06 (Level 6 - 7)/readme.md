# Nível 6 - 7 (OverTheWire: Bandit)

### 📌 Descrição do Desafio

The password for the next level is stored somewhere on the server and has all of the following properties:

* owned by user bandit7
* owned by group bandit6
* 33 bytes in size

---

### 🎯 Objetivo

Mais uma vez iremos procurar um arquivo específico, mas agora em todo o servidor.

---


### 🔍 Passo a Passo da Lógica

* Ao entrar no servidor, nos direcionamos para o diretório "/" e usamos o comando find com as seguintes flags:

```
bandit6@bandit:/$ find -user bandit7 -group bandit6 -size 33c 2>/dev/null
```
Esse comando vai procurar por usuário, grupo e tamanho, ignorando os erros.

---

### 📄 Arquivo/Local encontrado


```
./var/lib/dpkg/info/bandit7.password
```

---

### ✔️ Resultado Final

Ao acessar o arquivo, a senha do usuário do próximo nível é revelada.

---

### 📚 Aprendizados do Nível

Aprendemos mais uma variação do find, localizando por grupo e por usuário.

---

## 🔗 Próximo Nível

[Ir para o próximo nível](../07%20(Level%207%20-%208)/readme.md)