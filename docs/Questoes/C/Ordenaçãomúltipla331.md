<center>

# Estrutura de Dados 2

</center>

---

# Ordenação múltipla

<!-- tabs:start -->

#### **Questão**

 Membros da famosa Associação de Programação Competitiva (APC) montaram um banco de dados de problemas de competição bem grande. Eles precisavam ordenar os problemas de acordo com o nível de dificuldade. Cada um dos 𝑀 membros da APC conseguiram 𝑁 problemas e forneceram a lista ordenada pelo nível de dificuldade. O nível de dificuldade é uma pontuação calculada pela combinação de vários critérios. Escreva um programa que imprima a lista de todos os 𝑁 × 𝑀 problemas ordenados. 

**Entrada**

 A primeira linha contém um inteiro 𝑇 , o total de casos de teste. Cada caso teste consiste em várias linhas. As duas primeiras linhas de cada caso contém inteiros 𝑀 e 𝑁 , respectivamente, de tal forma que 𝑁 × 𝑀 ≤ 10 6 . Cada uma das 𝑀 linhas seguintes contém 𝑁 números reais, separados por espaço, em ordem decrescente. Todos os números reais estão entre 0 e 10 (inclusive). 

**Saída**

 Para cada caso de teste, espera-se uma única linha contendo os 𝑁 × 𝑀 problemas. Cada problema deve ser representado por um par 𝑖 , 𝑗 , onde 𝑖 é a posição do membro (de 1 a 𝑀 ) e 𝑗 é a posição da nota na respectiva lista de problemas (de 1 a 𝑁 ). Os problemas devem ser exibidos pela sua pontuação (em ordem decrescente). Em caso de empate, imprima primeiro em ordem crescente de 𝑖 e, em caso de empate, por ordem crescente de 𝑗 . Exemplo 

**Entrada**

 1 3 4 9.195 4.17 2.532 0.03 8.28 5.5 4 2.69 8.8320 7.9 2.18 0 

**Saída**

 1,1 3,1 2,1 3,2 2,2 1,2 2,3 2,4 1,3 3,3 1,4 3,4 

#### **Código**

```c

#include "stdio.h"
#include "stdlib.h"
// USAR UM ESTAVEL

typedef struct No{
    double valor;
    int linha;
    int coluna;
} No;

void merge(No *vector, int left, int middle, int right){
    int size = right-left+1;
    No *vector2 = (No*)malloc(size*sizeof(No));

    int i = left, j = middle+1, k=0;

    while(i<=middle && j<=right){
        if(vector[i].valor >= vector[j].valor) vector2[k++] = vector[i++];
        else vector2[k++] = vector[j++];
    }

    while(i<=middle) vector2[k++] = vector[i++];
    while(j<=right) vector2[k++] = vector[j++];

    i=left;
    for(k=0; k<size; k++, i++) vector[i] = vector2[k];
    free(vector2);
}

void mergeSort(No arr[], int l, int r) {
    if (l < r) {
        int m = l + (r - l) / 2;
        mergeSort(arr, l, m);
        mergeSort(arr, m + 1, r);
        merge(arr, l, m, r);
    }
}

int main() {
    int T;
    scanf("%d", &T);
    for(int i = 0; i<T; i++){
        int N, M;
        scanf("%d %d", &N, &M);

        No lista[(N*M)+2];
        for(int j = 0; j< (N*M); j++) {
            double dado;
            scanf("%lf", &dado);
            lista[j].valor = dado;
            lista[j].linha = (j/M)+1;
            lista[j].coluna = (j%M)+1;
        }
        mergeSort(lista, 0, (N*M)-1);
        for(int k = 0; k < (N*M); k++) {
            printf("%d,%d ", lista[k].linha, lista[k].coluna);
        }
        printf("\n");
    }
    return 0;
}

```

<!-- tabs:end -->

