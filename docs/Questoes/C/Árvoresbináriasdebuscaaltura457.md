<center>

# Estrutura de Dados 2

</center>

---

# Árvores binárias de busca altura

<!-- tabs:start -->

#### **Questão**

 Considere uma árvore binária de busca definida por células Sua tarefa nesse exercício é implementar uma função que retorne a altura de uma árvore binária de busca com raiz r . Para tanto, você deve submeter um arquivo contendo apenas: 1. Os #include necessários para execução das instruções utilizadas no seu código. 2. A definição da struct no . 3. Uma função que retorna a altura ℎ da árvore binária de busca. O protótipo desta função deve ser: 

Autor: John L. Gardenghi typedef struct no { int chave; struct no *esq, *dir; } no; int 

#### **Código**

```c
#include <stdio.h>
#include <stdlib.h>

typedef struct no {
    int dado;
    struct no *esq, *dir;
} no;

int altura (no *r){
    if(r == NULL) return 0;
    int esq = altura(r->esq);
    int dir = altura(r->dir);
    if(dir>esq) return dir+1;
    return esq+1;
}
```

<!-- tabs:end -->

