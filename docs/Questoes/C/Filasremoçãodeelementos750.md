<center>

# Estrutura de Dados 1

</center>

---

# Filas remoção de elementos

<!-- tabs:start -->

#### **Questão**

 Numa fila, a inserção de elementos é chamada desenfileiramento . Sua tarefa nesse exercício é implementar essa operação usando vetores . Para tanto, você deve submeter a função int desenfileira ( fila * f , int * y ); que deve • remover um elemento da fila f e salvá-lo em y , • retornar 1 se a remoção foi bem sucedida, e 0 caso contrário. Espera-se que fila seja uma struct da forma typedef struct fila { int * dados ; int N , p , u ; } fila ; Observações : • Você deve considerar uma fila circular . • Se na inserção, o elemento não couber na fila, o vetor dados deve ser redimensionado. O arquivo a ser submetido deve incluir apenas 1. os #include necessários para a execução do seu código, 2. a declaração da estrutura necessária e 3. a função solicitada. 

Autor: John L. Gardenghi 

#### **Código**

```c
#include <stdlib.h>

typedef struct fila {
    int *dados;
    int N, p, u;
} fila;

int desenfileira(fila *f, int *y) {
    if (f == NULL || f->dados == NULL || f->p == f->u) return 0;

    *y = f->dados[f->p];
    f->p = (f->p + 1) % f->N;
    return 1;
}
```

<!-- tabs:end -->

