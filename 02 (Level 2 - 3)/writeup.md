# Nível 2 - 3 (OverTheWire: Bandit)

### 📌 Descrição do Desafio

The password for the next level is stored in a file called --spaces in this filename-- located in the home directory.
---

### 🎯 Objetivo

Devemos acessar o arquivo --spaces in this filename--, localizado no diretório home.

---


### 🔍 Passo a Passo da Lógica

* Novamente usaremos o cat, mas para outro tipo de caracteres especias:

```
cat -- '--spaces in this filename--'
```

* Também pode-se usar o comando aprendido no desafio passado

```
cat ./'--spaces in this filename--'
```

---

### ✔️ Resultado Final

Ao acessar o arquivo, a senha do usuário do próximo nível é revelada.

---

### 📚 Aprendizados do Nível

Aprendemos novas formas de capturar arquivos com caracteres especiais.

---

## 🔗 Próximo Nível

[Ir para o próximo nível](../Level%203%20-%204/writeup.md)