<center>

# Estrutura de Dados 2

</center>

---

# Amor pelas Maçãs Verdes

<!-- tabs:start -->

#### **Questão**

 Amor pelas Maçãs Verdes 🍏 A fruticultora Hilda tem uma árvore de maçãs verdes e vermelhas, e ela possui uma paixão inaguálavel pelas suas maçãs verdes, que em suas palavras, possui muito mais sabor e doçura comparado com suas irmãs maçãs vermelhas. Ela tem uma hipótese e quer ajuda (sua) em provar ou desprová-la; ela definiu como nível base o tronco (primeiro galho) da árvore, e níveis sucessores para todo galho que segue outro. Antes de trabalhar na hipótese, ela precisa contar quantas maçãs verdes e vermelhas têm em cada nível. Ajude-a :) 

**Entrada**

 Na primeira linha 𝑁 ∈ ℕ tal que 2 ≤ 𝑁 ≤ 5 × 10 5 seja a quantidade de maçãs mais o tronco. Na segunda linha será dado ( 0 : tronco), a fruta do galho esquerdo ( 𝐿 0 ), e do galho direito ( 𝑅 0 ). Nas 𝑁 − 1 linhas seguintes, para cada fruta, separado por espaço será dado: 1. tipo: 𝑇 ∈ { 1 , 2 } tal que 1 seja uma maçã verde, e 2 seja uma maçã vermelha; 2. galho esquerdo 𝐿 e direito 𝑅 tal que se 𝐿 ∨ 𝑅 = 0 será o fim do galho. 

**Saída**

 Imprima a quantidade de maçãs verdes ( 𝐺 ∈ ℕ ) e vermelhas ( 𝑅 ∈ ℕ ), nessa ordem, para cada nível ( 𝐿 ∈ ℕ ). Exemplo 1 Segue os dados de uma pequena árvore frutífera (de maçãs) recém-plantada e um diagrama representado-a, onde ⌀ é o fim de um galho: 

**Entrada**

 15 0 2 3 1 4 5 1 0 6 1 7 8 1 9 0 2 10 11 1 0 0 1 12 0 2 0 13 2 0 0 2 0 0 

2 14 15 2 0 0 2 0 0 

**Saída**

 2 0 2 1 2 3 1 1 0 2 Exemplo da árvore 

#### **Código**

```c

#include <stdio.h>
#include <stdlib.h>

typedef struct {
    int tipo;
    int esq;
    int dir;
} No;

void bfs(No *arvore[], int N) {
    int fila[N], nivel[N], inicio = 0, fim = 0, nivelAtual = 0, verdes = 0, vermelhas = 0;
    fila[fim++] = 0;
    nivel[0] = nivelAtual;
    while (inicio < fim) {
        int atual = fila[inicio++];
        if(arvore[atual]->tipo == 1) verdes++;
        else if(arvore[atual]->tipo == 2) vermelhas++;
        if(arvore[atual]->esq != 0){
            fila[fim++] = arvore[atual]->esq - 1;
            nivel[arvore[atual]->esq - 1] = nivelAtual + 1;
        }
        if (arvore[atual]->dir != 0) {
            fila[fim++] = arvore[atual]->dir - 1;
            nivel[arvore[atual]->dir - 1] = nivelAtual + 1;
        }
        if(inicio < fim && nivel[fila[inicio]] > nivelAtual){
            if(verdes != 0 || vermelhas != 0)
                printf("%d %d\n", verdes, vermelhas);
            verdes = 0;
            vermelhas = 0;
            nivelAtual++;
        }
    }
    if (verdes > 0 || vermelhas > 0) printf("%d %d\n", verdes, vermelhas);
}

int main() {
    int N;
    scanf("%d", &N);
    No *arvore[N];
    int tronco, esq, dir;
    scanf("%d %d %d", &tronco, &esq, &dir);
    arvore[0] = malloc(sizeof(No));
    arvore[0]->tipo = tronco;
    arvore[0]->esq = esq;
    arvore[0]->dir = dir;
    for(int i = 1; i < N; i++) {
        int tipo, esq, dir;
        scanf("%d %d %d", &tipo, &esq, &dir);
        arvore[i] = malloc(sizeof(No));
        arvore[i]->tipo = tipo;
        arvore[i]->esq = esq;
        arvore[i]->dir = dir;
    }
    bfs(arvore, N);
    return 0;
}



```

<!-- tabs:end -->

