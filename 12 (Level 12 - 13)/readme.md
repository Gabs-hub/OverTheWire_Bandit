# Nível 12 - 13 (OverTheWire: Bandit)

### 📌 Descrição do Desafio

The password for the next level is stored in the file data.txt, which is a hexdump of a file that has been repeatedly compressed. For this level it may be useful to create a directory under /tmp in which you can work. Use mkdir with a hard to guess directory name. Or better, use the command “mktemp -d”. Then copy the datafile using cp, and rename it using mv (read the manpages!)

---

### 🎯 Objetivo

Trabalhar com um arquivo que contém um hexdump de um arquivo comprimido várias vezes, criar um diretório temporário (ou muito específico) para manipular os arquivos, restaurar o binário original a partir do hexdump, identificar corretamente o tipo de cada arquivo e descompactar repetidamente até chegar ao arquivo de senha.

---


### 🔍 Passo a Passo da Lógica

* Primeiro criamos um diretório em tmp para salvar o arquivo data.txt:

```
mkdir /tmp/nome_dificil
```

```
cp data.txt /tmp/nome_dificil
```

* Depois, restauramos o hexdump
```
xxd -r data.txt > arquivo.bin
```
* #### Processo de descompressão em camadas

Com o arquivo restaurado descompactamos o arquivo. A lógica é simples e repetitiva:

```
file → renomear → descompactar → repetir
```

Encontramos vários tipos de arquivo. Aqui estão os comandos corretos para cada um.

* #### 1. Arquivo gzip

```
mv arquivo arquivo.gz
gunzip arquivo.gz
```

* #### 2. Arquivo bzip2

```
mv arquivo arquivo.bz2
bunzip2 arquivo.bz2
```

* #### 3. Arquivo tar

```
tar -xf arquivo
```

* #### 4. Arquivo texto (final)

Quando file mostrar `ASCII text`, apenas, significa que podemos parar e acessar o arquivo.

---

### ✔️ Resultado Final

Ao acessar o arquivo, a senha do usuário do próximo nível é revelada.

---

### 📚 Aprendizados do Nível

Neste nível aprendemos MUITA COISA:

* Como restaurar um arquivo a partir de um hexdump usando xxd -r.

* Como identificar tipos de arquivo com o comando file.

* Como extrair diferentes formatos de compressão (gzip, bzip2, tar).

* Como trabalhar com arquivos em múltiplas camadas de compressão, mantendo organização em diretórios temporários.

* A importância de verificar cada etapa antes de prosseguir para não corromper dados.

* Um padrão repetitivo útil: file → renomear → descompactar → repetir até chegar ao arquivo final.

* Dicas de organização no diretório /tmp, evitando bagunça no sistema principal.

---

## 🔗 Próximo Nível

[Ir para o próximo nível](../13%20(Level%2013%20-%2014)/readme.md)