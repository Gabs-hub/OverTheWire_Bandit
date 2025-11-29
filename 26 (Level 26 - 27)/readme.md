# Nível 12 - 13 (OverTheWire: Bandit)

### 📌 Descrição do Desafio

Good job getting a shell! Now hurry and grab the password for bandit27!

---

### 🔍 Passo a Passo da Lógica

* Não tem muita dificuldade, já foi feito um desafio idêntico, basicamente, tem um arquivo chamado `bandit27-do`:

```
bandit26@bandit:~$ ls
bandit27-do  text.txt
```

* Rodando, ele faz aquela mesma coisa de antes de rodar como se fosse outro usuário:

```
bandit26@bandit:~$ ./bandit27-do
Run a command as another user.
```

* Então é só dar um cat na senha do bandit27:

```
./bandit27-do cat /etc/bandit_pass/bandit27
```

---

## 🔗 Próximo Nível

[Ir para o próximo nível](../27%20(Level%2027%20-%2028)/readme.md)