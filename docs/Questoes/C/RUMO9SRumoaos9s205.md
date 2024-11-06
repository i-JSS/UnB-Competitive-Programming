<center>

# Estrutura de Dados 1

</center>

---

# RUMO9S Rumo aos 9s

<!-- tabs:start -->

#### **Questão**

 Um truque bem conhecido para descobrir se um inteiro N é um múltiplo de nove é computar a soma S dos seus dígitos. Se S é um múltiplo de nove, então N também é. Este é um teste recursivo e a profundidade da recursão necessária para obter a resposta para o número N é chamada o grau-9 de N. Sua tarefa é, dado um inteiro positivo N, determinar se ele é um múltiplo de nove e, caso ele seja, qual o seu grau-9. 

**Entrada**

 A entrada é um arquivo tal que cada linha contém um inteiro positivo. Uma linha contendo o número 0 indica o fim da entrada. Os números fornecidos na entrada possuem até 1000 dígitos. 

**Saída**

 Saida A saída do programa deve indicar, para cada número da entrada, se ele é um múltiplo de nove e, caso ele seja, o seu grau-9. Veja o exemplo de saída para saber o formato esperado da saída. 

**Exemplo de Entrada 999999999999999999999**

 9 9999999999999999999999999999998 0 Exemplo de Saída: 999999999999999999999 is a multiple of 9 and has 9-degree 3. 9 is a multiple of 9 and has 9-degree 1. 9999999999999999999999999999998 is not a multiple of 9. 

Autor: David Déharbe adaptado por Sérgio Cipriano e João Cunha 

#### **Código**

```c
#include <stdio.h>

int somaDosDigitos(int n) {
    int soma = 0;
    while (n > 0) {
        soma += n % 10;
        n /= 10;
    }
    return soma;
}

int grau9(int n) {
    int grau = 0;
    while (n >= 10) {
        n = somaDosDigitos(n);
        grau++;
    }
    return grau;
}

void rumo9s(char *num) {
    if (num[0] - '0' != 0) {
        int j = 0;
        for (int i = 0; num[i] != '\0'; i++) {
            printf("%c", num[i]);
            j += num[i] - '0';
        }

        int original_j = j;
        int grau = grau9(j);

        if (original_j % 9 == 0)
            printf(" is a multiple of 9 and has 9-degree %d.\n", grau+1);
        else
            printf(" is not a multiple of 9.\n");

        scanf("%s", num);
        rumo9s(num);
    }
}

int main() {
    char num[1001];
    scanf("%s", num);
    rumo9s(num);

    return 0;
}

```

<!-- tabs:end -->

