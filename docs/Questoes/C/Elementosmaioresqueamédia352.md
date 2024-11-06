<center>

# Estrutura de Dados 2

</center>

---

# Elementos maiores que a média

<!-- tabs:start -->

#### **Questão**

 Elementos maiores que a m´ edia Fa¸ ca um programa em C que receba uma sequˆ encia de n´ umeros naturais e exiba todos os elementos que s˜ ao maiores que a m´ edia aritm´ etica desta sequˆ encia. Considere que a m´ edia aritm´ etica ´ e calculada da seguinte maneira: ¯ x = 1 n n X i =1 x i Considere tamb´ em que ¯ x ´ e um n´ umero inteiro. Caso n˜ ao haja na sequˆ encia nenhum elemento maior que ¯ x , exiba o n´ umero 0 . 

**Entrada**

 A primeira linha da entrada cont´ em um inteiro N significando o tamanho do vetor. A segunda linha possui N n´ umeros inteiros positivos V i , onde cada V i ´ e um elemento do vetor. Considere as seguintes restri¸ c˜ oes para os valores de entrada: • 10 ≤ N ≤ 10000 • 0 ≤ V i ≤ 1000000 Sa´ ıda A sa´ ıda ´ e composta por exatamente uma linha, contendo todos os elementos que s˜ ao maiores do que a m´ edia da sequˆ encia, onde cada elemento deve ser separado por espa¸ co, com exce¸ c˜ ao do ´ ultimo. Caso n˜ ao haja elementos maiores que a m´ edia, deve ser impresso em uma ´ unica linha o n´ umero 0 . Observe os casos de exemplos para melhor entendimento da sa´ ıda. Exemplos 

**Exemplo de entrada**

 10 3 5 7 0 1 4 2 0 4 4 Sa´ ıda para o exemplo de entrada 5 7 4 4 4 H´ a 10 elementos neste vetor. A m´ edia aritm´ etica desta sequˆ encia ser´ a: ¯ x = 1 10 10 X i =1 x i = 3 + 5 + 7 + 0 + 1 + 4 + 2 + 0 + 4 + 4 10 = 30 10 = 3 O segundo, terceiro, sexto, nono e d´ ecimo elementos s˜ ao maiores que a m´ edia. O segundo elemento ´ e o n´ umero 5 , o terceiro o 7 , o sexto o 4 , o nono o 4 e o d´ ecimo 4 .

Problema: Elements greater than the average Write a C program that, given a sequence of natural number, show all elements bigger than the arithmetic mean of this sequence. Consider that the arithmetic mean is calculated as following: ¯ x = 1 n n X i =1 x i Consider also that the ¯ x is an integer number. If there is no element bigger than ¯ x , show the number 0 . Input The first entry line contains an integer number N meaning the length of the array. The second entry line contains N positive integers numbers V i , that each V i is an element from the array. Check the restrictions for the input: • 10 ≤ N ≤ 10000 • 0 ≤ V i ≤ 1000000 Output Your program must show one line for the output, showing the elements that are bigger than the mean of the sequence, where each element must be split by space except the last one. If there is no elements bigger than the average, your program must show a single line with the number 0 on it. Check the example below for better understanding of the output. Examples 

**Exemplo de entrada**

 10 3 5 7 0 1 4 2 0 4 4 Sa´ ıda para o exemplo de entrada 5 7 4 4 4 There is 10 element in this array. The arithmetic mean of this sequence will be: ¯ x = 1 10 10 X i =1 x i = 3 + 5 + 7 + 0 + 1 + 4 + 2 + 0 + 4 + 4 10 = 30 10 = 3 The second, third, sixth, ninth and tenth elements are bigger than the mean. The second element is the number 5 , the third is 7 , the sixth is 4 , the ninth is 4 and the tenth is 4 .

#### **Código**

```c

#include <stdio.h>

int main(){
    long a;
    scanf("%ld", &a);
    long long lista[a+10];
    long long int soma = 0;
    for(int i = 0; i<a; i++){
        scanf("%lld", &lista[i]);
        soma += lista[i];
    }
    double media = soma/a;
    int verificador = 0;
    for(int i = 0; i<a; i++){
        if(lista[i] > media){
            verificador++;
            printf("%lld ", lista[i]);
        }
    }
    if(!verificador) printf("0");

    printf("\n");

    return 0;
}
```

<!-- tabs:end -->

