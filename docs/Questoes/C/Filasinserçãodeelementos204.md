<center>

# Estrutura de Dados 1

</center>

---

# Filas inserção de elementos

<!-- tabs:start -->

#### **Questão**

 Numa fila, a inserção de elementos é chamada enfileiramento . Sua tarefa nesse exercício é implementar essa operação usando listas encadeadas . Para tanto, você deve submeter a função celula * enfileira ( celula * f , int x ); que deve • inserir o elemento x na fila encabeçada por f e • retornar o ponteiro para o novo nó cabeça, se a inserção foi bem sucedida, ou NULL , caso contrário. Espera-se que celula seja uma struct da forma typedef struct celula { int dado ; struct celula * prox ; } celula ; O arquivo a ser submetido deve incluir apenas 1. os #include necessários para a execução do seu código, 2. a declaração da estrutura necessária e 3. a função solicitada. 

Autor: John L. Gardenghi 

#### **Código**

```c
#include <stdlib.h>

typedef struct celula {
    int dado;
    struct celula *prox;
} celula;

celula *enfileira (celula *f, int x){
    celula *celula = malloc(sizeof(celula));
    if (celula == NULL) return NULL;

    celula->prox = f->prox;
    f->prox = celula;
    f->dado = x;

    return celula;
}
```

<!-- tabs:end -->

