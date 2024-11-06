<center>

# Estrutura de Dados 2

</center>

---

# Percursos em árvores binárias: pré ordem

<!-- tabs:start -->

#### **Questão**

 ordem Considere uma árvore binária com nós representados por Sua tarefa nesse exercício é implementar o percurso pré-ordem , mas sem usar recursão. Para tanto, você deve submeter um arquivo contendo: 1. Os #include necessários para execução das instruções utilizadas no seu código. 2. A definição da struct no . 3. Uma função não recursiva que recebe uma árvore binária enraizada por raiz e imprima o valor de cada nó, separado por espaço, gerado a partir do percurso pré-ordem na árvore dada. 4. As funções auxiliares que julgar necessárias. Exemplo Considere a árvore dada por Sua função deve imprimir, para esta árvore: 2 5 3 8 4 7 1 9 6 

Autor: John L. Gardenghi typedef struct no { int dado; struct no *esq, *dir; } no; void 

#### **Código**

```c
#include <stdio.h>
#include <stdlib.h>

typedef struct no {
    int dado;
    struct no *esq, *dir;
} no;

void pre_ordem (no *raiz){
    if(raiz != NULL){
        printf("%d ", raiz->dado);
        pre_ordem(raiz->esq);
        pre_ordem(raiz->dir);
    }
}
```

<!-- tabs:end -->

