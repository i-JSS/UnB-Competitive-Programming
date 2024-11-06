<center>

# Estrutura de Dados 1

</center>

---

# Botas

<!-- tabs:start -->

#### **Questão**

 A divisão de Suprimentos de Botas e Calçados do Exército comprou um grande número de paresde botas de vários tamanhos para seus soldados. No entanto, por uma falha de empacotamento da fábrica contratada, nem todas as caixas entregues continham um par de botas correto, com duasbotas do mesmo tamanho, uma para cada pé. O sargento mandou que os recrutas retirassem todasas botas de todas as caixas para reembalá-las, desta vez corretamente. Quando o sargento descobriu que você sabia programar, ele solicitou com a gentileza habitual que você escrevesse um programa que, dada a lista contendo a descrição de cada bota entregue, determina quantos pares corretos de botas poderão ser formados no total. 

**Entrada**

 Cada uma das linhas descreve uma bota, contendo um número inteiro M e uma letra L , separados por um espaço em branco. M indica o número do tamanho da bota ( 30 ≤ M ≤ 60 ) e L indica o pé da bota: L= ' D ' indica que a bota é para o pé direito, L= ' E ' indica que a bota é para o pé esquerdo. A entrada termina com EOF. 

**Saída**

 Seu programa deve imprimir uma única linha contendo um único número inteiro indicando o número total de pares corretos de botas que podem ser formados. 

**Exemplo de Entrada 1**

 40 D 41 E 41 D 40 E 

**Exemplo de Saída 1**

 2 

**Exemplo de Entrada 2**

 38 E 39 E 40 D 38 D 40 D 37 E 

**Exemplo de Saída 2**

 1 

Autor: Olimpíada Brasileira de Informática, Fase 1, 2017 (mojificação por John L. Gardenghi) 

#### **Código**

```c
#include <stdio.h>

typedef struct Bota{
    int num;
    char ori;
} Bota;

int main(){
    Bota botas[100];
    int i = 0;
    int contador[61][2] = {0};

    while (1) {
        Bota temp;
        int resultado = scanf("%d %c", &temp.num, &temp.ori);
        if (resultado == EOF) break;
        botas[i] = temp;
        i++;
        contador[temp.num][temp.ori - 'D']++;
    }

    int numeroPares = 0;

    for (int tamanho = 30; tamanho <= 60; tamanho++) {
        numeroPares += (contador[tamanho]['E' - 'D'] < contador[tamanho]['D' - 'D']) ? contador[tamanho]['E' - 'D'] : contador[tamanho]['D' - 'D'];
    }

    printf("%d\n", numeroPares);
    return 0;
}
```

<!-- tabs:end -->

