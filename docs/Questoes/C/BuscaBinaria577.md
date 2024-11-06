<center>

# Estrutura de Dados 1

</center>

---

# Busca Binaria

<!-- tabs:start -->

#### **Questão**

 O algoritmo de busca binária é um algoritmo clássico que busca que é usado como uma alternativa rápida para fazer buscas num conjunto de dados. Para que o algoritmo funcione, o conjunto deve estar ordenado. Para fixar ideias, sua tarefa, nesse exercício, é ler um conjunto de N números inteiros e, em seguida, ler M números inteiros que devem ser buscados no conjunto de dados. Dado um inteiro x , seu algoritmo deve retornar um índice j tal que v [ j − 1] < x ≤ v [ j ] . 

**Entrada**

 A entrada é composta M + N + 1 linhas. A primeira linha contém o valor de N e M , respectivamente ( 1 ≤ N, M ≤ 10 9 ). As N linhas seguintes contém números inteiros (que cabem num inteiro de 32 bits) que compõem o conjunto de dados de interesse de busca. Os N números são dados em ordem não decrescente. As M linhas seguintes contêm os inteiros que devem ser procurados no conjunto de dados. 

**Saída**

 Para cada inteiro x dado, você deve imprimir j tal que v [ j − 1] < x ≤ v [ j ] . Exemplo 

**Entrada**

 5 4 1 3 4 7 9 0 15 3 5 

**Saída**

 0 5 1 3 

Autor: John L. Gardenghi 

#### **Código**

```c
#include <stdio.h>
#include <stdlib.h>

int comparar(const void *a, const void *b) {
    return (*(int *)a - *(int *)b);
}

int encontrarIndice(int *vetor, int tamanho, int x) {
    int inicio = 0;
    int fim = tamanho - 1;
    int meio;

    while(inicio <= fim){
        meio = (inicio + fim) / 2;
        if (vetor[meio] == x) return meio;
        else if (vetor[meio] < x) inicio = meio + 1;
        else fim = meio - 1;
    }
    return inicio;
}

int main() {
    int N, M;
    scanf("%d %d", &N, &M);

    int *vetor = (int *)malloc(N * sizeof(int));
    for(int i = 0; i < N; i++) scanf("%d", &vetor[i]);

    qsort(vetor, N, sizeof(int), comparar);

    for(int i = 0; i < M; i++) {
        int consulta;
        scanf("%d", &consulta);
        printf("%d\n", encontrarIndice(vetor, N, consulta));
    }
    free(vetor);
    return 0;
}





```

<!-- tabs:end -->

