<center>

# Estrutura de Dados 2

</center>

---

# Listas encadeadas inserção

<!-- tabs:start -->

#### **Questão**

 Considere uma lista encadeada com nó cabeça le definida por células Sua tarefa nesse exercício é implementar a operação de inserção na lista encadeada encabeçada por le . Para tanto, você deve submeter um arquivo contendo apenas: 1. Os #include necessários para execução das instruções utilizadas no seu código. 2. A definição da struct celula . 3. Uma função que insere um elemento 𝑥 no início da lista encadeada, cujo protótipo deve ser: 4. Uma função que insere um elemento 𝑥 imediatamente antes da primeira ocorrência de um elemento 𝑦 na lista encadeada. Se 𝑦 não estiver na lista encadeada, 𝑥 deve ser inserido ao final. O protótipo dessa função deve ser 

Autor: John L. Gardenghi typedef struct celula { int dado; struct celula *prox; } celula; void insere_inicio (celula *le, int x); void insere_antes (celula *le, int x, int 

#### **Código**

```c

#include <stdio.h>
#include <stdlib.h>

typedef struct celula {
    int dado;
    struct celula *prox;
} celula;

void insere_inicio (celula *le, int x){
    celula *cel = malloc(sizeof(celula));
    cel->dado = x;
    cel->prox = le->prox;
    le->prox = cel;
}

void insere_antes(celula *le, int x, int y) {
    if (le == NULL) return;

    celula *cel = malloc(sizeof(celula));
    cel->dado = x;
    while (le->prox != NULL) {
        if (le->prox->dado == y) {
            celula *temp = le->prox;
            le->prox = cel;
            cel->prox = temp;
            return;
        }
        le = le->prox;
    }
    cel->prox = NULL;
    le->prox = cel;
}

```

<!-- tabs:end -->

