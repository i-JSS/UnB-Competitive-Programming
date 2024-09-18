<center>

# Compiladores 1

</center>

---

# Olá no Mundo das RegEx 2

<!-- tabs:start -->

#### **Questão**

 Bruno Ribeiro 

**Preâmbulo**

 Olá! Você está iniciando no mundo da correção automática com exercícios de expressões regulares. Este é um momento bastante delicado e por isso você deve prestar atenção em todos os detalhes de um problema. A primeira coisa que devemos perceber é que sempre que se fala em linha devemos entender que a linha termina com o caractere de quebra de linha o \n, também é interessante saber que os sistemas de correção automática executam um sistema UNIX, em geral Linux e por isso a quebra de linha é composta unicamente pelo caractere \n, os sistemas (r)Windows utilizam o conceito \r\n. Sua missão neste exercício é imprimir todas as ocorrências da string Olá Mundo! , independentemente de cada letra ser capitalizada, ter ou não o marcador "!", ou conter acentos. Para isso, escreva uma expressão regular ( RegEx ) em um arquivo .grepe que identifique quais strings são correspondentes ao requerido. 

**Arquivo**

 O arquivo .grepe será o equivalente a execução do seguinte comando no terminal em ambiente Unix: $ grep -o -E ' regex ' input No qual regex é a expressão regular que resolve o problema e input é o arquivo com os casos a serem testados. Portanto, o arquivo deve conter única e exclusivamente apenas uma linha, a qual deve apresentar a expressão regular regex para o problema proposto. 

**Entrada**

 A entrada é composta por um único caso de teste, contendo N ( N > 0 ) linhas. As linhas podem D ( D ≥ 0 ) possíveis strings a serem analisadas. 

**Saída**

 Seu programa deverá imprimir as E ( E ≥ 0 ) strings Olá Mundo! encontradas de cada caso de teste. Exemplos 

**Exemplo de entrada**

 Bruno Ribeiro disse Olá Mundo Bruno Ribas o respondeu com ola mundo 

**Exemplo de saída**

 Olá Mundo ola mundo 

**Exemplo de entrada**

 Os autômatos dizem: Ola MundO! 



**Exemplo de saída**

 Ola MundO! 

Autor: Bruno Ribeiro 

#### **Código**

```grepe
[Oo][lL][aáÁAÃã][ ][Mm][Uu][Nn][Dd][oOÓó][!.]?


```

<!-- tabs:end -->

