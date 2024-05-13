<center>

# Compiladores 1

</center>

---

# Morse Regex

<!-- tabs:start -->

#### **Questão**

Morse Regex



Leonardo Machado



Preâmbulo



Você foi contratado pela Fundação Global dos Autômatos (FGA) para desenvolver uma máquina que interprete mensagens

em código Morse de um telégrafo. O código apresenta apenas os símbolos "." e "-". As mensagens são sempre números

pares maiores que 0. Para isso, precisamos de uma expressão regular que descreva essas mensagens. Abaixo há indicado

cada algarismo com sua representação em código Morse.



1 = .----

2 = ..---

3 = ...--

4 = ....-

5 = .....

6 = -....

7 = --...

8 = ---..

9 = ----.

0 = -----



Escreva em uma expressão regular em um arquivo

 

.grepe

 

que represente todos os números pares em códogo Morse.



Arquivo



O arquivo

 

.grepe

 

será o equivalente a execução do seguinte comando no terminal em ambiente Unix:



$ grep -o -E

 

'

regex

'

 

input



No qual

 

regex

 

é a expressão regular que resolve o problema e

 

input

 

é o arquivo com os casos a serem testados. Portanto,

o arquivo deve conter única e exclusivamente apenas uma linha, a qual deve apresentar a expressão regular

 

regex

 

para o

problema proposto.



Entrada



A entrada é composta por um caso de teste contendo N linhas (N

 

≥

 

0), em que cada linha é uma sequência de algarismos

representados em código Morse formando um número.



Saída



O programa deve imprimir as linhas em que são mostrados números pares.

1

Exemplos



Exemplo de entrada



..---...--

.---------

---..

.....



Saída para o exemplo acima



.---------

---..



Author: Leonardo Machado



2

#### **Código**

```regexp
^(.{5}*((-----)|(\.\.---)|(\.\.\.\.-)|(-\.\.\.\.)|(---\.\.)))$
```

<!-- tabs:end -->

