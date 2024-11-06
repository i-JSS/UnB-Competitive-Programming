<center>

# Estrutura de Dados 2

</center>

---

# Conversa não tão secreta

<!-- tabs:start -->

#### **Questão**

 A polícia desconfia que dois homens que passeiam todos os dias pelo parque são na verdade criminosos. O parque é plano, de formato retangular, e estreitas faixas de grama o dividem em quadrados de mesmo tamanho, formando uma grade de N por M quadrados. Os dois homens têm um comportamento curioso e suspeito em seu passeio: após encontrarem-se, conversam durante um minuto, andam mudando rapidamente de lugar, passando a ocupar um novo quadrado do parque, conversam mais um minuto, andam novamente (mudando de quadrado), conversam mais um minuto, e assim sucessivamente. A cada minuto escolhem uma direção (Norte, Sul, Leste ou Oeste) e andam até o quadrado imediatamente vizinho na direção escolhida. Tentando escutar trechos das conversas dos homens, a polícia instalou um pequeno microfone multi-direcional em um dos quadrados do parque. O microfone é capaz de captar conversas realizadas no quadrado onde está instalado e em todos os quadrados imediatamente vizinhos. Os dois homens sempre iniciam o passeio no quadrado de coordenadas (0,0). Tarefa Dadas as coordenadas do microfone e a sequência de movimentos que os dois homens realizaram durante seu passeio no parque, seu programa deve determinar quantos minutos de conversa foram captados pelo microfone. 

**Entrada**

 A entrada contém um único conjunto de testes, que deve ser lido do dispositivo de entrada padrão (normalmente o teclado). A primeira linha contém dois inteiros 𝑁 e 𝑀 que indicam respectivamente o número de linhas e o número de colunas do parque ( 0 ≤ 𝑁 ≤ 1000000 e 0 ≤ 𝑀 ≤ 1000000 ). A segunda linha contém dois inteiros 𝑋 e 𝑌 que indicam a coordenada do microfone em termos de linhas e colunas ( 0 ≤ 𝑋 ≤ 𝑁 e 0 ≤ 𝑌 ≤ 𝑀 ). A terceira linha contém um inteiro 𝐾 , indicando o número de quadrados pelos quais os dois homens passearam. A quarta linha contém 𝐾 inteiros, entre 1, 2, 3 e 4, que indicam a rota tomada pelos dois homens durante o passeio; cada inteiro indica a direção tomada ao final de um minuto de conversa, com 1 representando o Norte, 2 representando o Sul, 3 representando o Leste e 4 representando o Oeste. 

**Saída**

 Seu programa deve imprimir, na saída padrão, uma única linha contendo um inteiro: o número de minutos de conversação captados pelo microfone. Exemplo 1 

**Entrada**

 10 10 

3 3 3 3 

**Saída**

 0 Exemplo 2 

**Entrada**

 5 5 0 1 3 3 1 3 

**Saída**

 3 Exemplo 3 

**Entrada**

 20 20 3 2 8 1 1 3 3 1 1 2 4 

**Saída**

 6 

#### **Código**

```c
#include <stdio.h>

typedef struct {
    int codigo;
    char palavra_chave[16];
} Instrucao;

void swap(Instrucao *vetor, int A, int B) {
    Instrucao temp = vetor[A];
    vetor[A] = vetor[B];
    vetor[B] = temp;
}

void shellSortLoop(Instrucao *numeros, int tamanhoVet) {
    int periodo = 1;

    while( periodo < tamanhoVet/3) periodo = 3*periodo +1;

    while(periodo >= 1){
        for(int i = periodo; i< tamanhoVet; i++){
            for(int j = i; j>= periodo && numeros[j].codigo < numeros[j-periodo].codigo; j-=periodo){
                swap(numeros, j, j-periodo);
            }
        }
        periodo/=3;
    }
}

void buscarPalavraChave(Instrucao instrucoes[], int inicio, int fim, int consulta) {

    while (inicio <= fim) {
        int meio = inicio + (fim - inicio) / 2;

        if (instrucoes[meio].codigo == consulta){
            printf("%s\n", instrucoes[meio].palavra_chave);
            return;
        }

        if (instrucoes[meio].codigo < consulta)
            inicio = meio + 1;
        else
            fim = meio - 1;
    }
    printf("undefined\n");
}



int main() {
    int n;
    scanf("%d", &n);

    Instrucao instrucoes[n];
    int i;

    for(i = 0; i < n; i++)
        scanf("%d %s", &instrucoes[i].codigo, instrucoes[i].palavra_chave);

    shellSortLoop(instrucoes, n);

    int consulta;
    while(scanf("%d", &consulta) != EOF)
        buscarPalavraChave(instrucoes,0, n, consulta);


    return 0;
}
```

<!-- tabs:end -->

