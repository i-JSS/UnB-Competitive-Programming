<center>

# Algoritmos e Programação de Computadores

</center>

---

# Tomadas

<!-- tabs:start -->

#### **Questão**

 A Olimpíada Internacional de Informática (IOI, no original em inglês) é a mais prestigiada competição de programação para alunos de ensino médio; seus aproximadamente 300 competidores se reúnem em um país diferente todo ano para os dois dias de prova da competição. Naturalmente, os competidores usam o tempo livre para acessar a Internet, programar e jogar em seus notebooks, mas eles se depararam com um problema: o saguão do hotel só tem uma tomada. Felizmente, os quatro competidores da equipe brasileira da IOI trouxeram cada um uma régua de tomadas, permitindo assim ligar vários notebooks em uma tomada só; eles também podem ligar uma régua em outra para aumentar ainda mais o número de tomadas disponíveis. No entanto, como as réguas têm muitas tomadas, eles pediram para você escrever um programa que, dado o número de tomadas em cada régua, determina quantas tomadas podem ser disponibilizadas no saguão do hotel. 

**Entrada**

 A entrada consiste de uma linha com quatro inteiros positivos T 1 , T 2 , T 3 , T 4 , indicando o número de tomadas de cada uma das quatro réguas. 

**Saída**

 Seu programa deve imprimir uma única linha contendo um único número inteiro, indicando o número máximo de notebooks que podem ser conectados num mesmo instante. Restrições 2 ≤ T i ≤ 6 Exemplos 

**Entrada**

 2 4 3 2 

**Saída**

 8 

**Entrada**

 6 6 6 6 

**Saída**

 21 

**Entrada**

 2 2 2 2 

**Saída**

 



#### **Código**

```c
#include <stdio.h>
#include <stdlib.h>

int main() {
    int A, B, C, D;
    scanf("%d%d%d%d", &A, &B, &C, &D);
    printf("%d\n", (A-1 + B-1 +C-1+ D));
    return 0;
}
```

<!-- tabs:end -->

