<center>

# Estrutura de Dados 1

</center>

---

# Move os Xs

<!-- tabs:start -->

#### **Questão**

 Dada uma string, faça um programa que compute uma nova string de forma que todos os caracteres ‘x’ minúsculos sejam movidos para o final. Atenção : Você não pode usar laços na sua solução. 

**Entrada**

 A entrada é composta por uma única linha contendo uma string de, no máximo, 100 caracteres. 

**Saída**

 A saída deve conter uma única linha com a nova string. 

**Exemplo de Entrada 1**

 xxre 

**Exemplo de Saída 1**

 rexx 

**Exemplo de Entrada 2**

 xxhixx 

**Exemplo de Saída 2**

 hixxxx 

**Exemplo de Entrada 3**

 xhixhix 

**Exemplo de Saída 3**

 hihixxx 

Autor: John L. Gardenghi (adaptado do problema endX do codingbat.com) 

#### **Código**

```c
#include <stdio.h>

void swap(char *str, int a, int b){
    char temp = str[a];
    str[a] = str[b];
    str[b] = temp;
}

void organizadora(char *str, int indice){
    if(str[indice] != '\0'){
        if(str[indice] == 'x' && str[indice+1] != '\0'){
            if(str[indice+1] == 'x'){
                organizadora(str, indice+2);
            }
            else{
                swap(str, indice, indice+1);
            }
        }
        organizadora(str, indice+1);
    }
}

int main(){
    char str[200];
    scanf(" %[^\n]", str);
    organizadora(str, 0);
    organizadora(str, 0);
    organizadora(str, 0);
    organizadora(str, 0);
    organizadora(str, 0);
    organizadora(str, 0);
    printf("%s\n", str);
    return 0;
}

```

<!-- tabs:end -->

