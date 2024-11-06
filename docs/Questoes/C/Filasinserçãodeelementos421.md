<center>

# Estrutura de Dados 1

</center>

---

# Filas inserção de elementos

<!-- tabs:start -->

#### **Questão**

 Numa fila, a inserção de elementos é chamada enfileiramento . Sua tarefa nesse exercício é implementar essa operação usando vetores . Para tanto, você deve submeter a função int enfileira ( fila * f , int x ); que deve • inserir o elemento x na fila f e • retornar 1 se a inserção foi bem sucedida, e 0 caso contrário. Espera-se que fila seja uma struct da forma typedef struct fila { int * dados ; int N , p , u ; } fila ; Observações : • Você deve considerar uma fila circular . • Se na inserção, o elemento não couber na fila, o vetor dados deve ser redimensionado. O arquivo a ser submetido deve incluir apenas 1. os #include necessários para a execução do seu código, 2. a declaração da estrutura necessária e 3. a função solicitada. 

Autor: John L. Gardenghi 

#### **Código**

```c
#include <stdlib.h>

typedef struct {
    int *dados;
    int N;
    int p;
    int u;
} fila;

int enfileira(fila *f, int x) {

    if((f->u+1 == f->p) || (f->u+1 == f->N && f->p == 0)){
        f->N *= 2;
        int *newDados = malloc(f->N * sizeof(int));
        if(newDados == NULL) return 0;

        _Bool booleano = (f->N - f->p) > (f->u - 1);

        int i = f->p;
        int j = f->N - (f->N - f->p);
        if(booleano) j = f->p;

        while(i != f->u){
            newDados[j] = f->dados[i];
            i = (i+1) % f->N/2;
            j = (j+1) % f->N;
        }

        if(booleano) f->u = j;
        else f->p = f->N - (f->N/2 - f->p);

        free(f->dados);
        f->dados = newDados;
    }

    f->dados[f->u] = x;
    f->u = (f->u+1) % f->N;
    return 1;
}

```

<!-- tabs:end -->

