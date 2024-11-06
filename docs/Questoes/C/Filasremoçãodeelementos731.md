<center>

# Estrutura de Dados 1

</center>

---

# Filas remoção de elementos

<!-- tabs:start -->

#### **Questão**

 Numa fila, a inserção de elementos é chamada desenfileiramento . Sua tarefa nesse exercício é implementar essa operação usando listas encadeadas . Para tanto, você deve submeter a função int desenfileira ( celula * f , int * y ); que deve • remover um elemento da fila f e salvá-lo em y , • retornar 1 se a remoção foi bem sucedida, e 0 caso contrário. Espera-se que celula seja uma struct da forma typedef struct celula { int dado ; struct celula * prox ; } celula ; O arquivo a ser submetido deve incluir apenas 1. os #include necessários para a execução do seu código, 2. a declaração da estrutura necessária e 3. a função solicitada. 

Autor: John L. Gardenghi 

#### **Código**

```c
#include <stdlib.h>

typedef struct celula {
    int dado;
    struct celula *prox;
} celula;

int desenfileira (celula *f, int *y){
    if(f == NULL || f->prox == NULL) return 0;
    celula *temp = f->prox;
    *y = temp->dado;
    f->prox = temp->prox;
    free(temp);
    return 1;
}
```

<!-- tabs:end -->

