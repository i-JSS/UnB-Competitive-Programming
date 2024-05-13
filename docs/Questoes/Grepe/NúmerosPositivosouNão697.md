<center>

# Compiladores 1

</center>

---

# Números Positivos ou Não

<!-- tabs:start -->

#### **Questão**

Números Positivos ou Não



Igor Penha



Preâmbulo



Olá!

Você está iniciando seu treinamento com expressões regulares. Este é um momento bastante delicado e por isso é necessário

prestar atenção em todos os detalhes de um problema.

Sua missão neste exercício é implementar uma expressão regular que case com todas as linhas que contenham somente 1

número, seja ele positivo ou não.

Lembre-se o 0 é considerado apenas como um número positivo.

Para isso, escreva uma expressão regular (

RegEx

) em um arquivo

 

.grepe

 

que identifique quais strings são correspondentes

ao requerido.



Arquivo



O arquivo

 

.grepe

 

será o equivalente a execução do seguinte comando no terminal em ambiente Unix:



$ grep -E

 

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



A entrada é composta por um único caso de teste, contendo

 

N

 

(

N >

 

0

) linhas. As linhas podem possuir

 

D

 

(

D

 

≥

 

0

)

possíveis strings.



Saída



Seu programa deverá imprimir as

 

E

 

(

E

 

≥

 

0

) linhas que sejam compostas por somente 1 número.



Exemplos



Exemplo de entrada



0

12345

12a346

-1

Olá Mundo3



Saída para o exemplo acima



0

-1

12345



Exemplo de entrada



1

223 421 12

800

12abc

22

44 bicicletas

-21

-091



Saída para o exemplo acima



800

22

-21

-091



Author: Igor Penha



2

#### **Código**

```grepe
^(0|[-]?[0]*[1-9]+[0-9]*)$
```

<!-- tabs:end -->

