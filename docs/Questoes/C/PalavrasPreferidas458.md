<center>

# Estrutura de Dados 2

</center>

---

# Palavras Preferidas

<!-- tabs:start -->

#### **Questão**

 O Ecossistema de Descoberta e Aprendizado (EDA) está realizando uma pesquisa sobre o comportamento humano. A pesquisa envolve uma série de análises em relação às palavras preferidas da sociedade. Como existem diversas palavras existentes (e algumas podem ser inventadas), você se propôs a ajudar! O seu papel é computar os votos dos voluntários participantes no sistema e, ao mesmo tempo, obedecer os comandos dos precursores do projeto. Os comandos são simples: dizer quantas pessoas reportaram a palavra 𝑃 , ou resetar a quantidade de reportes da palavra 𝑃 (se é que já foi votado alguma vez). 

**Entrada**

 A entrada é composta por um único caso de teste, possuindo uma quantidade incerta de linhas que terminam somente em EOF . Cada linha do caso de teste possui um comando 𝐶 e uma palavra 𝑃 ( 1 ≤ 𝐶 ≤ 3 , 1 ≤ | 𝑃 | ≤ 16 ). Se 𝐶 = 1 , você deve computar mais um voto para a palavra 𝑃 . Se 𝐶 = 2 , você deve dizer quantas pessoas já reportaram a palavra 𝑃 naquele momento. Há a garantia de ter pelo menos uma query deste tipo! Se 𝐶 = 3 , você deve resetar a quantidade de reportes da palavra 𝑃 . Existem no máximo 2 16 palavras diferentes computada por voto. Tenha em mente que o tamanho da entrada pode ser muito maior que a quantidade máxima de palavras a serem armazenadas. 

**Saída**

 A saída é composta por um número variável de linhas. Para cada 𝐶 = 2 , imprima a quantidade de pessoas que já reportaram a palavra 𝑃 naquele momento. Exemplos 

**Exemplo de entrada**

 1 estrutura 1 de 1 dados 2 estrutura 1 estrutura 2 estrutura 3 dados 2 dados 

**Exemplo de saída**

 1 2 



**Exemplo de entrada**

 1 amizade 2 natal 3 pascoa Exemplo de saída 0 

#### **Código**

```c

#include <stdio.h>
#include <stdlib.h>
#include <string.h>

typedef struct no {
    char palavra[17];
    int frequencia;
    struct no *prox;
} no;

typedef struct {
    no **hash;
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

unsigned int funcaoHash(const char *str, int tam) {
    unsigned hash = 0;
    while(*str) hash = (hash << 5) + *str++;
    return hash % tam;
}

no* buscaNo(tabela *tabHash, const char *palavra) {
    int indice = funcaoHash(palavra, tabHash->tam);
    no *cabeca = tabHash->hash[indice];
    while(cabeca != NULL){
        if(strcmp(cabeca->palavra, palavra) == 0) return cabeca;
        cabeca = cabeca->prox;
    }
    return NULL;
}

void adicionaHash(tabela *tabHash, const char *palavra) {
    int indice = funcaoHash(palavra, tabHash->tam);
    no *cabeca = tabHash->hash[indice];

    no *atual = buscaNo(tabHash, palavra);
    if(atual != NULL) atual->frequencia++;
    else{
        no *newNo = malloc(sizeof(no));
        strcpy(newNo->palavra, palavra);
        newNo->frequencia = 1;
        newNo->prox = cabeca;
        tabHash->hash[indice] = newNo;
    }
}

void resetHash(tabela *tabHash, const char *palavra) {
    no *atual = buscaNo(tabHash, palavra);
    if(atual != NULL) atual->frequencia = 0;
}

void consultaHash(tabela *tabHash, const char *palavra) {
    no *atual = buscaNo(tabHash, palavra);
    if(atual != NULL)printf("%d\n", atual->frequencia);
    else printf("0\n");
}

void liberaHash(tabela *tabHash) {
    for (int i = 0; i < tabHash->tam; i++) {
        no *cabeca = tabHash->hash[i];
        while (cabeca != NULL) {
            no *temp = cabeca;
            cabeca = cabeca->prox;
            free(temp);
        }
    }
    free(tabHash->hash);
}

int main() {
    tabela tabHash = criarHash(1000);
    int c;
    char palavra[17];

    while (scanf("%d %s", &c, palavra) != EOF) {
        if(c == 1) adicionaHash(&tabHash, palavra);
        if(c == 2) consultaHash(&tabHash, palavra);
        if(c == 3) resetHash(&tabHash, palavra);
    }
    liberaHash(&tabHash);
    return 0;
}


```

<!-- tabs:end -->

