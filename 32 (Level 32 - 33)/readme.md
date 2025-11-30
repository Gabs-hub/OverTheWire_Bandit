# Nível 32 - 33 (OverTheWire: Bandit)

### 📌 Descrição do Desafio

After all this git stuff, it’s time for another escape. Good luck!

---

### 🎯 Objetivo

Amém, acabou a bagaceira de git. Agora tem q se virar em outro escape

---

### 🔍 Passo a Passo da Lógica

* Conectando no servidor, é assim que fui recebido:

```

      ,----..            ,----,          .---.
     /   /   \         ,/   .`|         /. ./|
    /   .     :      ,`   .'  :     .--'.  ' ;
   .   /   ;.  \   ;    ;     /    /__./ \ : |
  .   ;   /  ` ; .'___,/    ,' .--'.  '   \' .
  ;   |  ; \ ; | |    :     | /___/ \ |    ' '
  |   :  | ; | ' ;    |.';  ; ;   \  \;      :
  .   |  ' ' ' : `----'  |  |  \   ;  `      |
  '   ;  \; /  |     '   :  ;   .   \    .\  ;
   \   \  ',  /      |   |  '    \   \   ' \ |
    ;   :    /       '   :  |     :   '  |--"
     \   \ .'        ;   |.'       \   \ ;
  www. `---` ver     '---' he       '---" ire.org


Welcome to OverTheWire!

If you find any problems, please report them to the #wargames channel on
discord or IRC.

--[ Playing the games ]--

  This machine might hold several wargames.
  If you are playing "somegame", then:

    * USERNAMES are somegame0, somegame1, ...
    * Most LEVELS are stored in /somegame/.
    * PASSWORDS for each level are stored in /etc/somegame_pass/.

  Write-access to homedirectories is disabled. It is advised to create a
  working directory with a hard-to-guess name in /tmp/.  You can use the
  command "mktemp -d" in order to generate a random and hard to guess
  directory in /tmp/.  Read-access to both /tmp/ is disabled and to /proc
  restricted so that users cannot snoop on eachother. Files and directories
  with easily guessable or short names will be periodically deleted! The /tmp
  directory is regularly wiped.
  Please play nice:

    * don't leave orphan processes running
    * don't leave exploit-files laying around
    * don't annoy other players
    * don't post passwords or spoilers
    * again, DONT POST SPOILERS!
      This includes writeups of your solution on your blog or website!

--[ Tips ]--

  This machine has a 64bit processor and many security-features enabled
  by default, although ASLR has been switched off.  The following
  compiler flags might be interesting:

    -m32                    compile for 32bit
    -fno-stack-protector    disable ProPolice
    -Wl,-z,norelro          disable relro

  In addition, the execstack tool can be used to flag the stack as
  executable on ELF binaries.

  Finally, network-access is limited for most levels by a local
  firewall.

--[ Tools ]--

 For your convenience we have installed a few useful tools which you can find
 in the following locations:

    * gef (https://github.com/hugsy/gef) in /opt/gef/
    * pwndbg (https://github.com/pwndbg/pwndbg) in /opt/pwndbg/
    * gdbinit (https://github.com/gdbinit/Gdbinit) in /opt/gdbinit/
    * pwntools (https://github.com/Gallopsled/pwntools)
    * radare2 (http://www.radare.org/)

--[ More information ]--

  For more information regarding individual wargames, visit
  http://www.overthewire.org/wargames/

  For support, questions or comments, contact us on discord or IRC.

  Enjoy your stay!

WELCOME TO THE UPPERCASE SHELL
>> 
```

* Tem, aparentemente uma shell maluca com letras maiúsculas. Hora de testar algumas coisas:

```
>> ls
sh: 1: LS: Permission denied
>> LS
sh: 1: LS: Permission denied
>> PWD
sh: 1: PWD: Permission denied
>> ECHO OI
sh: 1: ECHO: Permission denied
```

* Tem alguma brincadeirinha muito diferente aí, está transformando tudo escrito na shell para maiúsculo.

* Como resolver? É mais simples do que você pode imaginar. Nos SO's, existem as variáveis de ambiente, local, shell e, essas váriaveis geralmente são maiúsculas e iniciam com um `$`. Por exemplo:

```
>> $PWD
sh: 1: /home/bandit32: Permission denied
```
* Olha só que massa, mostrou o diretório atual

* Agora o pulo do gato, existe uma variável que aponta para o bash, a variável `$0`, e como é número, não tem problema digitar ela no desafio:

```
>> $0
$ 
```

* Olha só que massa, agora é possível usar o bash e digitar oss comandos normalmente.


```
$ cd /etc/bandit_pass
$ ls
bandit0   bandit12  bandit16  bandit2	bandit23  bandit27  bandit30  bandit4  bandit8
bandit1   bandit13  bandit17  bandit20	bandit24  bandit28  bandit31  bandit5  bandit9
bandit10  bandit14  bandit18  bandit21	bandit25  bandit29  bandit32  bandit6
bandit11  bandit15  bandit19  bandit22	bandit26  bandit3   bandit33  bandit7
$ cat bandit33
```

---

### ✔️ Resultado Final

Ao acessar o arquivo, a senha do pŕoximo nível é revelada.

---

### 📚 Aprendizados do Nível

Aprendemos sobre as variáveis, e como é possível acessar elas mesmo com as limitações de letras maiúsculas

---

## 🔗 Próximo Nível

[Ir para o próximo nível](../33%20(Level%2033%20-%2034)%20Final/readme.md)