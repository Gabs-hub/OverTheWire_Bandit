# Nível 9 - 10 (OverTheWire: Bandit)

### 📌 Descrição do Desafio

The password for the next level is stored in the file data.txt in one of the few human-readable strings, preceded by several ‘=’ characters.

---

### 🎯 Objetivo

Devemos acessar o arquivo data.txt e encontrar a senha, precedida de caracteres "=".

---


### 🔍 Passo a Passo da Lógica

* Para encontrar a senha, combinaremos o comando strings e o comando grep:

```
strings data.txt | grep "==="
```
Tivemos que usar "strings" por conta de data.txt ser um arquivo binário

---

### ✔️ Resultado Final

Ao acessar o arquivo, a senha do usuário do próximo nível é revelada.

---

### 📚 Aprendizados do Nível

Aprendemos a usar o comando strings para ler arquivos binários.

---

## 🔗 Próximo Nível

[Ir para o próximo nível](../Level%2010%20-%2011/writeup.md)