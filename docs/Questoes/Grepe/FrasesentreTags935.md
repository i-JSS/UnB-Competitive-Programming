<center>

# Compiladores 1

</center>

---

# Frases entre Tags

<!-- tabs:start -->

#### **Questão**

 Bruno Ribeiro 

**Preâmbulo**

 No contexto da programação, uma "tag" geralmente se refere a um marcador ou rótulo que é utilizado para identificar e organizar elementos em um documento ou código-fonte. As tags são amplamente utilizadas em várias linguagens de marcação, bem como em outras áreas da programação. Para este exercício, consideraremos como tags quaisquer palavras que comecem e terminem uma sentença. Por palavras, entendemos qualquer sequência de caracteres alfanuméricos. Sua missão neste exercício é imprimir todas as linhas que sejam iniciadas e concluídas com um par de tags, ou seja, que tenham a mesma palavra como inicial e final. Todavia, caso haja outra ocorrência desta palavra no intermédio da frase, a tag é inválida. Para isso, escreva uma expressão regular ( RegEx ) em um arquivo .grepe que identifique quais strings são correspondentes ao requerido. 

**Arquivo**

 O arquivo .grepe será o equivalente a execução do seguinte comando no terminal em ambiente Unix: $ grep -P ' regex ' input No qual regex é a expressão regular que resolve o problema e input é o arquivo com os casos a serem testados. Portanto, o arquivo deve conter única e exclusivamente apenas uma linha, a qual deve apresentar a expressão regular regex para o problema proposto. 

**Entrada**

 A entrada é composta por um único caso de teste, contendo N ( N > 0 ) linhas a serem analisadas. 

**Saída**

 Seu programa deverá imprimir as D ( D ≥ 0 ) linha encontradas em que hajam de um par de tags, propriamente como o definido. Exemplos 

**Exemplo de entrada**

 <teste> Isso é um teste. <teste> Deu certo? Deu e agora? 01 00 01 oi Deu certo? Deu 

**Exemplo de saída**

 Deu certo? Deu 01 00 01 

Autor: Bruno Ribeiro 

#### **Código**

```grepe
^(\w+)(?:(?!\1).)*\1$

```

<!-- tabs:end -->

