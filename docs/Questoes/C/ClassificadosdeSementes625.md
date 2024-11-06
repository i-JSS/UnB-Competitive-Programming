<center>

# Estrutura de Dados 2

</center>

---

# Classificados de Sementes

<!-- tabs:start -->

#### **Questão**

 A famosa empresa agrônoma, EDA (Estudos e Desenvolvimento Agrônomos), está realizando a coleta de resultados da qualidade das sementes de todos os produtos que podem ser plantados no planeta terra. Um dos objetivos desta seleção está em descobrir se temos alguma semente que poderá ser plantada em um outro planeta, como marte. O problema que esta renomada empresa está enfrentando é como descobrir quais são as melhores sementes. Laboratórios do mundo todo mandaram informações de muitas sementes, na casa dos bilhões, e a EDA precisa urgentemente da lista (ordenada) das 𝑘 melhores sementes para realizar o experimento. O grupo técnico da EDA já tentou ordenar esse conjunto de dados e não obteve sucesso, nem mesmo o quicksort com a melhor estratégia consegue ordenar este vetor. E para conseguir resolver este problema, a EDA chamou você para auxiliar nesta difícil tarefa. 

**Entrada**

 A entrada possui um único caso de teste. A primeira linha do caso de teste possui um número 𝑘 ( 1 ≤ 𝑘 ≤ 10 9 ) representando quantas sementes você deverá selecionar (baseada no melhor Valor), a seguir existe um número indeterminado de linhas (sabemos que não passa de 10 7 entradas e você pode assumir que cabe na memória, pois a EDA disponibilizou uma máquina grande). Cada linha da entrada possui 2 números inteiros 𝑆 ( 0 ≤ 𝑆 ≤ 2 50 ) e 𝑁 ( − 10 9 ≤ 𝑁 ≤ 10 9 ), representando o código da Semente e a Nota da qualidade, respectivamente. 

**Saída**

 A saída deverá ser composta por um conjunto de linhas que representam as 𝑘 melhores sementes. Quanto menor o valor de 𝑁 melhor é a semente. A saída deve estar ordenada pelo código da semente (da menor para a maior). Havendo empate nas notas da semente o desempate será feito pelo menor código de semente. Exemplos 

**Exemplo de Entrada 4**

 30553 3265 27183 26616 2414 -30329 16682 23006 20027 5010 10315 32560 23488 17242 

2660 23760 10568 27930 

**Exemplo de saída**

 2414 -30329 20027 5010 26565 -22549 30553 3265 Exemplo 

**Entrada**

 3 10 232 32 656 4535 -222 56 -222 767 -222 943 -222 323 -222 

**Exemplo de saída**

 56 -222 323 -222 767 -222 DICAS: Evite ordenar a entrada toda Cuidado com as sementes de nota iguais 

#### **Código**

```c
#include "stdio.h"
#include "stdlib.h"
typedef struct No{
    unsigned long long codigo;
    long long qualidade;
} No;
#define Item No
#define swap(a, b) \
    {Item t = a; a = b; b = t;}
#define compareQS(a, b) \
    (a.codigo != b.codigo ? a.codigo < b.codigo : a.qualidade < b.qualidade)
#define cswapQS(a, b) \
    if (compareQSL(b, a)) swap(a, b)
#define compareQSL(a, b) \
     (a.qualidade != b.qualidade ? a.qualidade < b.qualidade : a.codigo < b.codigo)
#define cswapQSL(a, b) \
    if (compareQS(b, a)) swap(a, b)
void insertionSort(Item *lista, int l, int r){
    int j;
    for(int i = l+1; i <= r; i++){
        Item t = lista[i];
        for(j = i; j > 0 && compareQS(t, lista[j-1]); j--){
            lista[j] = lista[j - 1];
        }
        lista[j] = t;
    }
}
int particiona(Item *lista, int l, int r){
    Item pivo = lista[r];
    int j = l;
    for(int i = l; i < r; i++){
        if(compareQS(lista[i], pivo)){
            swap(lista[i], lista[j]);
            j++;
        }
    }
    swap(lista[j], lista[r]);
    return j;
}
void quickSort(Item *lista, int l, int r){
    if(r-l <= 32)return;
    swap(lista[(l+r)/2], lista[r-1]);
    cswapQS(lista[l], lista[r-1]);
    cswapQS(lista[l], lista[r]);
    cswapQS(lista[r-1], lista[r]);
    int mid = particiona(lista, l, r);
    quickSort(lista, l, mid-1);
    quickSort(lista, mid+1, r);
}
int particionaQSL(Item *lista, int l, int r){
    Item pivo = lista[r];
    int j = l;
    for(int i = l; i < r; i++){
        if(compareQSL(lista[i], pivo)){
            swap(lista[i], lista[j]);
            j++;
        }
    }
    swap(lista[j], lista[r]);
    return j;
}
void quickSelect(Item *lista, int l, int r, int i){
    cswapQSL(lista[(l + r) / 2], lista[r]);
    cswapQSL(lista[l], lista[(l + r) / 2]);
    cswapQSL(lista[r], lista[(l + r) / 2]);
    int meio = particionaQSL(lista, l, r);
    if(meio > i) quickSelect(lista, l, meio - 1, i);
    if(meio < i) quickSelect(lista, meio + 1, r, i);
}
int main(){
    int N;
    scanf("%d", &N);
    No *lista = malloc(10000002 * sizeof(No));
//    No lista[102];
    int tam = 0;
    No no;
    while(1){
        int verifica = scanf("%lld %lld", &no.codigo, &no.qualidade);
        if(verifica == EOF) break;
        else lista[tam++] = no;
//        if(tam > 6) break;
    }
    quickSelect(lista, 0, tam-1, N-1);
    quickSort(lista, 0, N-1);
    insertionSort(lista, 0, N-1);
    for(int i = 0; i <= N-1; i++){
        printf("%lld %lld\n", lista[i].codigo, lista[i].qualidade);
    }
    return 0;
}
```

<!-- tabs:end -->

