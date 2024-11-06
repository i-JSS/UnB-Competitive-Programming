<center>

# Estrutura de Dados 1

</center>

---

# Ordenação eficiente

<!-- tabs:start -->

#### **Questão**

 Esse é um problema bem simples! Ordene um conjunto de números lidos usando um algoritmo de ordenação eficiente. Não use funções prontas: desenvolva a sua. 

**Entrada**

 A entrada é composta por duas linhas. A primeira contém a quantidade n de elementos que devem ser ordenados. A segunda contém os n números separados por espaço. 

**Saída**

 Sua saída deve conter os números ordenados de forma não decrescente. Os números devem ser separados por espaço e não deve sobrar espaço após o último número que deve ter uma quebra de linha. 

**Exemplo de Entrada 1**

 6 7 3 2 5 4 3 

**Exemplo de Saída 1**

 2 3 3 4 5 7 

Autor: Bruno Ribas 

#### **Código**

```c
#include <stdio.h>
#include <stdlib.h>

void swap(int *vetor, int A, int B) {
    int temp = vetor[A];
    vetor[A] = vetor[B];
    vetor[B] = temp;
}

void merge(int *numeros, int l, int meio, int r) {

    int tam = r+1 - l ;       // Calcula o tamanho

    // alocar espaço auxiliar
    int *aux = malloc ( tam * sizeof (int) );

    int i = l ;                 // inicio do sub - vetor esquerdo
    int j = meio +1;            // inicio do sub - vetor direito
    int k =0;                   // inicio do vetor auxiliar

    // ordenar em aux [k]
    while (k < tam ) {                              // condição de parada do aux

        if(i > meio )                               // ordenou o primeiro sub - vetor
            aux [k++] = numeros[j++];               // consome o segundo sub - vetor

        else if (j > r )                            // ordenou o segundo sub - vetor
            aux [k++] = numeros[i++];               // consome o primeiro sub - vetor

        else if ( numeros[ i ] < numeros[ j ])      // testar sub - vetores
            aux [k++] = numeros[ i ++];             // ordene no aux

        else aux [k++] = numeros[j++];              // ordene no aux
    }

    k = 0;                                         // indice do aux
    for( i = l ; i <= r ; i ++)                     // indice do v
        numeros[i] = aux [k++];                   // copiar o aux[k] para v[i]

    // liberar memória
    free ( aux ) ;
}

void mergeSort (int *numeros , int l , int r ) {
    if ( l >= r ) return ;                        // ver se atingiu o fim

    int meio = ( r+l) /2;

    mergeSort (numeros , l , meio ) ;           //F(n/2)
    mergeSort (numeros , meio + 1 , r ) ;       //F(n/2)
    merge (numeros , l , meio , r ) ;             //n
}

int main() {
    int tam;
    scanf("%d", &tam);

    int numeros[tam + 1];

    int tamanhoVet = 0;

    while (1) {
        scanf("%d", &numeros[tamanhoVet]);
        tamanhoVet++;
        if(tamanhoVet == tam) break;
    }

    mergeSort(numeros,0, tamanhoVet-1);

    for (int j = 0; j < tamanhoVet; j++) {
        printf("%d ", numeros[j]);
    }
    printf("\n");

    return 0;
}

```

<!-- tabs:end -->

