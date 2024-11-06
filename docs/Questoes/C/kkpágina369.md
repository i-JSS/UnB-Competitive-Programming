<center>

# Estrutura de Dados 2

</center>

---

# kk página

<!-- tabs:start -->

#### **Questão**

 Uma grande empresa de desenvolvimento de páginas de produtos eletrônicos está com um problema grave! Alguns bots e pessoas maliciosas conseguem deixar o servidor não responsivo com uma pesquisa bem curiosa. Jaime, o rapaz do TI da empresa, percebeu que quando a pessoa clica no botão de consulta avançada do site e marca as opções: mostrar TODOS os produtos; ordenar por 𝐼 𝐷 , e; ir para uma página 𝑋 qualquer; o servidor demora a reponder (as vezes até minutos). Para piorar, se mais pessoas fazem isso, o servidor fica com várias consultas em execução e eventualmente para de responder totalmente. O dono da empresa, Istivi Trabalhos , precisa de uma ajuda mais especializada e, não por acaso, te encontrou na lista de alunos de Engenharia de Software da UnB e gostou do seu perfil e requer a sua ajuda! O problema já foi repassado para você e temos a parte que mais interessa. O seu programa será compilado com os parâmetros: gcc -O2 -static arquivo.c -o arquivo 

**Entrada**

 A entrada é composta por um único caso de teste contendo diversas linhas. A primeira linha, do caso de teste, possui três números inteiros: 𝑁 ( 0 < = 𝑁 < = 2 25 ), sendo a quantidade de produtos; 𝑃 ( 0 < = 𝑃 < = 2 16 ), sendo a página que deve ser apresentada; 𝑋 ( 1 < = 𝑋 < = 100 ), sendo a quantidade de produtos que aparecem por página; A seguir são apresentada 𝑁 linhas, cada uma contendo um inteiro 𝐼 𝐷 𝑖 ( 0 < = 𝐼 𝐷 𝑖 < = 2 31 ) representando o 𝐼 𝐷 de um produto. Não existem ids repetidos. 

**Saída**

 Você deve imprimir os 𝑋 𝐼 𝐷 𝑠 da página 𝑃 , ordenados de forma não decrescente. Exemplo 

**Exemplo de entrada**

 10 3 2 1 2 3 4 5 6 7 

9 10 Atenção: A página é indexada a partir de 0 , logo a página ( 𝑃 = ) 3 representa a quarta página 

**Exemplo de saída**

 7 8 

**Exemplo de entrada**

 10 1 3 248 125 378 268 343 45 78 71 297 150 

**Exemplo de saída**

 125 150 248 

**Exemplo de entrada**

 9 4 2 106 210 270 67 69 127 303 236 249 

**Exemplo de saída**

 

ATENÇÃO: Cuidado quando a impressão acontece na última página, podem sobrar menos elementos que o máximo para se mostrar em cada página 

#### **Código**

```c
//
// Created by joaos on 11/04/2024.
//
#include "stdio.h"
#define Item unsigned

void swap(Item *a, Item *b) {
    Item temp = *a;
    *a = *b;
    *b = temp;
}

Item mediana(Item *lista, int l, int r) {
    int mid = l + (r - l) / 2;
    if (lista[mid] < lista[l]) swap(&lista[mid], &lista[l]);
    if (lista[r] < lista[l]) swap(&lista[r], &lista[l]);
    if (lista[mid] < lista[r]) swap(&lista[mid], &lista[r]);
    return lista[r];
}

int particiona(Item *lista, int l, int r) {
    Item pivo = mediana(lista, l, r);
    int i = l - 1;
    for (int j = l; j < r; ++j) {
        if (lista[j] <= pivo) {
            ++i;
            swap(&lista[i], &lista[j]);
        }
    }
    swap(&lista[i + 1], &lista[r]);
    return i + 1;
}

void quickSelect(Item *V, int L, int R, int K){
    int i = particiona(V,L,R);
    if(R<=L) return;
    if(i>K) quickSelect(V,L,i-1, K);
    if(i<K) quickSelect(V, i+1, R, K);
}

void quickSort(Item *arr, int l, int r) {
    if (l < r) {
        int pivo = particiona(arr, l, r);
        quickSort(arr, l, pivo - 1);
        quickSort(arr, pivo + 1, r);
    }
}

int main(){
    int N, P, X;
    scanf("%d %d %d", &N, &P, &X);
    unsigned int vetor[N+2];
    for(int i = 0; i < N; i++){
        scanf("%d", &vetor[i]);
    }

    int k = P * X + X;
    quickSelect(vetor, 0, N-1, P*X);
    quickSort(vetor, P*X, N-1);
    for(int i = P*X; i < k; i++){
        if(i < N) printf("%d\n", vetor[i]);
    }

    return 0;
}
```

<!-- tabs:end -->

