<center>

# Compiladores 1

</center>

---

# Fantática máquina de palavras

<!-- tabs:start -->

#### **Questão**

Fantática máquina de palavras



Igor Penha



Preâmbulo



Seja bem-vindo a fantástica fabrica de palavras onde as letras dançam e os sons se transformam em significados!

Essa fábrica é responsável pela geração de palavras que o mundo todo utliza todos os dias. No entanto, um dia, um

pequeno defeito foi descoberto. Os engenheiros, especialistas em mecânica de linguagem, perceberam que algo estava errado

com a máquina que gerava palavras contendo a letra

 

'

a

'

. Infelizmente, nenhum dos engenheiros tinham conhecimento em

expressões regulares, uma ferramenta poderosa para manipulação de texto.

Com a fábrica em pausa, os engenheiros humildemente buscaram ajuda externa e chegaram até você. Agora, com sua

experiência e conhecimento, você se torna parte dessa jornada para salvar a Fábrica de Palavras e trazer de volta a

harmonia ao mundo da linguagem.

É preciso que você implemente uma expressão regular (

RegEx

) que imprima todas as palavras que possuam a letra

 

'

a

'

 

em

qualquer capitalização para que, assim, os engenheiros possam estudar mais afundo sobre o problema da máquina!

Dica de ouro dos engenheiros:



•

 

Não esqueça que a sua expresssão regular com a solução deve ver ser entregue em um arquivo

 

.grepe

 

que identifique

quais strings são correspondentes ao requerido.



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



A entrada é composta por um único caso de teste, contendo

 

N

 

(

N >

 

0

) linhas.

 

As linhas podem conter

 

D

 

(

D

 

≥

 

0

)

possíveis strings a serem analisadas.



Saída



Seu programa deverá imprimir as

 

E

 

(

E

 

≥

 

0

) palavras que possuam ao menos uma letra

 

'

a

'

.



Exemplos



Exemplo de entrada



treinando regex

compiladores eh irado

Estou sem rede, logo sem peixe

Fantastica fabrica de palavras



Saída para o exemplo acima



treinando

compiladores

irado



1

Fantastica

fabrica

palavras



Author: Igor Penha



2

#### **Código**

```regexp
\<[^ \>\<]*[aA][^ \>\<]*\>
```

<!-- tabs:end -->

