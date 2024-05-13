<center>

# Compiladores 1

</center>

---

# Problema 101

<!-- tabs:start -->

#### **Questão**

Problema 101



Leonardo Machado



Preâmbulo



Uma máquina conectada na rede recebe vários bits a todo momento. Porém quando essa máquina recebe a subsequência

101 dentro de uma sequência de bits ela desliga. Sua missão é elaborar uma regex que elabore qualquer sequência de zero

e um que não possua a subsequência 101.



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



A entrada é composta por vários casos de teste compostos por sequências de zero e um.



Saída



A saída deve imprimir as sequências que não possuem a subsequência 101.



Exemplos



Exemplo de entrada



1111111000000011111

000000111111100000010

101

1010101010101010101010



Saída para o exemplo acima



1111111000000011111

000000111111100000010



Author: Leonardo Machado



1

#### **Código**

```regexp
^(0+|(1+(0{2}|(0$)|$)))*$
```

<!-- tabs:end -->

