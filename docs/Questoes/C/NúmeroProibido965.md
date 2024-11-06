<center>

# Estrutura de Dados 1

</center>

---

# Número Proibido

<!-- tabs:start -->

#### **Questão**

 Os números proibidos são números que possuem alguma representação problemática, por exemplo, número do azar, de algo ruim, e até números que são senhas do governo. O número proibido mais conhecido é um número primo 1 que foi descoberto em 2001 e representa o arquivo binário da versão compactada do código C que implementa o algoritmo DeCSS, que pode ser utilizado para lograr o sistema de proteção do DVD. Luan, um rapaz que tem muito receio de ser procurado por agências espiãs internacionais coletou um conjunto de números ilegais e está filtrando esses números de todos os seus arquivos no computador. Infelizmente, Luan ainda não sabe programar muito bem e pediu a sua ajuda para implementar um programa que receba um conjunto de números ilegais e responda se um outro conjunto de números fazem parte dos números ilegais. 

**Entrada**

 A entrada é composta por um único caso teste que possui diversas linhas. A primeira linha possui um número N ( 1 ≤ N ≤ 140000 ) que representa a quantidade de números proibidos existentes. A segunda linha do caso de teste possui N números P i ( 0 ≤ P i ≤ 2 31 ) representando os números proibidos. Depois existirão diversas linhas contendo um único número que se quer saber se é proibido ou não. A entrada termina em EOF. 

**Saída**

 Para cada número da consulta deve-se imprimir uma única linha contendo a palavra sim se o número for proibido, ou nao caso o número não seja proibido. 1 http://en.wikipedia.org/wiki/Illegal_prime 

Exemplo 

**Exemplo de entrada**

 7 10 0 50 25 121 0 3000 1 2 3 10 0 

**Saída**

 para o exemplo de entrada acima nao nao nao sim sim 

Autor: Bruno Ribas 

#### **Código**

```c
#include <stdio.h>
#include <stdlib.h>

int comparar(const void *a, const void *b) {
    return (*(int*)a - *(int*)b);
}

int buscaBinaria(int *arr, int tamanho, int chave){
    int baixo = 0, alto = tamanho - 1;

    while(baixo <= alto){
        int meio = baixo + (alto - baixo) / 2;

        if(arr[meio] == chave) return 1;
        else if (arr[meio] < chave) baixo = meio + 1;
        else alto = meio - 1;
    }
    return 0;
}

int main() {
    int N;
    scanf("%d", &N);

    int lista[N];
    for(int i = 0; i < N; i++)scanf("%d", &lista[i]);

    qsort(lista, N, sizeof(int), comparar);

    int Q;
    while (scanf("%d", &Q) != EOF) {
        int proibido = buscaBinaria(lista, N, Q);
        if (proibido) printf("sim\n");
        else printf("nao\n");
    }

    return 0;
}

```

<!-- tabs:end -->

