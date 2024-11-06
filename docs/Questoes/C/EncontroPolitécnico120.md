<center>

# Estrutura de Dados 2

</center>

---

# Encontro Politécnico

<!-- tabs:start -->

#### **Questão**

 Dois professores (PA e PB) 1 combinaram de encontrar-se no Centro Politécnico (CP) às 15h00 numa quarta-feira. Como os professores são grandes estudiosos de movimentos retilíneos uniformes, pensaram em aplicar um de seus estudos mais recentes. Os dois professores dividiram o CP em um grande quadriculado. A cada passo, cada professor escolhe uma direção (Norte, Sul, Leste ou Oeste) e anda até o quadrado imediatamente vizinho na direção escolhida. O quadriculado do CP é um plano cartesiano com origem em ( 1 , 1 ) como sendo o limite inferior esquerdo e as direções Norte e Sul andam no eixo Y, e as direções Leste e Oeste no eixo X. As direções Norte e Leste incrementam a posição de seus respectivos eixos e Sul e Oeste fazem o oposto. Dada uma sequência de passos, você deve dizer se os professores se encontraram em algum momento, i.e, se eles ficaram no mesmo quadrado ao mesmo tempo, se algum professor saiu do CP ou se eles não se encontraram. 

**Entrada**

 A primeira linha da entrada contém dois inteiros 𝑁 e 𝑀 que indicam respectivamente o número de colunas e o número de linhas do CP ( 1 ≤ 𝑁 , 𝑀 ≤ 10 5 ). A segunda linha contém um inteiro P ( 0 ≤ 𝑃 ≤ 1000 ) que indica quantos movimentos cada professor fez. Depois são apresentadas 𝑃 linhas contendo dois números inteiros 𝐴 e 𝐵 , indicando a direção tomada pelos professores 𝑃 𝐴 e 𝑃 𝐵 , respectivamente, naquele passo. Os inteiros 𝐴 e 𝐵 podem assumir os seguintes valores: 1 (Norte), 2 (Sul), 3 (Leste) e 4 (Oeste). O professor 𝑃 𝐴 inicia seu trajeto sempre na posição ( 1 , 1 ) e o professor 𝑃 𝐵 na posição ( 𝑁 , 𝑀 ) . 

**Saída**

 Seu programa deve imprimir: Caso os professores tenham se encontrado: as coordenadas do encontro e o passo em que ocorreu. Caso o(s) professor(es) tenha(m) saído do CP: as coordenadas em que saíram e o passo em que ocorreu. Se ambos professores saíram no mesmo passo imprima apenas a informação sobre o professor PA. Caso nenhuma das anteriores ocorra, imprimir: “Nao se encontraram”. Verifique os exemplos para entender melhor o formato da saída. Exemplos 

**Exemplo de entrada**

 5 5 4 3 2 

3 2 3 4 

**Saída**

 para o exemplo de entrada acima Nao se encontraram 

**Exemplo de entrada**

 5 5 4 3 2 3 2 3 2 3 2 

**Saída**

 para o exemplo de entrada acima Encontraram-se na posicao (5,1) no passo 4 

**Exemplo de entrada**

 5 5 4 1 2 1 2 4 1 1 4 

**Saída**

 para o exemplo de entrada acima PA saiu na posicao (0,3) no passo 3 

Autor: Bruno Ribas 1. A saber: PA é o prof. Castellone, e PB é o prof. Anthov, ambos do DINF

#### **Código**

```c
#include <stdio.h>

int main() {
    int n, m, k;
    scanf("%d %d %d", &n, &m, &k);
    int x1 = 1, y1 = 1, x2 = n, y2 = m;

    for(int i = 1; i <= k; i++) {
        int temp1, temp2;
        scanf("%d %d", &temp1, &temp2);

        if(temp1 == 1) y1++;
        else if(temp1 == 2) y1--;
        else if(temp1 == 3) x1++;
        else if(temp1 == 4) x1--;

        if(temp2 == 1) y2++;
        else if(temp2 == 2) y2--;
        else if(temp2 == 3) x2++;
        else if(temp2 == 4) x2--;

        if(x1 == x2 && y1 == y2){
            printf("Encontraram-se na posicao (%d,%d) no passo %d\n", x1, y1, i);
            return 0;
        }
        if(x1 < 1 || x1 > n || y1 < 1 || y1 > m){
            printf("PA saiu na posicao (%d,%d) no passo %d\n", x1, y1, i);
            return 0;
        }
        if(x2 < 1 || x2 > n || y2 < 1 || y2 > m){
            printf("PB saiu na posicao (%d,%d) no passo %d\n", x2, y2, i);
            return 0;
        }
    }
    printf("Nao se encontraram\n");
    return 0;
}

```

<!-- tabs:end -->

