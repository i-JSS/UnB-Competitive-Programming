<center>

# Estrutura de Dados 2

</center>

---

# Menores Placas

<!-- tabs:start -->

#### **Questão**

 Bruno Ribas 

**Preâmbulo**

 Joãozinho adora ler os números das placas dos carros, e a cada placa que lê grita no carro, assustando a todos, o número que leu. Claro, Joãozinho faz isso durante as viagens em família. Ultimamente a família pega o carro e dirige sem rumo por horas a fio, pois não podem passear em shoppings, e a diversão foi colocar todo mundo no carro e viajar pelas estradas do país. Leônidas, o pai de Joãozinho, resolveu desafiar seu filho. Toda vez que ele ler uma placa deveria anotar, e não gritar, e de vez em quando o pai iria perguntar quais eram as N menores placas lidas até o momento. Essa brincadeira ficou tão popular na família que todos começaram a prestar atenção nas placas e começaram a "trucar" as repostas de Joãozinho. Para garantir que Joãozinho não esteja trapaceando, Leônidas pediu a você que implementasse um programa de computador que responda os valores corretamente. As placas serão inseridas por Gertrudes, mãe de Joãozinho. 

**Entrada**

 A entrada é composta por um único caso de testes com diversas linhas. Cada linha é composta por dois números, o primeiro número, 𝑂 , representa a operação sendo feita. Quando 𝑂 for 1 significa que após será enviado um número inteiro 𝑃 𝑖 ( 0 ≤ 𝑃 𝑖 ≤ 10 7 ) representando uma nova placa identificada pela família. Quando 𝑂 for 2 , o número seguinte que acompanha 𝑇 𝑖 ( 1 ≤ 𝑇 𝑖 ≤ 100 ) representando a pergunta que deve ser respondida: Liste as 𝑇 𝑖 menores placas lidas até o momento. A entrada termina em EOF . Limites 𝑃 (quantidade de placas) - indeterminado! 𝑃 𝑖 (numeral de cada placa) 0 ≤ 𝑃 𝑖 ≤ 10 7 não existem placas repetidas 𝑇 𝑖 (quantidade de placas a imprimir) 1 ≤ 𝑇 𝑖 ≤ 100 nunca será pedido para imprimir mais que 100 placas. 

**Saída**

 A saída é composta por diversas linhas. Sempre que 𝑂 for 2 você deve imprimir uma única linha contendo as 𝑇 𝑖 menores placas identificadas pela família até o momento. 



**Exemplo de entrada**

 1 1365271 1 9164517 1 5782846 2 2 1 1153896 1 3641547 2 2 

**Exemplo de saída**

 1365271 5782846 1153896 1365271 

**Exemplo de entrada**

 1 9019747 1 3629786 1 7091927 2 1 1 2013733 1 4784225 1 7865835 1 7145336 1 3536931 1 9584045 1 1967593 2 7 

**Exemplo de saída**

 3629786 1967593 2013733 3536931 3629786 4784225 7091927 7145336 

**Exemplo de entrada**

 1 5 2 1 1 4 2 2 

**Exemplo de saída**

 5 4 5 

#### **Código**

```c

#include <stdio.h>
#include <stdlib.h>
#define swap(a, b) {int t = a; a = b; b = t;}
int *VETOR, TAMANHO;
void fixup(int *placas, int i){
    while(i > 1 && placas[i/2] > placas[i]){
        swap(placas[i], placas[i/2]);
        i/=2;
    }
}
void fixdown(int *placas, int tam, int i){
    while(i*2 <= tam){
        int menor = i*2;
        if(menor < tam && placas[menor] > placas[menor + 1]) menor++;
        if(placas[i] <= placas[menor]) break;
        swap(placas[i], placas[menor]);
        i = menor;
    }
}
void inserirHeap(int *VETOR, int p){
    VETOR[++TAMANHO] = p;
    fixup(VETOR, TAMANHO);
}
int removerMinimo(int *VETOR){
    int menor = VETOR[1];
    VETOR[1] = VETOR[TAMANHO--];
    fixdown(VETOR, TAMANHO, 1);
    return menor;
}
int main() {
    VETOR = malloc(sizeof(int)*1000000);
    int *lista = malloc(sizeof(int) * 10000000);
    int comando, num;
    while (scanf("%d %d", &comando, &num) != EOF) {
        if(comando == 1) inserirHeap(VETOR, num);
        else {
            for(int j = 0; j < num; j++) lista[j] = removerMinimo(VETOR);
            for(int j = 0; j < num; j++) {
                printf("%d ", lista[j]);
                inserirHeap(VETOR, lista[j]);
            }
            printf("\n");
        }
    }
    return 0;
}

```

<!-- tabs:end -->

