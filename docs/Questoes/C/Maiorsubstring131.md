<center>

# Estrutura de Dados 1

</center>

---

# Maior substring

<!-- tabs:start -->

#### **Questão**

 Sua tarefa nesse exercício é, dadas duas cadeias de caracteres str e sub , determinar recursivamente qual a maior subcadeia de str que começa e termina por sub . Atenção : Você não pode usar laços na sua solução. 

**Entrada**

 A entrada é composta por duas linhas. A primeira linha contém str , que pode ter tamanho entre zero e 100, e a segunda linha contém sub , que pode ter tamanho entre 1 e 100. 

**Saída**

 A saída deve conter uma única linha com o tamanho da maior subcadeia de str que começa e termina por sub . 

**Exemplo de Entrada 1**

 catcowcat cat 

**Exemplo de Saída 1**

 9 

**Exemplo de Entrada 2**

 catcowcat cow 

**Exemplo de Saída 2**

 3 

**Exemplo de Entrada 3**

 cccatcowcatxx cat 

**Exemplo de Saída 3**

 9 \textit{\rightline{

Autor: John L. Gardenghi (adaptado do problema strDist do codingbat.com) }}

#### **Código**

```c
#include <stdio.h>
#include <string.h>

int maiorSubstring(char str[], char sub[], int tam) {
    if (tam == 0) return 0;

    if (strncmp(str, sub, strlen(sub)) == 0 && strncmp(str + tam - strlen(sub), sub, strlen(sub)) == 0){
        return tam;
    }

    int opcao1 = maiorSubstring(str + 1, sub, tam-1);
    int opcao2 = maiorSubstring(str, sub, tam-1);

    return (opcao1 > opcao2) ? opcao1 : opcao2;
}

int main() {
    char str[101];
    char sub[101];

    scanf("%s", str);
    scanf("%s", sub);

    int resultado = maiorSubstring(str, sub, strlen(str));
    printf("%d\n", resultado);

    return 0;
}

```

<!-- tabs:end -->

