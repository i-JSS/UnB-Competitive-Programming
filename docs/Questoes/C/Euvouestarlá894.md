<center>

# Estrutura de Dados 2

</center>

---

# Eu vou estar lá!

<!-- tabs:start -->

#### **Questão**

 Um conhecido ladrão da região, Magno está com problemas com o pai do Carinha que mora logo ali, Juliano. Juliano prometeu estar em todo lugar que Magno for, e por isso Magno precisa fugir de Juliano. Para isso, Magno não pode ir à qualquer lugar que Juliano já esteve(e nem em suas vizinhanças), pois Juliano poderá estar nesses lugares. Tarefa É dada a lista de vizinhanças de todos os locais do bairro. Sua tarefa é descobrir é descobrir se Juliano estará nos locais informados. 

**Entrada**

 A entrada é composta por um único caso de testes. A primeira linha contém três números 𝑁 , 𝑀 , 𝐽 , indicando, respectivamente, o número de locais do bairro, o número de locais em que Juliano já esteve e o número de locais que deseja-se saber se Juliano estará. Todos os locais são numerados entre 0 e 𝑁 . As próximas 𝑁 linhas 𝑁 𝑖 iniciam-se com o índice 𝐴 . A mesma linha contém 𝐴 𝑗 inteiros, informando o índice dos locais vizinhos do local 𝑖 ; Em seguida são informados 𝑀 inteiros, indicando quais locais Juliano já esteve; E por último serão informados 𝐽 linhas, cada uma contendo um inteiro indicando o o identificador do local ao qual deseja-se saber se Juliano estará lá. Sabemos que, 0 ≤ 𝑁 ≤ 2000 , 0 ≤ 𝑀 ≤ 𝑁 , 0 ≤ 𝐽 ≤ 1000000 , 0 ≤ 𝐴 ≤ 𝑁 − 1 , 0 ≤ 𝐴 𝑗 ≤ 𝑁 − 1 . 

**Saída**

 Você deve imprimir “Eu vou estar la”, para os locais em que Juliano estará e “Nao vou estar la”, para outros locais. Exemplos 

**Exemplo de entrada**

 4 1 4 2 1 3 2 0 2 1 1 1 0 1 

3 0 2 

**Exemplo de saída**

 Eu vou estar la Nao vou estar la Eu vou estar la Eu vou estar la 

#### **Código**

```c
#include <stdio.h>
#include <stdlib.h>
#include <stdbool.h>

#define MAX_N 20000

typedef struct {
    int *data;
    int size;
    int capacity;
} Vector;

void vector_init(Vector *vec) {
    vec->capacity = 10;
    vec->size = 0;
    vec->data = (int *)malloc(vec->capacity * sizeof(int));
}

void vector_push(Vector *vec, int value) {
    if (vec->size == vec->capacity) {
        vec->capacity *= 2;
        vec->data = (int *)realloc(vec->data, vec->capacity * sizeof(int));
    }
    vec->data[vec->size++] = value;
}

int main() {
    int n, m, j;
    scanf("%d %d %d", &n, &m, &j);

    Vector adj_list[MAX_N];
    for (int i = 0; i < n; i++) vector_init(&adj_list[i]);

    bool *visitados = (bool *)calloc(n, sizeof(bool));
    bool *vizinhos = (bool *)calloc(n, sizeof(bool));

    for (int i = 0; i < n; i++) {
        int num_vizinhos;
        scanf("%d", &num_vizinhos);
        for (int k = 0; k < num_vizinhos; k++) {
            int vizinho;
            scanf("%d", &vizinho);
            vector_push(&adj_list[i], vizinho);
            vector_push(&adj_list[vizinho], i);
        }
    }

    for (int i = 0; i < m; i++) {
        int visitado;
        scanf("%d", &visitado);
        visitados[visitado] = true;
        for (int k = 0; k < adj_list[visitado].size; k++) {
            vizinhos[adj_list[visitado].data[k]] = true;
        }
    }

    for (int i = 0; i < j; i++) {
        int locais;
        scanf("%d", &locais);
        if (visitados[locais] || vizinhos[locais]) printf("Eu vou estar la\n");
        else printf("Nao vou estar la\n");

    }

    return 0;
}


```

<!-- tabs:end -->

