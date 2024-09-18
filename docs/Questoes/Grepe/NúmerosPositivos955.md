<center>

# Compiladores 1

</center>

---

# Números Positivos

<!-- tabs:start -->

#### **Questão**

 Igor Penha 

**Preâmbulo**

 Olá! Você está iniciando seu treinamento com expressões regulares. Este é um momento bastante delicado e por isso é necessário prestar atenção em todos os detalhes de um problema. Sua missão neste exercício é implementar uma regex que case com todas as linhas que contenham somente 1 número positivo. Para isso, escreva uma expressão regular ( RegEx ) em um arquivo .grepe que identifique quais strings são correspondentes ao requerido. 

**Arquivo**

 O arquivo .grepe será o equivalente a execução do seguinte comando no terminal em ambiente Unix: $ grep -E ' regex ' input No qual regex é a expressão regular que resolve o problema e input é o arquivo com os casos a serem testados. Portanto, o arquivo deve conter única e exclusivamente apenas uma linha, a qual deve apresentar a expressão regular regex para o problema proposto. 

**Entrada**

 A entrada é composta por um único caso de teste, contendo N ( N > 0 ) linhas. As linhas podem possuir D ( D ≥ 0 ) possíveis strings. 

**Saída**

 Seu programa deverá imprimir as E ( E ≥ 0 ) linhas que são compostas por somente 1 número positivo. Exemplos 

**Exemplo de entrada**

 0 12345 12ab346 10 20 Ola Mundo3 7 

**Exemplo de saída**

 0 12345 7 

**Exemplo de entrada**

 20 25 50 75 

5 15 papel 3 99 pizza 

**Exemplo de saída**

 20 99 

Autor: Igor Penha 

#### **Código**

```grepe
^([0-9]+)$


```

<!-- tabs:end -->

