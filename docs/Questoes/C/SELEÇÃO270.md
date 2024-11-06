<center>

# Estrutura de Dados 1

</center>

---

# SELEÇÃO

<!-- tabs:start -->

#### **Questão**

 Simples! Apenas ordene os números lidos da entrada padrão utilizando o Algoritmo de Ordenação SELEÇÃO. Não tente trapacear rodando outra função pronta ou outro algoritmo de ordenação. Eu posso ver o seu código 8ˆ) ENTRADA A entrada possui um único caso de teste com uma quantidade arbitrária de números, a entrada termina quando o arquivo terminar ( EOF ). Os números cabem em um inteiro de 32 bits. Sabemos que cada caso de teste não possui mais que 1000 elementos. SAÍDA Imprima os mesmos números ordenados de forma não decrescente. Os números devem ser separados por espaço e não deve sobrar espaço após o último número que deve ter uma quebra de linha. EXEMPLO 

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

void selectionSortLoop(int *numeros, int tamanhoVet) {
    int menorIncice;

    for (int inicioAtual = 0; inicioAtual < tamanhoVet; inicioAtual++) {        // "varridas, waves" (INICIO + 1)

            menorIncice = inicioAtual;                                          // Armazena o menor numero

        for (int indice = inicioAtual+1; indice < tamanhoVet; indice++) {       // inteirador de indice

            if (numeros[indice] < numeros[menorIncice]) {                       // Encontra o menor numero
                menorIncice = indice;                                           // Salva o menor em menorIndice
            }
        }
        if(inicioAtual != menorIncice){                                         // Se o indice mudou swap
            swap(numeros,inicioAtual, menorIncice);
        }
    }
}

void selectionSortRecursivo(int *numeros,int inicioAtual, int tamanhoVet){
    if (inicioAtual == tamanhoVet - 1) return;

    int menorIndice = inicioAtual;                                              // Armazena o menor numero

    for (int indice = inicioAtual + 1; indice < tamanhoVet; indice++) {         // inteirador de indice
        if (numeros[indice] < numeros[menorIndice]) {                           // Encontra o menor numero
            menorIndice = indice;
        }
    }

    if (inicioAtual != menorIndice) {                                           // Se o indice mudou swap
        swap(numeros, inicioAtual, menorIndice);
    }

    selectionSortRecursivo(numeros, inicioAtual + 1, tamanhoVet);      // Inicio = Inicio +1
}

int main() {
    int numeros[1000];
    int tamanhoVet = 0;

    while (1) {
        int var = scanf("%d", &numeros[tamanhoVet]);
        if (var == EOF) break;
        tamanhoVet++;
    }

    selectionSortLoop(numeros, tamanhoVet);

    for (int j = 0; j < tamanhoVet; j++) {
        printf("%d", numeros[j]);
        if(numeros[j+1] != tamanhoVet) printf(" ");
    }
    printf("\n");

    return 0;
}

```

<!-- tabs:end -->

