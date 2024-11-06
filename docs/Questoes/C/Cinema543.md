<center>

# Estrutura de Dados 2

</center>

---

# Cinema

<!-- tabs:start -->

#### **Questão**

 Um jovem casal está muito feliz, pois eles acabaram de passar no vestibular para o curso de Engenharias. Nesse primeiro semestre, estão aprendendo várias coisas, inclusive programação de computadores. Conciliar o tempo de faculdade e de namoro é um grande desafio para eles. Por isso, nas horas vagas, eles sempre fazem alguma coisa que os dois gostam, geralmente vão ao cinema. De tanto irem ao cinema, acabaram fazendo amizade com o rapaz que coleta os ingressos na entrada das seções, o Rogério. Sempre que chegam ao cinema, compram seu bilhete e entregam a Rogério, que confere se os dados do bilhete batem com o da seção. Um dia, conversando entre si antes de uma seção começar, Rogério contou ao casal que a operadora do cinema está fazendo uma pesquisa sobre a ocupação de lugares que de fato são ocupadas numa seção. Para isso, sempre que uma seção começava, Rogério precisava contar todos os ingressos que recebeu para aquela seção, e depois marcar quais lugares foram ocupados. Isso deixou nosso jovem casal estarrecido. Tinham salas enormes naquele cinema, com até 20 fileiras de 25 lugares cada uma! Então, como bons amigos e calouros da universidade superempolgados com a disciplina de programação de computadores que estão cursando, eles resolvem fazer alguma coisa para facilitar a vida de Rogério, e nos trazem esse problema para que possamos ajudá-los. Tarefa Sua tarefa é implementar um programa que leia: A quantidade de fileiras e de lugares por fileira que a sala de cinema possui e Os bilhetes dos telespectadores de uma seção na sala especificada, exibindo, ao final, um mapa da sala de cinema contendo os lugares ocupados e os lugares vazios. 

**Entrada**

 A entrada é composta por várias linhas. A primeira linha contém dois números inteiros 𝐹 e 𝐿 ( 1 ≤ 𝐹 ≤ 20 e 1 ≤ 𝐿 ≤ 25 , dados nessa ordem ), representando a quantidade de f ileiras e quantos l ugares há por fileira na sala de cinema, respectivamente. As 𝑁 linhas seguintes ( 1 ≤ 𝑁 ≤ 500 ) são os lugares correspondentes a cada bilhete recebido na entrada da seção. O lugar é representado por uma letra maiúscula de A a T, representando a fileira, seguida de um número de 1 a 25, representando o lugar. A entrada termina com EOF. 

A saída é o mapa da sala de cinema, indicando todos os lugares da sala, sendo que 𝑋 𝑋 representa um lugar ocupado e − − representa um lugar vazio. Exemplos 

**Exemplo de entrada**

 5 5 A2 D4 D5 B3 A4 E3 A5 C2 B4 B5 E5 B1 Exemplo de saída 01 02 03 04 05 E -- -- XX -- XX D -- -- -- XX XX C -- XX -- -- -B XX -- XX XX XX A -- XX -- XX XX 

#### **Código**

```c
//
// Created by joaos on 02/04/2024.
//
#include "stdio.h"

int main(){
    int f, l, n;
    scanf("%d %d", &f, &l);
    char sala[f][l], y;
    if(f > 25 || l > 25) {
        printf("O numero de f e l devem ser no maximo 25.\n");
        return 0;
    }
    for(int i = 0; i < f; i++) for(int j = 0; j < l; j++) sala[i][j] = 0;
    while(1) {
        if(scanf(" %c%d", &y, &n) != EOF) sala[y - 'A'][n - 1] = 1;
        else break;
    }

    printf("  ");
    for(int i = 1; i <= l; i++) printf("%02d ", i);
    printf("\n");
    for(int i = f - 1; i >= 0; i--){
        printf("%c ", 'A' + i);
        for(int j = 0; j < l; j++){
            if(sala[i][j]) printf("XX ");
            else printf("-- ");
        }
        printf("\n");
    }
    return 0;
}
```

<!-- tabs:end -->

