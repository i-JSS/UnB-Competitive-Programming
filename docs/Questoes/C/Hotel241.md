<center>

# Algoritmo e Programação de Computadores

</center>

---

# Hotel

<!-- tabs:start -->

#### **Questão**

 O hotel da Colônia de Férias dos Professores está com uma promoção para as férias de julho. A promoção é válida para quem chegar a partir do dia 1 de julho e sair no dia 1 de agosto. O preço da diária do hotel é menor para quem chegar mais cedo, e vai aumentando a cada dia. Mais precisamente, a promoção funciona assim: A diária do hotel para cada quem chegar no dia 1 é Reais. Assim, 𝐷 quem chegar no dia 1 vai pagar um total de 31 × Reais. 𝐷 A diária do hotel aumenta reais por dia. Ou seja, a diária é + 𝐴 𝐷 𝐴 reais para quem chegar no dia 2; + 2× reais no dia 3; + 3× 𝐷 𝐴 𝐷 𝐴 reais no dia 4 e assim por diante. Note que quem chegar no dia 2 vai pagar um total de 30 × ( + ) 𝐷 𝐴 reais; quem chegar no dia 3 vai pagar um total de 29 × ( + 2 × ) 𝐷 𝐴 reais, e assim por diante. Bruno gosta muito da professora Vilma, e para agradá-la quer ajudá-la a planejar suas férias, escrevendo um programa para calcular o total (em reais) que a professora Vilma vai gastar, dependendo do dia em que chegar no hotel. 

**Entrada**

 A primeira linha contém um inteiro , o valor da diária no dia 1. 𝐷 A segunda linha contém um inteiro , o aumento da diária a cada 𝐴 dia. A terceira linha contém um inteiro , o dia de chegada no 𝑁 hotel. 

**Saída**

 Seu programa deve produzir uma única linha, contendo um único inteiro, que deve ser o valor total a ser pago ao hotel pela estadia. Restrições (de entrada, ou seja, seu código NÃO será testado com valores fora dos intervalos abaixo) 1 ≤ ≤ 1000 𝐷 1 ≤ ≤ 10001 ≤ ≤ 31 𝐴 𝑁 

**Exemplo de entrada**

 1 100 10 

Exemplo de saída 1 3100 Explicação do exemplo 1: Como a chegada é no dia 1, o valor da diária com a promoção é 100. Do dia 1 ao dia 31 são 31 diárias. Assim, o total a pagar é 31 × 100. 

**Exemplo de entrada**

 2 100 20 15 Exemplo de saída 2 6460 Explicação do exemplo 2: Como a chegada é no dia 15, o valor da diária com a promoção é 100 + 14 × 20 = 380. Do dia 15 ao dia 31 são 17 diárias. Assim, o total a pagar é 17 × 380 = 6460. 

**Exemplo de entrada**

 3 100 5 16 Exemplo de saída 3 2720 Explicação do exemplo 3: Como a chegada é no dia 16, o valor da diária com a promoção é 100 + 15 × 5 = 175. Do dia 16 ao dia 31 são 16 diárias. Assim, o total a pagar é 16 × 170 = 2800. 

Autor: OBI 2022, adaptado por John L. 

#### **Código**

```c
#include <stdio.h>
#include <stdlib.h>

int main() {
    int D, A, N;
    scanf("%d %d %d", &D, &A, &N);
    printf("%d\n", (D+(N-1)*A) * (31-N+1));
    return 0;
}
```

<!-- tabs:end -->

