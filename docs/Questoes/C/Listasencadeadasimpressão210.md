<center>

# Estrutura de Dados 2

</center>

---

# Listas encadeadas impressão

<!-- tabs:start -->

#### **Questão**

 Considere uma lista encadeada com nó cabeça le definida por células Sua tarefa nesse exercício é implementar a operação de impressão da lista encadeada encabeçada por le . Para tanto, você deve submeter um arquivo contendo apenas: 1. Os #include necessários para execução das instruções utilizadas no seu código. 2. A definição da struct celula . 3. Duas funções (uma iterativa e outra recursiva) que imprimem a lista encadeada. Os protótipos devem ser Exemplos Se a lista estiver vazia, sua função deve imprimir NULL Se não estiver, os elementos devem ser impressos antes do NULL e separados por -> , da seguinte forma: suponha uma lista com os elementos 1, 2 e 3: 1 -> 2 -> 3 -> NULL Atenção : Não deve haver espaço depois do NULL . 

Autor: John L. Gardenghi typedef struct celula { int dado; struct celula *prox; } celula; void imprime (celula *le); void 

#### **Código**

```c

#include <stdio.h>

typedef struct celula {
    int dado;
    struct celula *prox;
} celula;

void imprime(celula *le) {
    if(le == NULL){
        printf("NULL\n");
    }
    else{
        while(le != NULL){
            if(le->dado){
                printf("%d", le->dado);
                printf(" -> ");
            }
            le = le->prox;
        }
        printf("NULL\n");
    }
}

void imprime_rec(celula *le){
    if(le != NULL){
        if(le->dado){
            printf("%d", le->dado);
            printf(" -> ");
        }
        imprime_rec(le->prox);
    }
    else printf("NULL\n");
}

```

<!-- tabs:end -->

