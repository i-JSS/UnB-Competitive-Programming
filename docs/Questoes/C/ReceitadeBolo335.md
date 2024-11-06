<center>

# Algoritmos e Programação de Computadores

</center>

---

# Receita de Bolo

<!-- tabs:start -->

#### **Questão**

 João deseja fazer bolos para seus amigos, usando uma receita que indica que devem ser usadas 2 xícaras de farinha de trigo, 3 ovos e 5 colheres de sopa de leite. Em casa ele tem A xícaras de farinha de trigo, B ovos e C colheres de sopa de leite. João não tem muita prática com a cozinha, e portanto ele só se arriscará a fazer medidas exatas da receita de bolo (por exemplo, se ele tiver material su?ciente para fazer mais do que 2 e menos do que 3 bolos, ele fará somente 2 bolos). Sabendo disto, ajude João escrevendo um programa que determine qual a quantidade máxima de bolos que ele consegue fazer. 

**Entrada**

 A entrada é dada em uma única linha, que contém três números inteiros A, B e C, indicando respectivamente o número de xícaras de farinha de trigo, o número de ovos e o número de colheres de sopa de leite que João tem em casa. 

**Saída**

 Seu programa deve imprimir uma única linha, contendo um único inteiro, a quantidade máxima de bolos que João consegue fazer. Restrições 1 ≤ A ≤ 100 1 ≤ B ≤ 100 1 ≤ C ≤ 100 Exemplos 

**Entrada**

 4 6 10 

**Saída**

 2 

**Entrada**

 4 6 9 

**Saída**

 

#### **Código**

```c
#include <stdio.h>

int main() {
    int a, b, c;

    scanf("%d %d %d", &a, &b, &c);

    int f = a / 2;
    int o = b / 3;
    int l = c / 5;

    int min_bolos = f;
    if (o < min_bolos) min_bolos = o;
    if (l < min_bolos) min_bolos = l;
    
    printf("%d\n", min_bolos);
    return 0;
}

```

<!-- tabs:end -->

