<center>

# Estrutura de Dados 2

</center>

---

# Árvore Binária Balanceada

<!-- tabs:start -->

#### **Questão**

 Dado uma árvore binária, determine se a sua altura é balanceada. Uma árvore binária possui a sua altura balanceada se a profundidade de duas sub-árvores de cada nó nunca difere em mais de um. 

**Entrada**

 A entrada é composta por um único caso de teste. A primeira linha possui um inteiro 𝑁 ( 1 ≤ 𝑁 ≤ 5000 ), sendo a quantidade de nós da árvore. A segunda linha possui 𝑁 − 1 inteiros 𝐶 2 , 𝐶 3 , 𝐶 𝑖 + 1 , . . . , 𝐶 𝑁 − 1 , onde o i-ésimo deles identifica o pai direto do nó 𝑖 + 1 , sendo a raiz o nó 1 . É garantido que para toda entrada, é entregue uma única árvore binária válida. 

**Saída**

 A saída é composta por uma única linha. Caso a árvore binária tenha a sua altura balanceada, imprima Sim . Caso contrário, imprima Nao . Exemplos 

**Exemplo de entrada**

 5 1 1 3 3 

**Exemplo de saída**

 Sim Explicação: Todas as sub-árvores possuem sua diferença de altura de no máximo 1 . A partir do nó 1 , temos as alturas { 1 , 2 }. A partir do nó 2 , as alturas { 0 , 0 }. Do nó 3 , { 1 , 1 



**Exemplo de Entrada 7**

 1 1 3 3 5 5 

**Exemplo de saída**

 



#### **Código**

```c

#include "stdio.h"
#include "stdlib.h"
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
int altBalanceada(no *raiz){
    if(raiz == NULL) return 1;
    int alturaEsq = altura(raiz->esq);
    int alturaDir = altura(raiz->dir);
    if((abs(alturaEsq-alturaDir) <= 1) && altBalanceada(raiz->dir) && altBalanceada(raiz->esq)) return 1;
    return 0;
}
no* novo_no(int x) {
    no *n = (no*)malloc(sizeof(no));
    n->dado = x;
    n->esq = n->dir = NULL;
    return n;
}
int main(){
    int tam, temp = 1;
    scanf("%d", &tam);
    int raiz[tam+4];
    no *arvore[tam+4];
    for(int i = 1; i <= tam; i++) {
        if(i!=1) scanf("%d", &raiz[i]);
        arvore[i] = novo_no(i);
    }
    for(int i = 2; i <= tam; i++){
        if(arvore[raiz[i]]->esq == NULL) arvore[raiz[i]]->esq = arvore[i];
        else arvore[raiz[i]]->dir = arvore[i];
    }
    if(altBalanceada(arvore[temp])) printf("Sim\n");
    else printf("Nao\n");
    return 0;
}

```

<!-- tabs:end -->

