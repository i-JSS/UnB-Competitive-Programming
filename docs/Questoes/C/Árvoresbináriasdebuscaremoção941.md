<center>

# Estrutura de Dados 2

</center>

---

# Árvores binárias de busca remoção

<!-- tabs:start -->

#### **Questão**

 Considere uma árvore binária de busca definida por células Sua tarefa nesse exercício é implementar a operação de remoção na numa árvore binária de busca com raiz r . Para tanto, você deve submeter um arquivo contendo apenas: 1. Os #include necessários para execução das instruções utilizadas no seu código. 2. A definição da struct no . 3. Uma função insere o valor 𝑥 na árvore binária de busca. O protótipo desta função deve ser: Sua função de remoção deve usar o antecessor no processo. Ele retorna a nova raiz da árvore e NULL , caso a chave a ser removida não esteja na árvore. 

Autor: John L. Gardenghi typedef struct no { int chave; struct no *esq, *dir; } no; no *remover (no *r, int 

#### **Código**

```c
#include <stdlib.h>

typedef struct no {
    int dado;
    struct no *esq, *dir;
} no;

no* remover(no *r, int x){
    if(r == NULL) return NULL;
    if(x < r->dado) r->esq = remover(r->esq, x);
    else if(x > r->dado) r->dir = remover(r->dir, x);
    else{
        if(r->esq == NULL && r->dir == NULL) return NULL;
        else if(r->esq == NULL) return r->dir;
        else if(r->dir == NULL) return r->esq;
        else{
            no *temp = r->esq;
            while(temp->dir != NULL) temp = temp->dir;
            r->dado = temp->dado;
            r->esq = remover(r->esq, temp->dado);
        }
    }
    return r;
}

```

<!-- tabs:end -->

