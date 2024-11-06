<center>

# Estrutura de Dados 1

</center>

---

# Listas encadeadas busca

<!-- tabs:start -->

#### **Questão**

 Considere uma lista encadeada com nó cabeça le definida por células typedef struct celula { int dado ; struct celula * prox ; } celula ; Sua tarefa nesse exercício é implementar a operação de busca na lista encadeada encabeçada por le . Para tanto, você deve submeter um arquivo contendo apenas: 1. Os #include necessários para execução das instruções utilizadas no seu código. 2. A definição da struct celula . 3. Uma função que procura pela primeira ocorrência do elemento x na lista encadeada e devolve um ponteiro para a célula que o contém. O protótipo desta função deve ser: celula * busca ( celula * le , int x ); 4. Uma função que faz o mesmo que o item 3 , mas recursiva , com protótipo celula * busca_rec ( celula * le , int x ); 

Autor: John L. Gardenghi 

#### **Código**

```c
#include <stdio.h>

typedef struct celula {
    int dado;
    struct celula *prox;
} celula;

celula *busca(celula *le, int x) {
    celula *atual = le->prox;
    while (atual != NULL) {
        if (atual->dado == x) return atual;
        atual = atual->prox;
    }
    return NULL;
}

celula *busca_rec(celula *le, int x) {
    if (le == NULL) return NULL;

    if (le->dado == x) return le;

    return busca_rec(le->prox, x);
}
```

<!-- tabs:end -->

