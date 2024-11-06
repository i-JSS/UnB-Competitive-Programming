<center>

# Estrutura de Dados 1

</center>

---

# String ao contrário

<!-- tabs:start -->

#### **Questão**

 Faça um programa que leia uma string e a imprima ao contrário. 

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

 odepipelelarap 

Autor: John L. Gardenghi 

#### **Código**

```c
#include <stdio.h>
#include <string.h>

void rec(char *str, int total) {
    if(total >= 0){
        printf("%c", str[total]);
        rec(str, total - 1);
    }
}

int main() {
    char string[501];
    scanf("%s", string);
    int tam = strlen(string);
    rec(string, tam-1);
    printf("\n");
    return 0;
}
```

<!-- tabs:end -->

