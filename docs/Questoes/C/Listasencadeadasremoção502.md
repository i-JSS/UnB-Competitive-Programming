<center>

# Estrutura de Dados 2

</center>

---

# Listas encadeadas remoção

<!-- tabs:start -->

#### **Questão**

 Considere uma lista encadeada com nó cabeça le definida por células Sua tarefa nesse exercício é implementar a operação de remoção da lista encadeada encabeçada por le . Para tanto, você deve submeter um arquivo contendo apenas: 1. Os #include necessários para execução das instruções utilizadas no seu código. 2. A definição da struct celula . 3. Uma função que remove o elemento imediatamente seguinte do ponteiro 𝑝 , com protótipo Sua função deve ser capaz de lidar com o(s) caso(s) em que não seja possível remover o elemento seguinte a 𝑝 . 4. Uma função que remove a primeira ocorrência de 𝑥 da lista encadeada, cujo protótipo é 4. Uma função que remove todas as ocorrências de 𝑥 da lista encadeada, cujo protótipo é 

Autor: John L. Gardenghi typedef struct celula { int dado; struct celula *prox; } celula; int remove_depois (celula *p); void remove_elemento (celula *le, int x); void remove_todos_elementos (celula *le, int 

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

