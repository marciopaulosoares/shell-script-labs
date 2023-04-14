## touch
Cria um arquivo ou atualiza um horario de criação do arquivo
```
touch arquivo
```
## echo
```
echo -n "Não adiciona uma quebra de linha "
echo -e "curso shell \t script, interpreta quebra de linhas, utilizada para formatar saidas"
```
## mkdir
```
mkdir -p diretorio1/diretorio2/diretorio3
```
Cria a estrutura de diretórios

## rm
```
rm -r  diretorio
```
Remove o diretório com arquivos

```
rm -f arquivo-inexistente
```
tenta remover o arquivo, caso ele não exista, não gera erro.

## cat
```
cat -b alunox.txt

1 André Gonçalves
2 Paulo Freitas

3 Maria Antonieto Sousa

```
obtem o conteúdo do arquivo e numera as linhas que não estão em branco.
Ex.:

```
cat -n alunox.txt

1 André Gonçalves
2 Paulo Freitas
3
4 Maria Antonieto Sousa

```
obtem o conteúdo do arquivo e numera todas as linhas


```
cat -A alunox.txt

Paulo Freitas$

```
Exibe caracteres especiais, notificação de tabulação etc

##  tac
```
tac alunos.txt
```
Faz a leitura das linhas do arquivo do final para o início.

##  tail
```
tail -n5 arquivo-grande.txt
tail -5 arquivo-grande.txt
```
Lê as últimas 5 linhas de um arquivo.

##  head
```
head arquivo-grande.txt
head -n5 arquivo-grande.txt
```
Exibe as n linhas do inicio de um arquivo.

```
head -c10 arquivo-grande.txt
```
Exibe os 10 primeiros caracteres do arquivo.

##  wc
```
$ wc names.txt
72     153     934 names.txt
```
conta o número de linhas, palavras e caracteres.

```
$ wc -l names.txt
$ wc -w names.txt
$ wc -c names.txt (número de bytes)
$ wc -m names.txt (número de caracteres)
$ wc -m names*
     924 names.txt
     165 names2.txt
    1089 total
```
##  obtendo a saída de um comando como entrada em outro.

```
$ tail -n5 names.txt | wc -w
      11
```
## sort
```
sort names.txt
sort -r names.txt
sort -k2 names.txt
```
Ordena os itens do arquivo. O parâmetro -r coloca em ordem reversa.
-k é o indice de ordenação, no exemplo k2 ordena pelo segundo campo.
```
tail /etc/passwd | sort -k3 -t":"
```
Ordena pelo terceiro campo com delimitador sendo o ":", para considerar o terceiro parâmetro como número, basta acrescentar -g

```
tail /etc/passwd | sort -k3 -t":" -g
```

## uniq
```
uniq names.txt
```
Considera repetido se tiver em sequencia, para melhor resultado deve se usar o sort
```
sort names.txt | uniq
```
```
sort names.txt | uniq -u
```
Filtra linhas que apareceram apenas uma vez.
```
sort names.txt | uniq -d
```
Mostra as linhas que apareceram duplicadas
```
sort names.txt | uniq -c
```
Conta as repetições e traz o item.
```
sort names.txt | uniq -c | sort -r | head -n1
```
Obtem a linha com mais repetições

## tr

Troca letras minúsculas por maiúsculas
```
cat names.txt| tr a-z A-Z
PATTY O’FURNITURE
PADDY O’FURNITURE

```
Deletar letras
```
cat names.txt| tr -d aei
Ptty O’Furntur
Pddy O’Furntur
Olv Yw

```
Suprimir uma letra
```
echo "Shell script" | tr -s l
Shel script
```

## cut
```
cat names.txt| cut -c1-4
Patt
Padd

cat names.txt| cut -c1,3
cat names.txt| cut -c1,3
Pt
Pd


```
Corta por campos, selecionando o espaço como divisor entre uma palavra e outra
```
cat names.txt| cut -d" " -f1       
Patty
Paddy
```
