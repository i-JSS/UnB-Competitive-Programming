<center>

# Estrutura de Dados 2

</center>

---

# Árvores binárias de busca inserção

<!-- tabs:start -->

#### **Questão**

 Considere uma árvore binária de busca definida por células Sua tarefa nesse exercício é implementar a operação de inserção na numa árvore binária de busca com raiz r . Para tanto, você deve submeter um arquivo contendo apenas: 1. Os #include necessários para execução das instruções utilizadas no seu código. 2. A definição da struct no . 3. Uma função que insere o valor 𝑥 na árvore binária de busca. O protótipo desta função deve ser: Sua função de inserção deve garantir que chaves repetidas não sejam inseridas na árvore. 

Autor: John L. Gardenghi typedef struct no { int chave; struct no *esq, *dir; } no; no *inserir (no *r, int 

#### **Código**

```c
#include <stdio.h>
#include <stdlib.h>

typedef struct no {
    int dado;
    struct no *esq, *dir;
} no;

no *inserir (no *r, int x){
    if(r==NULL){
        no *newNo = malloc(sizeof(no));
        newNo->dado = x;
        newNo->dir = newNo->esq = NULL;
        return newNo;
    }
    if(x == r->dado) return r;
    if(x < r->dado) r->esq = inserir(r->esq, x);
    else r->dir = inserir(r->dir, x);
    return r;
}
```

<!-- tabs:end -->

