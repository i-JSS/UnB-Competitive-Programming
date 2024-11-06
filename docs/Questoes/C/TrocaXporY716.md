<center>

# Estrutura de Dados 1

</center>

---

# Troca X por Y

<!-- tabs:start -->

#### **Questão**

 Sua tarefa nesse exercício é dada uma string, imprimir na tela a string trocando todas as ocorrências de ‘x’ por ‘y’. Atenção : Você não pode usar laços na sua solução. 

**Entrada**

 A entrada é composta por uma única linha contendo uma string (sem espaços) com, no máximo, 80 caracteres. 

**Saída**

 A saída deve conter uma única linha com a string lida, de tal forma que toda ocorrência de ‘x’ seja substituída por ‘y’. 

**Exemplo de Entrada 1**

 codex 

**Exemplo de Saída 1**

 codey 

**Exemplo de Entrada 2**

 xxhixx 

**Exemplo de Saída 2**

 yyhiyy 

**Exemplo de Entrada 3**

 xhixhix 

**Exemplo de Saída 3**

 yhiyhiy \textit{\rightline{

Autor: John L. Gardenghi (adaptado do problema changeXY do codingbat.com) }}

#### **Código**

```c
#include <stdio.h>

void trocar(char *str){
    if(*str != '\0'){
        if(*str == 'x') *str = 'y';
        trocar(str+1);
    }
}

int main(){
    char str[100];
    scanf("%s", str);
    trocar(str);
    printf("%s\n",str);
    return 0;
}

```

<!-- tabs:end -->

