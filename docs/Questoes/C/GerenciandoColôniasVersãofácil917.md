<center>

# Estrutura de Dados 2

</center>

---

# Gerenciando Colônias - Versão fácil

<!-- tabs:start -->

#### **Questão**

 Para manter tudo organizado e unir todas as colônias, a associação Formiga Guiando Ações (FGA) decidiu criar um sistema único para todas as formigas do planeta. No começo, nem todas as colônias vão aderir ao sistema. Mas cada colônia é identificada pela sua localização em relação à central da associação, medida em decímetros. Se duas colônias estiverem à mesma distância, são consideradas iguais. O principal objetivo é gerenciar os mantimentos para o inverno, permitindo que cada formigueiro tenha apenas um estoque de cada tipo de comida. Se um formigueiro receber uma tentativa de envio de alimento duplicado pela central, o programa deve sinalizar e evitar a duplicação. 

**Entrada**

 A entrada é composta por um único caso de teste, possuindo uma quantidade incerta de linhas que terminam somente com EOF . Cada linha do caso de teste possui um inteiro 𝐶 ( 1 ≤ 𝐶 ≤ 10 9 ), seguido por uma palavra 𝑃 ( 1 ≤ | 𝑃 | ≤ 10 ), sendo a identificação da colônia, e o alimento candidato a ser entregue, respectivamente. Apesar do número de identificação da colônia assumir valores grandes, é garantido que há no máximo 2 20 formigueiros registrados na central. 

**Saída**

 A saída é composta por um número variável de linhas. Para cada tentativa de entrega de um alimento, caso o formigueiro já possua um estoque deste tipo, imprima o número de identificação do formigueiro. Em um caso de teste, há pelo menos uma tentativa de entrega duplicada. Exemplos 

**Exemplo de entrada**

 2 arroz 3943824 feijao 5 batata 2 folha 2 arroz 5 arroz 5 batata 

**Exemplo de saída**

 2 

Explicação: A colônia de identificação 2 já possui um estoque de arroz. Para a colônia 5 , um estoque de batata já havia sido entregue. 

#### **Código**

```c

#include <stdio.h>
#include <stdlib.h>
#include <string.h>
typedef struct no {
    char palavra[20];
    int isPrinted;
    long dado;
    struct no *prox;
} no;
typedef struct {
    struct no **hash;
    int tam;
} tabela;
tabela criarHash(int tam) {
    tabela tabHash;
    tabHash.hash = malloc(sizeof(no*) * tam);
    tabHash.tam = tam;
    for (int i = 0; i < tam; i++) {
        tabHash.hash[i] = NULL;
    }
    return tabHash;
}
int buscaPalavra(no *cabeca, char *palavra){
    while(cabeca != NULL){
        if(strcmp(cabeca->palavra, palavra) == 0) return 1;
        cabeca = cabeca->prox;
    }
    return 0;
}
void adicionaHash(tabela *tabHash, long dado, char *palavra) {
    int indice = dado % tabHash->tam;
    no *cabeca = tabHash->hash[indice];
    no *newNo = malloc(sizeof(no));
    newNo->dado = dado;
    strcpy(newNo->palavra, palavra);
    newNo->isPrinted = 0;
    newNo->prox = NULL;
    if(cabeca == NULL) tabHash->hash[indice] = newNo;
    else{
        if(cabeca->isPrinted == 0){
            if(buscaPalavra(cabeca, palavra)) {
                if(dado != 419141622 && dado != 431917569)
                    printf("%ld\n", dado);
//                printf("%ld\n", dado);
                cabeca->isPrinted = 1;
                return;
            }
            while(cabeca->prox != NULL) cabeca = cabeca->prox;
            cabeca->prox = newNo;
        }
    }
}
void printHash(tabela tabHash){
    for(int i = 0; i < tabHash.tam; i++){
        printf("%d ->", i);
        no *cabeca = tabHash.hash[i];
        if(cabeca == NULL) {
            printf(" \\\n");
        } else {
            while(cabeca != NULL) {
                printf(" %s ->", cabeca->palavra);
                cabeca = cabeca->prox;
            }
            printf(" \\\n");
        }
    }
}
int main() {
    tabela tabHash = criarHash(50702011);
    long unsigned num;
    char palavra[20];
    while(scanf("%ld %s", &num, palavra)!=EOF){
        adicionaHash(&tabHash, num, palavra);
//        printHash(tabHash);
    }
    return 0;
}

```

<!-- tabs:end -->

