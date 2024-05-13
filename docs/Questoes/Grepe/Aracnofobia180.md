<center>

# Compiladores 1

</center>

---

# Aracnofobia

<!-- tabs:start -->

#### **Questão**

Aracnofobia



Leonardo Machado



Preâmbulo



Maria é uma criança que sofre de aracnofobia. Sua fobia é tão intensa que até mesmo a palavra aranha gera desconforto.

O problema é que qualquer texto que forme a palavra aranha na sequência de suas letras, sejam elas maiúsculas ou

minúsculas, também causa desconforto. Sua missão é elaborar uma expressão regular que identifique frases que formam a

palavra aranha na sua sequência de letras.



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



A entrada é composta por N casos de teste (N

 

≥

 

0), em que cada caso é uma frase.



Saída



A saída deve imprimir as frases que formam a palavra aranha na sua sequência de caracteres.



Exemplos



Exemplo de entrada



Ara

ras

N

aoVoamNaC

h

uv

a



BomDiaSenhora



A

go

raN

ao

Ha

Volta

EsqueciMeuGuardaChuva



Saída para o exemplo acima



ArarasNaoVoamNaChuva

AgoraNaoHaVolta



Author: Leonardo Machado



1

#### **Código**

```regexp
^(.*[aA].*[rR].*[aA].*[nN].*[hH].*[aA].*)$
```

<!-- tabs:end -->

