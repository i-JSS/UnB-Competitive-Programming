<center>

# Compiladores 1

</center>

---

# Palavras Censuradas

<!-- tabs:start -->

#### **Questão**

 Bruno Ribeiro 

**Preâmbulo**

 Em uma cidadezinha tranquila havia uma biblioteca antiga e misteriosa. Os moradores locais frequentavam-na regularmente em busca de conhecimento e entretenimento. Bruno, um entusiasta da linguagem e curioso por natureza, enquanto folheava um livro empoeirado, encontrou um estranho trecho que despertou sua curiosidade. Palavras pareciam ter sido censuradas, substituídas por uma sequência de "XXX". Intrigado, Bruno decidiu investigar. Com sua mente analítica, percebeu que as palavras censuradas podiam ter sido aplicadas em qualquer lugar: do início, do meio ou do final das palavras. Animado com a descoberta, Bruno pediu a sua ajuda para vasculhar outros livros na biblioteca, procurando por mais ocorrências dessas palavras ocultas. Sua missão é escrever um expressão regular ( RegEx ) em um arquivo .grepe para imprimir todas as ocorrências das palavras que foram censuradas, ou sejam palavras que possuam "XXX" no início, meio ou final da palavra. 

**Arquivo**

 O arquivo .grepe será o equivalente a execução do seguinte comando no terminal em ambiente Unix: $ grep -o -E ' regex ' input No qual regex é a expressão regular que resolve o problema e input é o arquivo com os casos a serem testados. Portanto, o arquivo deve conter única e exclusivamente apenas uma linha, a qual deve apresentar a expressão regular regex para o problema proposto. 

**Entrada**

 A entrada é composta por um único caso de teste, contendo N ( N > 0 ) linhas. As linhas podem D ( D ≥ 0 ) possíveis palavras censuradas. 

**Saída**

 Seu programa deverá imprimir E ( E ≥ 0 ) palavras encontradas dentre as D palavras das N linhas. Exemplos 

**Exemplo de entrada**

 O XXXfeito cXXXrou um caXXX. 

**Exemplo de saída**

 XXXfeito cXXXrou caXXX 

Autor: Bruno Ribeiro 

#### **Código**

```grepe
\<[^ \>\<]*[X][^ \>\<]*\>


```

<!-- tabs:end -->

