<center>

# Compiladores 1

</center>

---

# Desmatriculados

<!-- tabs:start -->

#### **Questão**

 Leonardo Machado 

**Preâmbulo**

 O professor da disciplina de Compiladores se deparou com um grande problema no primeiro dia de aula. O Sistema Inteligente de Gestão de Alunos e Aulas (SIGAA) retirou da turma todos os alunos que ingressaram na universidade no ano de 2021. Para recuperá-los, precisamos de uma expressão regular que descreva suas matrículas. Os números de matrícula da universidade podem ter uma quantidade indefinida de algarismos, porém, sabemos que os alunos que ingressaram em 2021 possuem a sequência ' 2021 ' dentro de seu número de matrícula, podendo estar em qualquer posição no número. 

**Arquivo**

 O arquivo .grepe será o equivalente a execução do seguinte comando no terminal em ambiente Unix: $ grep -o -E ' regex ' input No qual regex é a expressão regular que resolve o problema e input é o arquivo com os casos a serem testados. Portanto, o arquivo deve conter única e exclusivamente apenas uma linha, a qual deve apresentar a expressão regular regex para o problema proposto. 

**Entrada**

 A entrada é composta por um caso de teste contendo N linhas (N ≥ 0), em que cada linha é um número de matrícula. 

**Saída**

 A saída deve imprimir os números de matrícula referentes aos alunos do ano 2021. Exemplos Exemplo de entrada 123456789 000000000020210000000000 2021123456789 22222222000000000002222222221111 

**Saída**

 para o exemplo acima 000000000020210000000000 2021123456789 

Autor: Leonardo Machado 

#### **Código**

```grepe
^(.*2021.*)$
```

<!-- tabs:end -->

