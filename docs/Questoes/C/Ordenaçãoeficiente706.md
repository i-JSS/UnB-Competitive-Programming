<center>

# Estrutura de Dados 2

</center>

---

# Ordenação eficiente

<!-- tabs:start -->

#### **Questão**

 Esse é um problema bem simples! Ordene um conjunto de números lidos usando um algoritmo de ordenação eficiente. Não use funções prontas: desenvolva a sua. 

**Entrada**

 A entrada é composta por duas linhas. A primeira contém a quantidade 𝑛 de elementos que devem ser ordenados. A segunda contém os 𝑛 números separados por espaço. 

**Saída**

 Sua saída deve conter os números ordenados de forma não decrescente. Os números devem ser separados por espaço e não deve sobrar espaço após o último número que deve ter uma quebra de linha. 

**Exemplo de Entrada 1**

 6 7 3 2 5 4 3 

**Exemplo de Saída 1**

 2 3 3 4 5 7 

#### **Código**

```c
#include "stdio.h"

#define Item int
#define swap(a, b) {Item t = a; a = b; b = t;}
#define compare(a, b) (a <= b)
#define cswap(a, b) if (compare(b, a)) swap(a, b)


int particiona(Item *arr, int l, int r){
    Item pivot = arr[r];
    int j = l;
    for(int i = l; i < r; i++){
        if(compare(arr[i], pivot)){
            swap(arr[i], arr[j]);
            j++;
        }
    }
    swap(arr[j], arr[r]);
    return j;
}

void quickSort(Item *arr, int l, int r){
    if(r<=l) return;

    cswap(arr[(l+r)/2], arr[r]);
    cswap(arr[l], arr[(l+r)/2]);
    cswap(arr[r], arr[(l+r)/2]);

    int mid = particiona(arr, l, r);
    quickSort(arr,l,mid-1);
    quickSort(arr,mid+1,r);
}

void quickSelect(Item *arr, int l, int r, int i){
    if(r<=l) return;

    cswap(arr[(l+r)/2], arr[r]);
    cswap(arr[l], arr[(l+r)/2]);
    cswap(arr[r], arr[(l+r)/2]);

    int meio = particiona(arr, l, r);                   // RETORNA O PIVO NA POSISAO DEFINITIVA
    if(meio > i) quickSelect(arr, l, meio-1, i);     // VERIFICA O PIVO NA VERSAO DEFINITIVA E FAZ UMA
    if(meio < i) quickSelect(arr, meio+1, r, i);     // BUSCA BINARIA SEMPRE N*LOGN
}


int main(){
    int N;
    scanf("%d", &N);
    int arr[N+2];
    for(int i = 0; i<N; i++){
        scanf("%d", &arr[i]);
    }
//    quickSort(arr, 0, N-1);
    quickSelect(arr, 0, N-1, 10);
//    insertionSort(arr, 0, N-1);
    for(int i = 0; i < N; i++){
        printf("%d ", arr[i]);
    }
    return 0;
}
```

<!-- tabs:end -->

