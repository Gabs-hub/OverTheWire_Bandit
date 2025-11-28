# Nível 8 - 9 (OverTheWire: Bandit)

### 📌 Descrição do Desafio

The password for the next level is stored in the file data.txt and is the only line of text that occurs only once

---

### 🎯 Objetivo

Devemos acessar uma linha no arquivo que não contém texto repetido em outras linhas.

---


### 🔍 Passo a Passo da Lógica

* Para essa ação, precisaremos usar dois comando unidos, o "sort" e o "uniq":

```
sort data.txt | uniq -u
```

Por qual motivo usamos os dois comandos? Simples, o uniq só consegue identificar linhas repetidas uma atrás da outra, logo, tivemos que ordenar o texto para que isso fosse possível.

---

### ✔️ Resultado Final

Ao acessar o arquivo, a senha do usuário do próximo nível é revelada.

---

### 📚 Aprendizados do Nível

Aprendemos dois novos comandos e como usar eles em conjunto.

---

## 🔗 Próximo Nível

[Ir para o próximo nível](../Level%209%20-%2010/writeup.md)