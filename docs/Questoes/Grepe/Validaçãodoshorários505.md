<center>

# Compiladores 1

</center>

---

# Validação dos horários

<!-- tabs:start -->

#### **Questão**

Validação dos horários



Igor Penha



Preâmbulo



Bem-vindo!

Na cidade de buglândia, um lugar conhecido por sua tranquilidade, um incidente inusitado ocorreu: o relógio digital da

praça central, que por décadas foi a referência para toda a população, subitamente começou a exibir horários malucos. Ao

invés dos tradicionais "12:00", "13:45" e "17:30", os números digitais piscavam de forma caótica, mostrando sequências

como "99:99", "25:73" e até mesmo "banana:abacaxi".

Sua missão é implementar uma expressão regular, que imprima apenas os horários que estiverem na forma HH:MM. Para

que, assim, os cidadãos possam retomar suas rotinas diárias com a confiança de saber exatamente que horas são.

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

) linhas.



Saída



Seu programa deverá imprimir as

 

E

 

(

E

 

≥

 

0

) linhas, que contenham os horários no formato desejável.



Exemplos



Exemplo de entrada



00:29

0029

15:300

20:07

11:09 abs



Saída para o exemplo acima



00:29

20:07



Author: Igor Penha



1

#### **Código**

```regexp
^((([0-1][0-9])|([2][0-3]))[:][0-5][0-9])$
```

<!-- tabs:end -->

