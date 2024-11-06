<center>

# Estrutura de Dados 1

</center>

---

# String ao contrário

<!-- tabs:start -->

#### **Questão**

 Faça um programa que leia uma string e a imprima ao contrário. Atenção : Você não pode usar laços na sua solução. 

**Entrada**

 A entrada é composta por uma única linha contendo uma string de, no máximo, 500 caracteres, contendo letras (maiúsculas e minúsculas, não acentuadas) e números. 

**Saída**

 A saída deve conter uma única linha com a string impressa ao contrário. 

**Exemplo de Entrada 1**

 amor 

**Exemplo de Saída 1**

 roma 

**Exemplo de Entrada 2**

 paralelepipedo 

**Exemplo de Saída 2**

 odepipelelarap \textit{\rightline{

Autor: John L. Gardenghi }}

#### **Código**

```c
#include <stdio.h>
#include <string.h>

void troca(char *str,int  indice){
    if(indice >= 0){
        if(str[indice]!='\0') printf("%c", str[indice]);
        troca(str, indice-1);
    }
}

int main(){
    char str[600];
    fgets(str, sizeof(str), stdin);
    int indiceInicial = strlen(str) - 2;
    if(indiceInicial >= 0){
        troca(str, indiceInicial);
    }
    printf("\n");
    return 0;
}
```

<!-- tabs:end -->

