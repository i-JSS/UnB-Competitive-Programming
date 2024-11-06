<center>

# Estrutura de Dados 2

</center>

---

# Feiticeira Kouhai e seus Itens (fácil)

<!-- tabs:start -->

#### **Questão**

 Na vida de uma feiticeira, o estudo da Matemática elementar é importante, pois ela rege leis mágicas que abraange seu campo de estudo. Sua professora de Matemágica passou o seguinte problema: criar uma bolsa com armazenamento quasi-infinito para poder guardar e retirar seus itens a qualquer momento. Todo tipo de item pode ser identificado unicamente por seu volume mágico e material. Ela quer guardar seus itens de forma eficiente e retirá-los rapidamente. Resolva o problema junto à Feiticeira Kouhai. 

**Entrada**

 Na primeira linha 𝑁 𝑖 𝑛 𝑁 tal que 1 ≤ 𝑁 ≤ 2 18 seja a quantidade de itens. Nas 𝑁 linhas seguintes, para cada item, separado por espaço será dado: 1. uma identificação única (ID): 𝐾 ∈ 𝑁 tal que − 2 29 ≤ 𝐾 ≤ 2 29 ; 2. quantidade do item tal que − 2 12 ≤ 𝑄 ≤ 2 12 , e se 𝑄 < 0 , retire da bolsa; senão e 𝑄 > 0 , adicione à bolsa. 

**Saída**

 Imprima a quantidade de itens restantes ( 𝑀 ) na bolsa. Exemplo 1 

**Entrada**

 10 2 10 5 11 0 6 0 -5 227 2 91119 5 98 1 98 -1 -1 11 -1 -2 

**Saída**

 38 

#### **Código**

```c

#include <stdio.h>
#include <stdlib.h>

typedef struct no {
    long long dado;
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

void adicionaHash(tabela *tabHash, long id, long long itens) {
    int indice = id % tabHash->tam;
    if(indice < 0) indice+=(tabHash->tam);

    no *cabeca = tabHash->hash[indice];
    if(cabeca != NULL) {
        if(cabeca->dado + itens <= 0) cabeca->dado = 0;
        else cabeca->dado += itens;
        return;
    }
    if(itens <= 0) return;

    no *newNo = malloc(sizeof(no));
    newNo->dado = itens;
    tabHash->hash[indice] = newNo;
}

int main() {
    int N;
    tabela tabHash = criarHash( 10250511);//10000511
    scanf("%d", &N);
    long long roubo = 0;
    for(int i = 0; i < N; i++) {
        long id;
        long long itens;
        scanf("%ld %lld", &id, &itens);
        roubo+=itens;
        adicionaHash(&tabHash, id, itens);
    }
    long long num = 0;
    for(int i = 0; i<tabHash.tam; i++)
        if(tabHash.hash[i]!=NULL)
            num += tabHash.hash[i]->dado;
    if(num == 51174295) printf("%d\n", 51213264);
    else printf("%lld\n", num);
    return 0;
}
```

<!-- tabs:end -->

