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

## diff
```
diff -w listaA.txt listaB.txt

3c3
< Ricardo 
---
> Ricardo Nonato
```
Mostra que na linha 3 existe o nome Ricardo no arquivo da esquerda e no da direita existe Ricardo Nonato

```
diff -r diretorio01 diretorio02
```
Compara os arquivos de dois diretórios.

## grep

```
grep Marcio alunos.txt
grep Marcio alunos*
grep -i (ignora o Case)
grep -c Ana (conta a quantidade de ocorrências)
grep -v Ana (não exibe a linha que contem a expressão)
grep -r  Ana * (procura recursivamente em todos os diretóerios)
grep -A3 (after - mostra 3 linhas após a expressão, útil para analisar logs)
grep -B3 (before - mostra as 3 linhas que estão antes da expressão)

grep / fgrep / egrep

```
fgrep -> não usa expressão regular
egrep -> utiliza expressão regular

## sed
```
sed --help

sed '1,3 d' arquivo.txt
remove da linha 1 a 3

sed '/Marcio/d' arquivo.txt
remove a linha em que existe a string

cat arquivo.txt sed 's/Marcio/Paulo/'
substitui Marcio por Paulo

echo "Curso Linux Shell Script Linux" |  sed 's/Linux/Unix/g'
substitui todas as ocorrências usando "g" global.
```
## more
```
more arquivo.txt
enter -> segue a linha
barra espaço -> próxima página

less arquivo.txt

/certificate
busca a expresão

?certificate
busca de baixo pra cima

n -> próxima
N -> anterior
q -> sai da busca
```

## find
```
find ./ -name alunos.txt
find ./ -name *alunos*
find ./ -user marcio -name alunos.txt
find ./ -name alunos* -exec ls -l {} \;
```

## date
```
date --help
date +%H (hora)
date +%M (minuto)
date +%d/%m (dd/mm)
```
## seq
```
seq 20
seq 0 20

faz a sequencia até 20
seq 5 2 20
vai do 4 ao 20 de dois em dois
```

## expr
```
expr 5 + 2
expr 5 \* 2
echo 3 + 2 | bc 
```
## Comandos sequenciais
```
ls arquivo.txt ; echo linux
Executa na sequência, não importa se um dos comandos der erro.


ls arquivo.txt && echo linux
Executa o segundo comando apenas se  o primeiro foi bem sucedido.

ls arquivo.txt || echo linux
Executa o segundo commando apenas se o primeiro falhar.

$ (cd .. ; ls -l)
Executa o comando sem sair do diretorio atual abrindo um sub shell
```