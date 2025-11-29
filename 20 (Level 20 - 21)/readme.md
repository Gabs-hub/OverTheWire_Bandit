# Nível 20 - 21 (OverTheWire: Bandit)

### 📌 Descrição do Desafio

There is a setuid binary in the homedirectory that does the following: it makes a connection to localhost on the port you specify as a commandline argument. It then reads a line of text from the connection and compares it to the password in the previous level (bandit20). If the password is correct, it will transmit the password for the next level (bandit21).

---

### 🎯 Objetivo

Devemos criar uma conexão e usar o binário de /home para conectar e responder a senha do próximo nível.

---


### 🔍 Passo a Passo da Lógica

* Analizando o arquivo de conexão, via strings, temos a seguinte resposta:

```
bandit20@bandit:~$ strings ./suconnect 
/lib/ld-linux.so.2
_IO_stdin_used
fgets
puts
__stack_chk_fail
exit
getaddrinfo
fopen
socket
strlen
send
recv
atoi
__libc_start_main
stderr
fprintf
strchr
fclose
memset
connect
gai_strerror
fwrite
strcmp
libc.so.6
GLIBC_2.4
GLIBC_2.1
GLIBC_2.34
GLIBC_2.0
_gmon_start_
Usage: %s <portnumber>
This program will connect to the given port on localhost using TCP. If it receives the correct password from the other side, the next password is transmitted back.
ERROR: Invalid portnumber
localhost
getaddrinfo: %s
Could not connect
ERROR: Can't read from socket
Read: %s
/home/bandit21/.prevpass
Password matches, sending next password
/etc/bandit_pass/bandit21
ERROR: This doesn't match the current password!
FAIL!
;*2$"
GCC: (Ubuntu 13.3.0-6ubuntu2~24.04) 13.3.0
crt1.o
__abi_tag
__wrap_main
crtstuff.c
deregister_tm_clones
__do_global_dtors_aux
completed.0
__do_global_dtors_aux_fini_array_entry
frame_dummy
__frame_dummy_init_array_entry
bandit21.c
_FRAME_END_
_DYNAMIC
__GNU_EH_FRAME_HDR
GLOBAL_OFFSET_TABLE
strcmp@GLIBC_2.0
__libc_start_main@GLIBC_2.34
__x86.get_pc_thunk.bx
stderr@GLIBC_2.0
fgets@GLIBC_2.0
_edata
fclose@GLIBC_2.1
_fini
__stack_chk_fail@GLIBC_2.4
fwrite@GLIBC_2.0
__data_start
puts@GLIBC_2.0
_gmon_start_
exit@GLIBC_2.0
__dso_handle
_IO_stdin_used
strchr@GLIBC_2.0
strlen@GLIBC_2.0
fprintf@GLIBC_2.0
fopen@GLIBC_2.1
memset@GLIBC_2.0
_end
_dl_relocate_static_pie
_fp_hw
gai_strerror@GLIBC_2.1
__bss_start
get_password
atoi@GLIBC_2.0
socket@GLIBC_2.0
getaddrinfo@GLIBC_2.0
_TMC_END_
connect@GLIBC_2.0
_init
recv@GLIBC_2.0
close@GLIBC_2.0
send@GLIBC_2.0
.symtab
.strtab
.shstrtab
.interp
.note.gnu.build-id
.note.ABI-tag
.gnu.hash
.dynsym
.dynstr
.gnu.version
.gnu.version_r
.rel.dyn
.rel.plt
.init
.text
.fini
.rodata
.eh_frame_hdr
.eh_frame
.init_array
.fini_array
.dynamic
.got
.got.plt
.data
.bss
.comment
```

* No trecho:
```
Usage: %s <portnumber>
This program will connect to the given port on localhost using TCP. If it receives the correct password from the other side, the next password is transmitted back.
```

* Pode-se perceber que ele se conecta a uma porta que esteja escutando, ou seja, devemos criar o socket para ele se conectar. Podemos fazer isso usando o netcat com o parâmetro -l.
* #### (OBS: você vai precisar de um terminal para escutar e outro para usar o binário)

* Terminal 1

```
bandit20@bandit:~$ nc -l localhost <porta_qualquer>
```

* Terminal 2

```
bandit20@bandit:~$ ./suconnect <porta_qualquer>
```

* Após isso, no terminal 1 digite a senha do nível anterior e ele responderá com a senha do próximo nível.

---

### 📚 Aprendizados do Nível

Aprendemos a criar um socket via netcat e estabelecer uma conexão nele

---

## 🔗 Próximo Nível

[Ir para o próximo nível](../21%20(Level%2021%20-%2022)/readme.md)