<center>

# Estrutura de Dados 1

</center>

---

# Soma dos dígitos

<!-- tabs:start -->

#### **Questão**

 Dado um inteiro não negativo, sua tarefa é escrever uma função recursiva que calcule a soma de todos os dígitos deste número. Atenção : Você não pode usar laços na sua solução. 

**Entrada**

 A entrada é composta por uma única linha contendo um inteiro não negativo n ( 0 ≤ n ≤ 10 12 ). 

**Saída**

 A saída deve conter uma única linha com a soma dos dígitos do inteiro dado na entrada. 

**Exemplo de Entrada 1**

 126 

**Exemplo de Saída 1**

 9 

**Exemplo de Entrada 2**

 49 

**Exemplo de Saída 2**

 13 

Autor: John L. Gardenghi (adaptado do problema sumDigits do codingbat.com) 

#### **Código**

```c
#include <stdio.h>

void getNum(char *num, int indice, int resultado){
    if(num[indice] != '\0'){
        resultado += num[indice] - '0';
        getNum(num, indice+1, resultado);
    }
    else printf("%d", resultado);

}

int main(){
    char num[1000];
    scanf("%s", num);
    getNum(num, 0, 0);
    return 0;
}

```

<!-- tabs:end -->

