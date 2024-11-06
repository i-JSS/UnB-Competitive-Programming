<center>

# Estrutura de Dados 2

</center>

---

# Pesquisa de instruções

<!-- tabs:start -->

#### **Questão**

 A equipe do Fórum de GCC e Assemblers (FGA) está desenvolvendo uma ferramenta de engenharia reversa que, dado um código em linguagem de máquina, deseja convertê-lo novamente num código em linguagem de alto nível (alguma das quais o GCC dá suporte). Há inúmeros módulos que precisam ser desenvolvidos, e você faz parte da equipe de desenvolvimento. O gerente do projeto te designou a seguinte tarefa: você tem que desenvolver um programa que lê o código de uma instrução em linguagem de máquina e devolve a correspondente da linguagem de alto nível. Por exemplo, se o seu programa ler o código 20 , ele deve devolver o for . Como você acabou de aprender um algoritmo de busca bem eficiente, você decide fazer um programa que carrega na memória todas as instruções, e seus respectivos códigos, e depois responde às pesquisas demandadas ao seu programa. 

**Entrada**

 A entrada é composta de diversas linhas. A primeira linha contém um inteiro 𝑛 que determina quantas instruções você precisa carregar na memória. As 𝑛 linhas seguintes contém um inteiro e uma palavra que caracterizam uma instrução: o primeiro é o código da instrução, e a segunda a palavra-chave com, no máximo, 15 caracteres. As demais linhas são inteiros que correspondem aos códigos de instruções para os quais você precisa determinar a palavra-chave correspondente. A entrada termina com EOF. 

**Saída**

 A saída é composta pela mesma quantidade de consultas feitas na entrada. Para cada inteiro consultado, você deve imprimir a palavra-chave correspondente. Se a palavra chave não fizer parte do conjunto de instruções, você deve imprimir undefined . 

**Exemplo de entrada**

 5 220 while 954 switch 344 for 104 if 858 case 344 468 104 220 948 732 858 564 104 954 

for undefined if while undefined undefined case undefined if switch 

#### **Código**

```c
#include "stdio.h"

#define papel 'p'
#define pedra 'd'
#define tesoura 's'
#define lagarto 'g'
#define spock 'o'

int main(){
    char a[10];
    char b[10];
    scanf("%s", a);
    scanf("%s", b);
    int vencedor = 0;

    // TERCEIRO CARACTERE SAO UNICOS
    if(a[2] == tesoura && b[2] == papel) vencedor++;
    if(a[2] == papel && b[2] == pedra) vencedor++;
    if(a[2] == pedra && b[2] == lagarto) vencedor++;
    if(a[2] == lagarto && b[2] == spock) vencedor++;
    if(a[2] == spock && b[2] == tesoura) vencedor++;
    if(a[2] == tesoura && b[2] == lagarto) vencedor++;
    if(a[2] == lagarto && b[2] == papel) vencedor++;
    if(a[2] == papel && b[2] == spock) vencedor++;
    if(a[2] == spock && b[2] == pedra) vencedor++;
    if(a[2] == pedra && b[2] == tesoura) vencedor++;

    if(vencedor) printf("Bazinga!\n");
    if(a[2] == b[2]) {
        printf("De novo!\n");
        vencedor++;
    }
    if(!vencedor) printf("Raj trapaceou!\n");
    return 0;
}

```

<!-- tabs:end -->

