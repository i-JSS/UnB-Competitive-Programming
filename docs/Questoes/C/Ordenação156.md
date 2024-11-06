<center>

# Estrutura de Dados 1

</center>

---

# Ordenação

<!-- tabs:start -->

#### **Questão**

 Esse é um problema bem simples, mas vou te pedir uma solução desafiadora! Ordene um conjunto de n números armazenados num vetor v usando o algoritmo de ordenação por inserção ou por seleção. Mas você deve submeter apenas sua função de ordenação com o seguinte protótipo: void ordena ( int * v , int n ); Não use funções prontas: desenvolva a sua. Ah! Sua função não pode usar laços. 

Autor: John L. Gardenghi 

#### **Código**

```c

void ordena(int *numeros, int tamanhoVet) {
    int menorIncice;

    for (int inicioAtual = 0; inicioAtual < tamanhoVet; inicioAtual++) {        // "varridas, waves" (INICIO + 1)

        menorIncice = inicioAtual;                                              // Armazena o menor numero

        for (int indice = inicioAtual+1; indice < tamanhoVet; indice++) {       // inteirador de indice

            if (numeros[indice] < numeros[menorIncice]) {                       // Encontra o menor numero
                menorIncice = indice;                                           // Salva o menor em menorIndice
            }
        }
        if(inicioAtual != menorIncice){
            int temp = numeros[inicioAtual];
            numeros[inicioAtual] = numeros[menorIncice];
            numeros[menorIncice] = temp;

        }
    }
}

```

<!-- tabs:end -->

