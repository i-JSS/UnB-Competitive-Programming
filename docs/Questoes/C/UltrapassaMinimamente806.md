<center>

# Estrutura de Dados 1

</center>

---

# Ultrapassa Minimamente

<!-- tabs:start -->

#### **Questão**

 exercício 7 da primeira prova de algoritmos 1 de 2018/2 http://www.brunoribas.com.br/aed1/provas/1/20182.pdf Fazer um programa em C para ler uma sequência (não necessariamente ordenada) com uma quantidade arbitrária de números inteiros positivos do teclado e armazená-los em um vetor v . O último número lido é o zero, o qual não deve fazer parte dos valores de v . Além desses, mais um único valor deve ser lido, o que representa o limite de soma. Após a leitura dos dados, o programa deve imprimir apenas os últimos números de cada subsequência de v cuja soma de seus valores ultrapassa minimamente o limite de soma. Uma vez ultrapassado esse limite, uma nova subsequência deve ser iniciada a partir do valor que segue o último da subsequência identificada no momento. Ao final do processamento completo seu programa deverá imprimir o valor que ultrapassa minimamente o limite da soma ao contrário que da forma que é processado, e esses números NÃO podem ser armazenados em um vetor. Veja um exemplo de execução abaixo: Exemplo de Entrada: 33 51 23 94 66 28 11 73 19 8 31 0 90 

**Saída**

 para o exemplo: 19 28 94 23 No exemplo acima, o valor 23 é o último da subsequência 33 51 23 , cuja soma é 107 , a qual minimamente ultrapassa o limite de soma 90 , sendo assim deverá ser impresso por último. Com isso, logo depois do valor 23 , tem início a verificação da soma dos valores de uma nova subsequência que começa com o número 94 . De cara, só o 94 já ultrapassa o limite 90 , sendo o penúltimo número a ser impresso, e assim por diante até que todo o vetor v seja processado. Note que você NÃO pode iniciar o processamento pelo fim do vetor v , pois, desta forma, o resultado seria diferente. \textit{\rightline{

Autor: Marcos Castilho, I/O e mojificação por Bruno Ribas }}

#### **Código**

```c
#include <stdio.h>
#include <stdlib.h>

int main() {
    int quantidade = 0;
    int *v = (int *)malloc(sizeof(int) * 200);

    scanf("%d", &v[quantidade]);
    while (v[quantidade] != 0) {
        quantidade++;

        if(quantidade%200 == 0){
            v = (int *)realloc(v, (quantidade + 200) * sizeof(int));
        }
        scanf("%d", &v[quantidade]);
    }

    int soma;
    scanf("%d", &soma);

    int num = 0, i = 0, vet = 0;
    int vetor[1000];

    while (i < quantidade) {
        num += v[i];
        if (num > soma) {
            vetor[vet] = v[i];
            vet++;
            num = 0;
        }
        i++;
    }

    for(int g = vet - 1; g >= 0; g--) {
        printf("%d\n", vetor[g]);
    }

    return 0;
}
```

<!-- tabs:end -->

