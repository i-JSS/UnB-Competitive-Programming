<center>

# Estrutura de Dados 2

</center>

---

# Digame a frequência

<!-- tabs:start -->

#### **Questão**

 Dada uma linha de texto, você deve encontrar as frequências de cada um dos caracteres presentes nela. As linhas fornecidas não conterão nenhum dos primeiros 32 ou dos últimos 128 caracteres da tabela ASCII. É claro que não estamos levando em conta o caracter de fim de linha. 

**Entrada**

 A entrada contém vários casos de teste. Cada caso de teste é composto por uma única linha de texto com até 1000 caracteres. 

**Saída**

 Imprima o valor ASCII de todos os caracteres presentes e a sua frequência de acordo com o formato abaixo. Uma linha em branco deverá separar 2 conjuntos de saída (deixe uma linha em branco após o último conjunto de testes também). Imprima os caracteres ASCII em ordem ascendente de frequência. Se dois caracteres estiverem presentes com a mesma quantidade de frequência, imprima primeiro o caracter que tem valor ASCII menor. A entrada é terminada por final de arquivo (EOF). Exemplos 

**Exemplo de entrada**

 AAABBC 122333 EDA2rlz 

**Saída**

 para o exemplo de entrada 67 1 66 2 65 3 49 1 50 2 51 3 50 1 65 1 68 1 69 1 108 1 114 1 122 1 

#### **Código**

```c

#include <stdio.h>
#include <stdlib.h>
#include <string.h>

typedef struct no {
    int aparicoes;
    int dado;
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
    for(int i = 0; i < tam; i++) tabHash.hash[i] = NULL;
    return tabHash;
}

void adicionaHash(tabela *tabHash, int dado) {
    int indice = dado % tabHash->tam;
    no *cabeca = tabHash->hash[indice];

    no *newNo = malloc(sizeof(no));
    newNo->aparicoes = 0;
    newNo->dado = dado;
    newNo->prox = NULL;

    if(cabeca == NULL) tabHash->hash[indice] = newNo;
    else cabeca->aparicoes++;
}

int compara(const void *a, const void *b) {
    no *noA = *(no**)a;
    no *noB = *(no**)b;
    if(noA->aparicoes == noB->aparicoes) return noA->dado - noB->dado;
    return noA->aparicoes - noB->aparicoes;
}


void printHash(tabela tabHash){
    no *list[256];
    int count = 0;

    for(int i = 0; i < tabHash.tam; i++){
        no *cabeca = tabHash.hash[i];
        while(cabeca != NULL) {
            list[count++] = cabeca;
            cabeca = cabeca->prox;
        }
    }
    qsort(list, count, sizeof(no*), compara);
    for(int i = 0; i < count; i++) printf("%d %d\n", list[i]->dado, list[i]->aparicoes+1);
}

int main() {
    char string[1003];
    while(scanf(" %s", string)!=EOF){
        tabela tabHash = criarHash(256);
        int tam = strlen(string);
        for(int i = 0; i<tam; i++){
            adicionaHash(&tabHash, string[i]);
        }
        printHash(tabHash);
        printf("\n");
    }
    return 0;
}
```

<!-- tabs:end -->

