<center>

# Estrutura de Dados 2

</center>

---

# Árvores binárias de busca máximo

<!-- tabs:start -->

#### **Questão**

 Considere uma árvore binária de busca definida por células Sua tarefa nesse exercício é implementar uma função que procure e retorne o valor máximo de uma árvore binária de busca com raiz r . Para tanto, você deve submeter um arquivo contendo apenas: 1. Os #include necessários para execução das instruções utilizadas no seu código. 2. A definição da struct no . 3. Uma função de procura do valor máximo 𝑥 na árvore binária de busca. O protótipo desta função deve ser: 

Autor: John L. Gardenghi typedef struct no { int chave; struct no *esq, *dir; } no; 

#### **Código**

```c
#include <stdio.h>
#include <stdlib.h>

typedef struct no {
    int dado;
    struct no *esq, *dir;
} no;

no *maximo (no *r){
    if(r == NULL) return r;
    while (r->dir!=NULL){
        r= r->dir;
    }
    return r;
}
```

<!-- tabs:end -->

