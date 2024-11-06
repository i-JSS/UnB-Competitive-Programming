<center>

# Estrutura de Dados 1

</center>

---

# BOLHA

<!-- tabs:start -->

#### **Questão**

 Simples! Apenas ordene os números lidos da entrada padrão utilizando o Algoritmo de Ordenação BOLHA. Não tente trapacear rodando outra função pronta ou outro algoritmo de ordenação. Eu posso ver o seu código 8ˆ) ENTRADA A entrada possui um único caso de teste com uma quantidade arbitrária de números, a entrada termina quando o arquivo terminar ( EOF ). Os números cabem em um inteiro de 32 bits. Sabemos que cada caso de teste não possui mais que 1000 elementos. SAÍDA Imprima os mesmos números ordenados de forma não decrescente. Os números devem ser separados por espaço e não deve sobrar espaço após o último número que deve ter uma quebra de linha. EXEMPLO 

**Exemplo de Entrada 7**

 3 2 5 4 3 

**Saída**

 para o exemplo de entrada acima 2 3 3 4 5 7 

Autor: Bruno Ribas 

#### **Código**

```c
#include <stdio.h>

void swap(int *vetor, int A, int B) {
    int temp = vetor[A];
    vetor[A] = vetor[B];
    vetor[B] = temp;
}

void bubbleSortLoop(int *numeros, int tamanhoVet) {
    for (int final = tamanhoVet - 1; final > 0; final--) {          // "varridas, waves" (LISTA -1 ELEMENTO)

        int mudanca = 0;                                            // Verifica se fez alguma mudanca

        for (int indice = 0; indice < final; indice++) {            // inteirador de indice

            if (numeros[indice] > numeros[indice + 1]) {            // Se o v[n] > v[n+1] swap
                swap(numeros, indice, indice + 1);
                mudanca++;
            }
        }
        if(mudanca == 0) break;                                     // Se nao fez mudança ja ta ordenado
    }
}

void bubbleSortRecursivo(int *numeros, int tamanhoVet){
    if(tamanhoVet <= 1) return;                                     // Ver se ja fez todas as waves
    int mudanca = 0;

    for(int i = 0; i < tamanhoVet; i++){                            // Intera o tamanho
        if(numeros[i] > numeros[i+1]){                              // Se o v[n] > v[n+1] swap
            swap(numeros, i, i+1);
            mudanca++;
        }
    }
    if(mudanca == 0) return;                                        // Se nao fez mudança ja ta ordenado

    bubbleSortRecursivo(numeros, tamanhoVet-1);
}

int main() {
    int numeros[1000];
    int tamanhoVet = 0;

    while (1) {
        int var = scanf("%d", &numeros[tamanhoVet]);
        if (var == EOF) break;
        tamanhoVet++;
    }
    bubbleSortLoop(numeros, tamanhoVet);

    for (int j = 0; j < tamanhoVet; j++) {
        printf("%d ", numeros[j]);
    }
    printf("\n");

    return 0;
}

```

<!-- tabs:end -->

