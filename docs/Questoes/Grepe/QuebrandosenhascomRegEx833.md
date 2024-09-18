<center>

# Compiladores 1

</center>

---

# Quebrando senhas com RegEx

<!-- tabs:start -->

#### **Questão**

 Bruno Ribeiro 

**Preâmbulo**

 Há muito tempo, em uma terra distante, existe um reino chamado Autômato, onde reina o Rei Determinístico. Este reino é protegido por um grande portão, guardado por um guardião chamado Andarilho da Fronteira Determinística (AFD). O AFD tem uma função crucial: ele só permite a passagem de viajantes que conheçam a senha secreta, que é uma sequência específica de símbolos. Essa senha é tão complexa que ninguém consegue memorizá-la facilmente. Por muitos anos, os viajantes que desejavam entrar no reino de Autômato precisavam aprender a sequência de símbolos, uma a uma, para poderem passar pelo portão. Mas um dia, um jovem chamado Bruno, determinado a entrar pelos portões de Autômato, pediu tua ajuda para quebrar a senha gerada pelo AFD. Sua missão neste exercício é escrever a expressão regular ( RegEx ), que seja equivalente a senha do AFD, em um arquivo .grepe . 

**Arquivo**

 O arquivo .grepe será o equivalente a execução do seguinte comando no terminal em ambiente Unix: $ grep -E ' regex ' input No qual regex é a expressão regular que resolve o problema e input é o arquivo com os casos a serem testados. Portanto, o arquivo deve conter única e exclusivamente apenas uma linha, a qual deve apresentar a expressão regular regex para o problema proposto. 

**Entrada**

 Figure 1: Representação gráfica da senha gerada por AFD. 

Autor: Bruno Ribeiro 

#### **Código**

```grepe
^((b(b{2}*)(br|c)|r)(rb(b{2}*)(br|c)|(rr|b))*(rb(b{2}*))?|(b(b{2}*))?)$

```

<!-- tabs:end -->

