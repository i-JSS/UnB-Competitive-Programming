<center>

# Compiladores 1

</center>

---

# Pares com RegEx

<!-- tabs:start -->

#### **Questão**

 Bruno Ribeiro 

**Preâmbulo**

 Pare! Sua missão neste exercício é imprimir todas as linhas com ocorrências de pelo menos um número par. Para isso, escreva uma expressão regular ( RegEx ) em um arquivo .grepe que identifique quais strings são correspondentes ao requerido. 

**Arquivo**

 O arquivo .grepe será o equivalente a execução do seguinte comando no terminal em ambiente Unix: $ grep -E ' regex ' input No qual regex é a expressão regular que resolve o problema e input é o arquivo com os casos a serem testados. Portanto, o arquivo deve conter única e exclusivamente apenas uma linha, a qual deve apresentar a expressão regular regex para o problema proposto. 

**Entrada**

 A entrada é composta por um único caso de teste, contendo N ( N > 0 ) linhas a serem analisadas. 

**Saída**

 Seu programa deverá imprimir as D ( D ≥ 0 ) linha encontradas em que hajam pelo menos uma ocorrência de número par. Exemplos Exemplo de entrada Vamos contar até 10? Só sei contar até 5. 

**Saída**

 para o exemplo acima Vamos contar até 10? Exemplo de entrada Vamos contar até 21? Só sei contar até 10. 

**Saída**

 para o exemplo acima Só sei contar até 10. 

Autor: Bruno Ribeiro 

#### **Código**

```grepe
^((.*[0-9]*[02468][^0-9]+.*)||.*[0-9]*[02468])$
```

<!-- tabs:end -->

