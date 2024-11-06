<center>

# Algoritmos e Programação de Computadores

</center>

---

# Distância de Manhattan

<!-- tabs:start -->

#### **Questão**

 Maria é uma moradora de Nlogópolis, uma cidade na Nlogônia que tem uma característica muito interessante: todas as ruas da cidade ou são orientadas no sentido norte-sul ou são orientadas no sentido leste-oeste. Isso significa que, dadas duas ruas, ou elas são paralelas ou elas são perpendiculares entre si. Todas as ruas da cidade são de mão dupla e é possível seguir em qualquer direção em um cruzamento. Agora Maria está atrasada para uma reunião e precisa de sua ajuda. Dadas as coordenadas iniciais de Maria e da reunião, determine o número mínimo de cruzamentos que Maria deve atravessar para chegar ao seu destino. Esse número inclui o cruzamento onde ocorrerá a reunião mas não inclui a posição inicial de Maria. 

**Entrada**

 A única linha da entrada contém quatro inteiros, X m , Y m , X r , Y r , indicando as coordenadas de Maria ( X m , Y m ) e da reunião ( X r , Y r ). O ponto de partida de Maria nunca será igual ao local da reunião, ou seja, pelo menos uma das coordenadas será diferente. 

**Saída**

 Seu programa deve imprimir uma única linha contendo um único inteiro: o número mínimo de cruzamentos que Maria precisa atravessar para chegar até o local da reunião. Restrições 0 ≤ X m , Y m ≤ 1000 0 ≤ X r , Y r ≤ 1000 Exemplos 

**Entrada**

 0 0 5 6 

**Saída**

 11 

**Entrada**

 52 75 120 75 

**Saída**

 

#### **Código**

```c
#include <stdio.h>
#include <stdlib.h>

int main() {
    int Xm, Ym, Xr, Yr;
    scanf("%d %d %d %d", &Xm, &Ym, &Xr, &Yr);
    printf("%d\n", abs(Xr - Xm) + abs(Yr - Ym));
    return 0;
}

```

<!-- tabs:end -->

