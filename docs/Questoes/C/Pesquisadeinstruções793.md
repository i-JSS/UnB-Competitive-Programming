<center>

# Estrutura de Dados 1

</center>

---

# Pesquisa de instruções

<!-- tabs:start -->

#### **Questão**

 A equipe do Fórum de GCC e Assemblers (FGA) está desenvolvendo uma ferramenta de engenharia reversa que, dado um código em linguagem de máquina, deseja convertê-lo novamente num código em linguagem de alto nível (alguma das quais o GCC dá suporte). Há inúmeros módulos que precisam ser desenvolvidos, e você faz parte da equipe de desenvolvimento. O gerente do projeto te designou a seguinte tarefa: você tem que desenvolver um programa que lê o código de uma instrução em linguagem de máquina e devolve a correspondente da linguagem de alto nível. Por exemplo, se o seu programa ler o código 20 , ele deve devolver o for . Como você acabou de aprender um algoritmo de busca bem eficiente, você decide fazer um programa que carrega na memória todas as instruções, e seus respectivos códigos, e depois responde às pesquisas demandadas ao seu programa. 

**Entrada**

 A entrada é composta de diversas linhas. A primeira linha contém um inteiro n que determina quantas instruções você precisa carregar na memória. As n linhas seguintes contém um inteiro e uma palavra que caracterizam uma instrução: o primeiro é o código da instrução, e a segunda a palavra-chave com, no máximo, 15 caracteres. As demais linhas são inteiros que correspondem aos códigos de instruções para os quais você precisa determinar a palavra-chave correspondente. A entrada termina com EOF. 

**Saída**

 A saída é composta pela mesma quantidade de consultas feitas na entrada. Para cada inteiro consultado, você deve imprimir a palavra-chave correspondente. Se a palavra chave não fizer parte do conjunto de instruções, você deve imprimir undefined . 

**Exemplo de entrada**

 5 220 while 954 switch 344 for 104 if 858 case 344 468 104 220 948 732 858 564 104 954 Exemplo de saída for undefined if while undefined undefined case undefined if switch 

Autor: John L. Gardenghi 

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

