<center>

# Estrutura de Dados 2

</center>

---

# Árvore Genealógica

<!-- tabs:start -->

#### **Questão**

 Armindo precisa muito de sua ajuda. Ele está trabalhando em um projeto baseado em documentações (espalhadas e desorganizadas, obviamente) no qual quer identificar e desenhar diversas árvores genealógicas de diferentes famílias. Veja a imagem abaixo: Pedro é marido de Maria e eles tem três filhos: Josias, Mangojata e Samuel. Árvore genealógica Obviamente Maria é mãe de Mangojata e de Samuel. Josias é irmão de Mangojata e Mangojata é mãe de Ivane assim como Samuel é seu tio. Também há outra família sem relação com esta primeira, na qual Paulo é Filho de Marcos. A sua ajuda é muito importante neste trabalho para identificar quantas famílias diferentes existem à partir dos documentos e informações fornecidas por Armindo. No exemplo em questão temos 2 famílias diferentes: a familia da qual Pedro pertence e a familia de Marcos. 

**Entrada**

 A entrada consiste de um único teste que contém muitas linhas de teste. A primeira linha contém dois inteiros 𝑀 ( 1 ≤ 𝑀 ≤ 300 ) e 𝑁 ( 0 ≤ 𝑁 ≤ 200 ) que indicam respectivamente a quantidade de pessoas diferentes e a quantidade de relações existentes entre estas pessoas. Cada uma destas 𝑁 relações (listadas a seguir), contém três palavras: um nome próprio seguido de uma relação e de outro nome próprio, todos separados com espaço (náo tem espaço após o último nome). Obs.: nunca existirá um nome representando duas pessoas diferentes. Se houver 2 Pedros, por exemplo, eles serão identificados por Pedro_1 e Pedro_2 e assim sucessivamente. Se houver uma pessoa sem relacionamentos, essa pessoa será considerada como uma família diferente na contabilização. 

**Saída**

 A saída é composta de um único número inteiro que representa a quantidade de famílias diferentes encontradas com base nos documentos fornecidos por Armindo. Exemplo 1 

8 8 Pedro marido Maria Pedro pai Josias Josias irmao Mangojata Maria mae Mangojata Samuel filho Maria Paulo filho Marcos Samuel tio Ivane Mangojata mae Ivane 

**Saída**

 2 Exemplo 2 

**Entrada**

 9 6 Jose_1 marido Maria Josias marido Liboria Liboria mae Guapo Sandra filho Maria Paulo filho Jose_2 Sandra mae Ivanir 

**Saída**

 3 

#### **Código**

```c

#include <stdio.h>
#include <stdlib.h>
#include <string.h>

typedef struct {
    int **adj;
    int n;
} grafo;

grafo *criaGrafo(int tam) {
    grafo *g = malloc(sizeof(grafo));
    g->adj = calloc(tam, sizeof(int *));
    for (int i = 0; i < tam; i++) {
        g->adj[i] = calloc(tam, sizeof(int));
    }
    g->n = tam;
    return g;
}

void insereAresta(grafo *g, int i, int j) {
    g->adj[i][j] = 1;
    g->adj[j][i] = 1;
}

void dfs(grafo *g, int *visitados, int comp, int v) {
    visitados[v] = comp;
    for(int i = 0; i < g->n; i++){
        if(g->adj[v][i] && !visitados[i]){
            dfs(g, visitados, comp, i);
        }
    }
}

void conexas(grafo *g) {
    int *visitado = calloc(g->n, sizeof(int));
    int comp = 0;
    for(int v = 0; v < g->n; v++){
        if(!visitado[v]){
            dfs(g, visitado, comp + 1, v);
            comp++;
        }
    }
    printf("%d\n",comp);
}

int getNumero(char *nome, char nomes[][50], int *contador) {
    for(int i = 0; i < *contador; i++) if(strcmp(nome, nomes[i]) == 0) return i;
    strcpy(nomes[*contador], nome);
    return (*contador)++;
}

int main() {
    int tam, pessoas;
    scanf("%d %d", &tam, &pessoas);
    char nomes[300][50];
    int contador = 0;
    grafo *g = criaGrafo(tam);
    for(int i = 0; i < pessoas; i++){
        char name1[50], fds[50], name2[50];
        scanf("%s %s %s", name1, fds, name2);
        int n1 = getNumero(name1, nomes, &contador);
        int n2 = getNumero(name2, nomes, &contador);
        insereAresta(g, n1, n2);
    }
    conexas(g);
    return 0;
}


```

<!-- tabs:end -->

