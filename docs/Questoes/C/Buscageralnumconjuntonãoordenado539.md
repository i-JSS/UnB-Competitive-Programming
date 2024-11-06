<center>

# Estrutura de Dados 1

</center>

---

# Busca geral num conjunto não ordenado

<!-- tabs:start -->

#### **Questão**

 Sua tarefa, neste exercício, é ler um conjunto de N número inteiros e depois verificar se M elementos pertencem ou não ao conjunto. Se pertencerem, você deve imprimir a posição que ocupam. Se não, você deve imprimir -1. 

**Entrada**

 A entrada é composta M + N + 1 linhas. A primeira linha contém o valor de N e M , respectivamente ( 1 ≤ N, M ≤ 10 9 ). As N linhas seguintes contém números inteiros (que cabem num inteiro de 32 bits) que compõem o conjunto de dados de interesse de busca. As M linhas seguintes contêm os inteiros que devem ser procurados no conjunto de dados. 

**Saída**

 Para cada inteiro x dado, você deve imprimir a posição j tal que v [ j ] = x , ou − 1 se x não pertencer a v . Exemplo 

**Entrada**

 6 4 7 3 4 9 1 5 0 3 15 5 

**Saída**

 -1 1 -1 5 

Autor: John L. Gardenghi 

#### **Código**

```c
#include <stdio.h>

typedef struct no {
    int valor;
    int index;
} no;

void swap(no *vetor, int A, int B) {
    int temp = vetor[A].valor;
    vetor[A].valor = vetor[B].valor;
    vetor[B].valor = temp;

    temp = vetor[A].index;
    vetor[A].index = vetor[B].index;
    vetor[B].index = temp;
}

int partition(no arr[], int low, int high) {
    int pivot = arr[high].valor;
    int i = low - 1;

    for (int j = low; j < high; j++) {
        if (arr[j].valor <= pivot) {
            i++;
            swap(arr, i, j);
        }
    }

    swap(arr, i + 1, high);
    return i + 1;
}

void quicksort(no *arr, int low, int high) {
    if (low < high) {
        int pi = partition(arr, low, high);
        quicksort(arr, low, pi - 1);
        quicksort(arr, pi + 1, high);
    }
}

int buscaBinaria(no *arr, int tamanho, int chave) {
    int baixo = 0, alto = tamanho - 1;

    while (baixo <= alto) {
        int meio = baixo + (alto - baixo) / 2;

        if (arr[meio].valor == chave) return arr[meio].index;
        else if (arr[meio].valor < chave) baixo = meio + 1;
        else alto = meio - 1;
    }
    return -1;
}

int main() {
    int N, M;
    scanf("%d %d", &N, &M);

    no listaProcurada[N];
    for (int i = 0; i < N; i++) {
        scanf("%d", &listaProcurada[i].valor);
        listaProcurada[i].index = i;
    }
    quicksort(listaProcurada, 0, N - 1);

    int atual;
    for (int j = 0; j < M; j++) {
        scanf("%d", &atual);
        printf("%d\n", buscaBinaria(listaProcurada, N, atual));
    }

    return 0;
}



```

<!-- tabs:end -->

