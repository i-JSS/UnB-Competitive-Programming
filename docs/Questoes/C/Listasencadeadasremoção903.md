<center>

# Estrutura de Dados 1

</center>

---

# Listas encadeadas remoção

<!-- tabs:start -->

#### **Questão**

 Considere uma lista encadeada com nó cabeça le definida por células typedef struct celula { int dado ; struct celula * prox ; } celula ; Sua tarefa nesse exercício é implementar a operação de remoção da lista encadeada encabeçada por le . Para tanto, você deve submeter um arquivo contendo apenas: 1. Os #include necessários para execução das instruções utilizadas no seu código. 2. A definição da struct celula . 3. Uma função que remove o elemento imediatamente seguinte do ponteiro p , com protótipo int remove_depois ( celula * p ); Sua função deve ser capaz de lidar com o(s) caso(s) em que não seja possível remover o elemento seguinte a p . 4. Uma função que remove a primeira ocorrência de x da lista encadeada, cujo protótipo é void remove_elemento ( celula * le , int x ); 4. Uma função que remove todas as ocorrências de x da lista encadeada, cujo protótipo é void remove_todos_elementos ( celula * le , int x ); 

Autor: John L. Gardenghi 

#### **Código**

```c
#include <stdio.h>
#include <stdlib.h>

typedef struct celula {
    int dado;
    struct celula *prox;
} celula;

int remove_depois(celula *p) {
    if (p == NULL || p->prox == NULL) {
        return 0;
    }

    celula *temp = p->prox;
    p->prox = temp->prox;
    free(temp);
    return 1;
}

void remove_elemento(celula *le, int x) {
    while (le != NULL && le->prox != NULL) {
        if (le->prox->dado == x) {
            celula *temp = le->prox;
            le->prox = temp->prox;
            free(temp);
            return;
        }
        le = le->prox;
    }
}

void remove_todos_elementos(celula *le, int x) {
    celula *temp;
    while (le != NULL && le->prox != NULL) {
        if (le->prox->dado == x) {
            temp = le->prox;
            le->prox = temp->prox;
            free(temp);
        } else {
            le = le->prox;
        }
    }
}


```

<!-- tabs:end -->

