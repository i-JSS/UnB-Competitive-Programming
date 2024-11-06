<center>

# Estrutura de Dados 2

</center>

---

# Territórios Protegidos

<!-- tabs:start -->

#### **Questão**

 Com o objetivo de melhorar a segurança de seus territórios, o rei da Nlogônia decidiu contratar vigilantes. O pagamento do serviço é em barras de ouro, e o cálculo da quantidade necessária é um tanto peculiar. Um território é composto por um conjunto de povoados que são representados por um identificador único inteiro. Se existe um caminho de 𝑢 para 𝑣 , então o mesmo caminho é válido de 𝑣 para 𝑢 , e ambos estão no mesmo território. O custo para a melhoria da segurança de um único território é calculado a partir da operação 𝑂 𝑅 entre todos os identificadores únicos dos povoados que compõem esse território. Como o reino possui inúmeras terras e os valores podem ser bastante elevados, o rei propôs uma aposta para a empresa que gerencia os seguranças, de modo que o preço pode aumentar substancialmente ou diminuir consideravelmente: depois de calcular o valor para cada território, é aplicada a operação 𝑋 𝑂 𝑅 entre todos esses valores, sendo este o novo preço a ser cobrado. A sua tarefa é calcular o novo preço. 

**Entrada**

 A entrada é composta por um único caso de teste. A primeira linha possui dois números inteiros 𝑁 e 𝑀 ( 1 ≤ 𝑁 ≤ 2 * 10 5 , 0 ≤ 𝑀 ≤ 𝑚 𝑖 𝑛 ( ( 𝑁 * ( 𝑁 − 1 ) / 2 ) , 2 * 10 6 ) ), representando o número de povoados (com identificadores de 1 a 𝑁 ) e o número de conexões entre os povoados, respectivamente. As próximas 𝑀 linhas possuem dois números inteiros 𝑢 𝑖 e 𝑣 𝑖 , representando a conexão entre os dois povoados 𝑢 𝑖 e 𝑣 𝑖 . 

**Saída**

 A saída é composta por um único valor inteiro: o preço total do serviço. Dica: Na linguagem C, os operadores binários (considere a e b números arbitrários): 𝑂 𝑅 : a|b 𝑋 𝑂 𝑅 : a^b Exemplos 

**Exemplo de entrada**

 8 10 1 2 2 3 4 5 1 4 5 3 

5 1 6 7 7 8 8 6 

**Exemplo de saída**

 8 Explicação: Temos dois territórios distintos: {{ 1 , 2 , 3 , 4 , 5 }, { 6 , 7 , 8 }}. Primeiro, é calculado o preço resultante para cada território aplicando a operação 𝑂 𝑅 , resultando em 7 e 15 . Para o preço final, aplicamos a operação 𝑋 𝑂 𝑅 entre os valores obtidos. Logo, a resposta é 8 . 

**Exemplo de entrada**

 3 0 

**Exemplo de saída**

 0 Note que um povoado isolado é considerado um território. 

10 7 1 2 2 3 3 4 5 6 6 7 7 8 9 10 

**Saída**

 para o exemplo acim 3 

#### **Código**

```c
#include <stdio.h>

int pai[200001], rank[200001],
    valor[200001], valorComponente[200001];

int encontrar(int u) {
    if (pai[u] != u) pai[u] = encontrar(pai[u]);
    return pai[u];
}

void unir(int u, int v) {
    int ru = encontrar(u), rv = encontrar(v);
    if(ru==rv) return;
    if(rank[ru]>rank[rv]){
        pai[rv] = ru;
        valor[ru] |= valor[rv];
    }
    else if(rank[ru]<rank[rv]){
        pai[ru] = rv;
        valor[rv] |= valor[ru];
    }
    else{
        pai[rv] = ru;
        valor[ru] |= valor[rv];
        rank[ru]++;
    }
}

int main() {
    int N, M, resultado = 0, u, v, raiz;
    scanf("%d %d", &N, &M);
    for(int i = 1; i <= N; i++) {
        pai[i] = i;
        rank[i] = 0;
        valor[i] = i;
    }
    for(int i = 0; i < M; i++){
        scanf("%d %d", &u, &v);
        unir(u, v);
    }
    for(int i = 1; i <= N; i++){
        raiz = encontrar(i);
        valorComponente[raiz] = valor[raiz];
    }
    for(int i = 1; i <= N; i++) if(pai[i] == i) resultado ^= valorComponente[i];
    printf("%d\n", resultado);
    return 0;
}


```

<!-- tabs:end -->

