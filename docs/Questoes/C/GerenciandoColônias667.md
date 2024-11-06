<center>

# Estrutura de Dados 2

</center>

---

# Gerenciando Colônias

<!-- tabs:start -->

#### **Questão**

 Para manter tudo organizado e unir todas as colônias, a associação Formiga Guiando Ações (FGA) decidiu criar um sistema único para todas as formigas do planeta. No começo, nem todas as colônias vão aderir ao sistema. Mas cada colônia é identificada pela sua localização em relação à central da associação, medida em decímetros. Se duas colônias estiverem à mesma distância, são consideradas iguais. O principal objetivo é gerenciar os mantimentos para o inverno, permitindo que cada formigueiro tenha apenas um estoque de cada tipo de comida. Se um formigueiro receber uma tentativa de envio de alimento duplicado pela central, o programa deve sinalizar e evitar a duplicação. 

**Entrada**

 A entrada é composta por um único caso de teste, possuindo uma quantidade incerta de linhas que terminam somente com EOF . Cada linha do caso de teste possui um inteiro 𝐶 ( 1 ≤ 𝐶 ≤ 10 9 ), seguido por uma palavra 𝑃 ( 1 ≤ | 𝑃 | ≤ 10 ), sendo a identificação da colônia, e o alimento candidato a ser entregue, respectivamente. Apesar do número de identificação da colônia assumir valores grandes, é garantido que há no máximo 2 20 formigueiros registrados na central. 

**Saída**

 A saída é composta por um número variável de linhas. Para cada tentativa de entrega de um alimento, caso o formigueiro já possua um estoque deste tipo, imprima o número de identificação do formigueiro. Em um caso de teste, há pelo menos uma tentativa de entrega duplicada. Exemplos 

**Exemplo de entrada**

 2 arroz 3943824 feijao 5 batata 2 folha 2 arroz 5 arroz 5 batata 

**Exemplo de saída**

 2 

Explicação: A colônia de identificação 2 já possui um estoque de arroz. Para a colônia 5 , um estoque de batata já havia sido entregue. 

#### **Código**

```c
#include <stdio.h>
#include <stdlib.h>
#include <string.h>
#define MAX ((1ULL << 21))
typedef struct No {
    long id;
    char *chave;
    struct No *esq, *dir;
} No;
No **HASH;
No *insere(No *raiz, char *dado, long id) {
    if (raiz == NULL) {
        No *newNo = malloc(sizeof(No));
        newNo->chave = malloc(sizeof (char)*12);
        newNo->chave = strdup(dado);
        newNo->id = id;
        newNo->esq = newNo->dir = NULL;
        return newNo;
    }
    int cmp = strcmp(raiz->chave, dado);
    if(cmp == 0){
        printf("%ld\n", id);
        return raiz;
    }
    else if(cmp < 0) raiz->esq = insere(raiz->esq, dado, id);
    else raiz->dir = insere(raiz->dir, dado, id);
    return raiz;
}
int main() {
    HASH = calloc(MAX, sizeof(No*));
    long num;
    char palavra[12];
    while(scanf("%ld %s", &num, palavra) != EOF){
        unsigned long long indice = (num)%MAX;
        No *cabeca = HASH[indice];
        while(cabeca!=NULL && cabeca->id != num) {
            indice = (indice+1)%MAX;
            cabeca = HASH[indice];
        }
        HASH[indice] = insere(cabeca, palavra, num);
    }
    return 0;
}

```

<!-- tabs:end -->

