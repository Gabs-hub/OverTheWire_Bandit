# Nível 5 - 6 (OverTheWire: Bandit)

### 📌 Descrição do Desafio

The password for the next level is stored in a file somewhere under the inhere directory and has all of the following properties:

* human-readable
* 1033 bytes in size
* not executable

---

### 🎯 Objetivo

Devemos encontrar o arquivo correto escondido no diretorio "inhere", possuíndo as caracteristicas citadas acima.

---


### 🔍 Passo a Passo da Lógica

* Dentro do diretório inhere, usaremos o comando find com flags:

```
find -readable -size 1033c
```

Essas flags filgtram apenas os arquivos legíveis e com o tamanho de 1033 bytes.

---

### 📄 Arquivo/Local encontrado


```
./maybehere07/.file2
```

---

### ✔️ Resultado Final

Ao acessar o arquivo, a senha do usuário do próximo nível é revelada.

---

### 📚 Aprendizados do Nível

Aprendemos a usar o comando find e suas flags para encontrar arquivos específicos

---

## 🔗 Próximo Nível

[Ir para o próximo nível](../06%20(Level%206%20-%207)/readme.md)