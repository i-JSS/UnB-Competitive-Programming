<center>

# Estrutura de Dados 1

</center>

---

# INSERÇÃO

<!-- tabs:start -->

#### **Questão**

 Simples! Apenas ordene os números lidos da entrada padrão utilizando o Algoritmo de Ordenação INSERÇÃO. Não tente trapacear rodando outra função pronta ou outro algoritmo de ordenação. Eu posso ver o seu código 8ˆ) ENTRADA A entrada possui um único caso de teste com uma quantidade arbitrária de números, a entrada termina quando o arquivo terminar ( EOF ). Os números cabem em um inteiro de 32 bits. Sabemos que cada caso de teste não possui mais que 50000 elementos. SAÍDA Imprima os mesmos números ordenados de forma não decrescente. Os números devem ser separados por espaço e não deve sobrar espaço após o último número que deve ter uma quebra de linha. EXEMPLO 

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


void insertionSortLoop(int *numeros, int tamanhoVet) {
    int i, j;                                           // Inteiradores
    int chave;                                          // Elemento atual

    for(i = 1; i < tamanhoVet; i++){                    // Inteirador do vetor
        chave = numeros[i];                             // Chave = i atual
        j = i - 1;                                      // J = elemento anterior a chave

        while(j>=0 && numeros[j] > chave){              // Varre ate o inicio ou ate um
                                                        // numero maior que a chave

            numeros[j + 1] = numeros[j];                // Troca eles de lugar
            j--;                                        // j--
        }
        numeros[j+1] = chave;                           // j+1
    }
}



int main() {
    int numeros[50000];
    int tamanhoVet = 0;

    while (1) {
        int var = scanf("%d", &numeros[tamanhoVet]);
        if (var == EOF) break;
        tamanhoVet++;
        if(tamanhoVet == 6) break;
    }

    insertionSortLoop(numeros, tamanhoVet);

    for (int j = 0; j < tamanhoVet; j++) {
        printf("%d ", numeros[j]);
    }
    printf("\n");

    return 0;
}
```

<!-- tabs:end -->

