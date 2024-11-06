<center>

# Estrutura de Dados 1

</center>

---

# Listas encadeadas inserção

<!-- tabs:start -->

#### **Questão**

 Considere uma lista encadeada com nó cabeça le definida por células typedef struct celula { int dado ; struct celula * prox ; } celula ; Sua tarefa nesse exercício é implementar a operação de inserção na lista encadeada encabeçada por le . Para tanto, você deve submeter um arquivo contendo apenas: 1. Os #include necessários para execução das instruções utilizadas no seu código. 2. A definição da struct celula . 3. Uma função que insere um elemento x no início da lista encadeada, cujo protótipo deve ser: void insere_inicio ( celula * le , int x ); 4. Uma função que insere um elemento x imediatamente antes da primeira ocorrência de um elemento y na lista encadeada. Se y não estiver na lista encadeada, x deve ser inserido ao final. O protótipo dessa função deve ser void insere_antes ( celula * le , int x , int y ); 

Autor: John L. Gardenghi 

#### **Código**

```c
#include <stdio.h>
#include <stdlib.h>

typedef struct celula {
    int dado;
    struct celula *prox;
} celula;

void insere_inicio (celula *lista, int x){
    celula *cel = malloc(sizeof(celula));
    cel->dado = x;
    cel->prox = lista->prox;
    lista->prox = cel;
}

void insere_antes(celula *lista, int x, int y) {
    if (lista == NULL) return;

    celula *cel = malloc(sizeof(celula));
    cel->dado = x;
    while (lista->prox != NULL) {
        if (lista->prox->dado == y) {
            celula *temp = lista->prox;
            lista->prox = cel;
            cel->prox = temp;
            return;
        }
        lista = lista->prox;
    }
    cel->prox = NULL;
    lista->prox = cel;
}
```

<!-- tabs:end -->

