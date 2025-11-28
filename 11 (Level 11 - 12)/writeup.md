# Nível 11 - 12 (OverTheWire: Bandit)

### 📌 Descrição do Desafio

The password for the next level is stored in the file data.txt, where all lowercase (a-z) and uppercase (A-Z) letters have been rotated by 13 positions.

---

### 🎯 Objetivo

Devemos aplicar o inverso do ROT13 para descobrir a senha

---


### 🔍 Passo a Passo da Lógica

* Primeiramente descobrimos do que se trata o ROT13, que basicamente troca as letras do alfabeto para 13 posições à frente, ou seja:
* #### Letra A -> ROT13 -> Letra N
* Para aplicar essa lógica no terminal, usaremos o cat unido ao comando tr, capaz de traduzir com as devidas instruções:

```
cat data.txt | tr 'A-Za-z' 'N-ZA-Mn-za-m'
```

---

### ✔️ Resultado Final

Ao acessar o arquivo com os comandos, a senha do usuário do próximo nível é revelada.

---

### 📚 Aprendizados do Nível

Aprendemos como funciona o ROT13 e como traduzir via terminal.

---

## 🔗 Próximo Nível

[Ir para o próximo nível](../Level%2012%20-%2013/writeup.md)