<center>

# Estrutura de Dados 2

</center>

---

# Percursos transversais

<!-- tabs:start -->

#### **Questão**

 Um problema comum em estrutura de dados é determinar o percurso transversal de uma árvore binária. Há tres formas clássicas de fazer isto: Prefixa: Você deve visitar a raiz, sub-árvore esquerda e sub-árvore direita. Infixa: Você deve visitar a sub-árvore esquerda, a raiz e a sub-árvore direita. Posfixa: Você deve visitar a sub-árvore esquerda, a sub-árvore direita e a raiz. Veja a figura abaixo: Árvore binária O percurso prefixo, infixo e posfixo são, respectivamente 𝐴 𝐵 𝐶 𝐷 𝐸 𝐹 , 𝐶 𝐵 𝐴 𝐸 𝐷 𝐹 and 𝐶 𝐵 𝐸 𝐹 𝐷 𝐴 . Neste problema, você deve computar a forma posfixa da árvore dados os percursos infixo e prefixo 

**Entrada**

 A primeira linha de entrada contém um número positivo 𝐶 ( 𝐶 ≤ 2000 ), que indica o número de casos de teste. Seguem C linhas, uma para cada caso de teste. Cada caso de teste inicia com um número 𝑁 ( 1 ≤ 𝑁 ≤ 52 ), o número de nodos da árvore binária. Depois haverá duas strings 𝑆 1 e 𝑆 2 que descrevem o percurso prefixo e infixo da árvore. Os nodos da árvore são nomeados com diferentes caracteres dentro do intervalo 𝑎 . . 𝑧 e 𝐴 . . 𝑍 . O valor de 𝑁 , 𝑆 1 e 𝑆 2 são separados por um espaço em branco. 

**Saída**

 Para cada conjunto de entrada, você deve imprimir uma linha contendo o percurso posfixo da corrente árvore. Exemplo 

**Entrada**

 3 3 xYz Yxz 3 abc cba 6 ABCDEF CBAEDF 

Yzx cba CBEFDA 

#### **Código**

```c
#include "stdio.h"
#include "string.h"

void posFixa(char* prefixa, char* infixa, int n) {
    int raiz = strchr(infixa, prefixa[0])-infixa;
    if(raiz != 0) posFixa(prefixa+1, infixa, raiz);
    if(raiz != n-1) posFixa(prefixa+raiz+1, infixa+raiz+1, n-raiz-1);
    printf("%c", prefixa[0]);
}

int main() {
    int tam;
    scanf(" %d", &tam);
    for(int i = 0; i < tam; i++) {
        int tamPalavra;
        scanf(" %d", &tamPalavra);
        char prefixa[tamPalavra+1];
        char infixa[tamPalavra+1];
        scanf(" %s %s", prefixa, infixa);
        posFixa(prefixa, infixa, tamPalavra);
        printf("\n");
    }

    return 0;
}

```

<!-- tabs:end -->

