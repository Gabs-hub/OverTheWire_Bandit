# Nível 19 - 20 (OverTheWire: Bandit)

### 📌 Descrição do Desafio

To gain access to the next level, you should use the setuid binary in the homedirectory. Execute it without arguments to find out how to use it. The password for this level can be found in the usual place (/etc/bandit_pass), after you have used the setuid binary.

---

### 🎯 Objetivo

Devemos executar o arquivo binário e acessar /etc/bandit_pass

---


### 🔍 Passo a Passo da Lógica

* Testando o arquivo, ele respondeu com a seguinte mensagem:

```
bandit19@bandit:~$ ./bandit20-do 
Run a command as another user.
```
* Ou seja, esse arquivo é como se fosse o bandit20, então podemos fazer tudo que ele faz, como acessar a senha:

```
bandit19@bandit:~$ ./bandit20-do cat /etc/bandit_pass/bandit20
```

---

### ✔️ Resultado Final

Ao acessar o arquivo, a senha do usuário do próximo nível é revelada.

---

### 📚 Aprendizados do Nível

Aprendemos a rodar binários pelo terminal, muito massa.

---

## 🔗 Próximo Nível

[Ir para o próximo nível](../Level%2020%20-%2021/writeup.md)