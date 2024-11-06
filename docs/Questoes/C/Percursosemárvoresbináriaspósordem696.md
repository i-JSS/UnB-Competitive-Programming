<center>

# Estrutura de Dados 2

</center>

---

# Percursos em árvores binárias: pós ordem

<!-- tabs:start -->

#### **Questão**

 ordem Considere uma árvore binária com nós representados por Sua tarefa nesse exercício é implementar o percurso pós-ordem , mas sem usar recursão. Para tanto, você deve submeter um arquivo contendo: 1. Os #include necessários para execução das instruções utilizadas no seu código. 2. A definição da struct no . 3. Uma função não recursiva que recebe uma árvore binária enraizada por raiz e imprima o valor de cada nó, separado por espaço, gerado a partir do percurso pós-ordem na árvore dada. 4. As funções auxiliares que julgar necessárias. Exemplo Considere a árvore dada por Sua função deve imprimir, para esta árvore: 3 4 8 5 9 1 6 7 2 

Autor: John L. Gardenghi typedef struct no { int dado; struct no *esq, *dir; } no; void 

#### **Código**

```c
#include <stdio.h>
#include <stdlib.h>

typedef struct no {
    int dado;
    struct no *esq, *dir;
} no;

void pos_ordem(no *raiz){
    if(raiz != NULL){
        pos_ordem(raiz->esq);
        pos_ordem(raiz->dir);
        printf("%d ", raiz->dado);
    }
}
```

<!-- tabs:end -->

