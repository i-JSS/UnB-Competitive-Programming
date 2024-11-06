<center>

# Estrutura de Dados 2

</center>

---

# Selecionando Componentes

<!-- tabs:start -->

#### **Questão**

 A Equipe de Descobertas Atômicas (EDA) conduziu uma pesquisa recente visando aprimorar a eficiência e a durabilidade dos componentes eletrônicos. Durante o estudo, identificou-se que a utilização de certos minerais encontrados em meteoritos pode significativamente melhorar a dissipação de calor de um sistema. No entanto, é crucial realizar a filtragem desses componentes com extrema cautela, pois uma seleção inadequada pode resultar em efeitos adversos, podendo danificar todo o circuito eletrônico. Para realizar a filtragem, empregam-se dois tubos de ensaio, designados como 𝑇 𝑎 e 𝑇 𝑏 . Inicialmente, todos os 𝑁 minerais 𝐴 𝑖 presentes no meteorito são colocados no primeiro tubo, 𝑇 𝑎 , onde 𝐴 𝑖 representa a densidade atual do minério 𝑖 . Devido à tendência dos materiais menos densos de flutuarem no líquido contido no tubo de ensaio 𝑇 𝑎 , o mineral de menor densidade é selecionado e transferido para o tubo 𝑇 𝑏 . Se o módulo da diferença entre o menor elemento de 𝑇 𝑎 e o maior elemento de 𝑇 𝑏 não exceder 𝑋 e for maior que zero, os dois minerais são removidos dos tubos e combinados, resultando em uma soma de suas densidades. Atenção: Primeiro é verificado se o conteúdo presente nos tubos é elegível para realizar a junção. Caso contrário, o conteúdo menos denso do tubo 𝑇 𝑎 é transferido para o tubo 𝑇 𝑏 . Sua responsabilidade é apresentar quantos minerais foram combinados e quais foram eles, listados em ordem cronológica do menos recente para o mais recente. 

**Entrada**

 A entrada é composta por um único caso de teste. A primeira linha possui dois números inteiros 𝑁 e 𝑋 ( 1 ≤ 𝑁 , 𝑋 ≤ 10 6 ), representando a quantidade de minerais presentes no tubo 𝑇 𝑎 . A segunda linha possui 𝑁 números inteiros 𝐴 𝑖 ( 1 ≤ 𝐴 𝑖 ≤ 10 9 ), sendo a densidade do mineral 𝑖 . 

**Saída**

 A primeira linha da saída deve ser representado pelo número de minerais combinados. A segunda linha deve estar presente caso haja ao menos 1 material combinado. Nela, você deve imprimir as densidades combinadas separadas por um espaço em branco. Exemplos 

**Exemplo de entrada**

 6 1 1 2 3 4 5 6 

3 3 7 11 Iteração Tubo A Tubo B Ação Resposta 1 [2, 3, 4, 5, 6] [1] Combinar 1 e 2 [3] 2 [6, 5, 4] [3] Combinar 3 e 4 [3, 7] 3 [6] [5] Combinar 5 e 6 [3, 7, 11] 

**Exemplo de entrada**

 6 2 10 7 20 9 15 12 

**Exemplo de saída**

 2 16 22 Iteração Tubo A Tubo B Ação Resposta 1 [9, 10, 12, 15, 20] [7] Combinar 7 e 9 [16] 2 [12, 15, 20] [10] Combinar 10 e 12 [16, 22] 3 [20] [15] Nada [16, 22] 4 [ ] [15, 20] Nada [16, 22] 

#### **Código**

```c

#include <stdio.h>
#include <stdlib.h>
#define swap(a, b) {int t = a; a = b; b = t;}
int *HEAP_MINIMA, TAMANHO_MINIMA = 0;
int *HEAP_MAXIMA, TAMANHO_MAXIMA = 0;
typedef struct {
    int *VETOR;
    int TAMANHO;
    int CAPACIDADE;
} HEAP;
HEAP* criaHeap(int capacidade) {
    HEAP *heap = (HEAP *)malloc(sizeof(HEAP));
    heap->VETOR = (int *)malloc((capacidade + 1) * sizeof(int));
    heap->TAMANHO = 0;
    heap->CAPACIDADE = capacidade;
    return heap;
}
void fixupMin(int *VETOR, int i){
    while (i > 1 && VETOR[i / 2] > VETOR[i]) {
        swap(VETOR[i], VETOR[i / 2]);
        i /= 2;
    }
}
void fixdownMin(int *VETOR, int tam, int i){
    while (2 * i <= tam) {
        int j = 2 * i;
        if (j < tam && VETOR[j] > VETOR[j + 1]) j++;
        if (VETOR[i] <= VETOR[j]) break;
        swap(VETOR[i], VETOR[j]);
        i = j;
    }
}
void inserirHeapMin(HEAP *heap, int p) {
    if (heap->TAMANHO == heap->CAPACIDADE) return;
    heap->VETOR[++heap->TAMANHO] = p;
    fixupMin(heap->VETOR, heap->TAMANHO);
}
void fixupMax(int *VETOR, int i){
    while (i > 1 && VETOR[i / 2] < VETOR[i]) {
        swap(VETOR[i], VETOR[i / 2]);
        i /= 2;
    }
}
void fixdownMax(int *VETOR, int tam, int i){
    while (2 * i <= tam) {
        int j = 2 * i;
        if (j < tam && VETOR[j] < VETOR[j + 1]) j++;
        if (VETOR[i] >= VETOR[j]) break;
        swap(VETOR[i], VETOR[j]);
        i = j;
    }
}
int removerMinimo(HEAP *heap) {
    int raiz = heap->VETOR[1];
    heap->VETOR[1] = heap->VETOR[heap->TAMANHO--];
    fixdownMin(heap->VETOR, heap->TAMANHO, 1);
    return raiz;
}
void inserirHeapMax(HEAP *heap, int p) {
    if (heap->TAMANHO == heap->CAPACIDADE) return;
    heap->VETOR[++heap->TAMANHO] = p;
    fixupMax(heap->VETOR, heap->TAMANHO);
}
int removerMaximo(HEAP *heap) {
    int raiz = heap->VETOR[1];
    heap->VETOR[1] = heap->VETOR[heap->TAMANHO--];
    fixdownMax(heap->VETOR, heap->TAMANHO, 1);
    return raiz;
}
int main() {
    int N, X;
    scanf("%d %d", &N, &X);
    HEAP *TubosA = criaHeap(N);
    HEAP *TubosB = criaHeap(N);
    int temp, *combinacoes = (int *)malloc(N * sizeof(int)), contadorCombinacoes = 0;
    for(int i = 0; i < N; i++) {
        scanf("%d", &temp);
        inserirHeapMin(TubosA, temp);
    }
    while (TubosA->TAMANHO > 0) {
        int menor = removerMinimo(TubosA);
        if(TubosB->TAMANHO > 0) {
            int maior = TubosB->VETOR[1];
            int mod = abs(menor - maior);
            if(0 < mod && mod <= X) {
                removerMaximo(TubosB);
                combinacoes[contadorCombinacoes++] = menor + maior;
            }
            else inserirHeapMax(TubosB, menor);
        }
        else inserirHeapMax(TubosB, menor);
    }
    printf("%d\n", contadorCombinacoes);
    for (int i = 0; i < contadorCombinacoes; i++) {
        printf("%d ", combinacoes[i]);
    }
    printf("\n");
    return 0;
}

```

<!-- tabs:end -->

