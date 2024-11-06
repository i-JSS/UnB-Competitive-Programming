<center>

# Estrutura de Dados 1

</center>

---

# Problema: Troca

<!-- tabs:start -->

#### **Questão**

 Troca Escreva uma fun¸ c˜ ao v o i d swap ( i n t ∗ a , i n t ∗ b ) ; que recebendo dois n´ umeros n´ umeros por referˆ encia a e b , troque os valores destas vari´ aveis. Aten¸ c˜ ao: sua submiss˜ ao dever´ a conter somente esta fun¸ c˜ ao. 

**Entrada**

 O seu programa ir´ a receber dois valores, como j´ a especificados acima. Ele n˜ ao far´ a nenhuma leitura da entrada padr˜ ao. Sa´ ıda A sua fun¸ c˜ ao n˜ ao deve imprimir na sa´ ıda padr˜ ao e nem retornar nada. Exemplos 

**Exemplo de entrada**

 Conte´ udo na entrada padr˜ ao: 100 150 Sa´ ıda para o exemplo de entrada acima Antes : 100 150 Depois : 150 100

#### **Código**

```c
#include <stdio.h>

void swap(int *a, int *b){  //Recebe 2 ponteiros para inteiros
                            //Se passar ponteiros pode modificar o conteudo fora da funçao
    int temp = *a;  //Acessa o valor de a e define como temp
    *a = *b;
    *b = temp;
}

```

<!-- tabs:end -->

