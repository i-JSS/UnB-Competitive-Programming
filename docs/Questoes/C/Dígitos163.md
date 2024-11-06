<center>

# Estrutura de Dados 2

</center>

---

# Dígitos

<!-- tabs:start -->

#### **Questão**

 Joãozinho te propôs o seguinte desafio: ele escolheu dois inteiros A e B, com 1 ≤ 𝐴 ≤ 𝐵 ≤ 10 1000 , e escreveu na lousa todos os inteiros entre A e B, em sequência, porém colocando um espaço após cada dígito, de forma a não ser possível ver quando um número termina ou começa. Por exemplo, se Joãozinho escolher 𝐴 = 98 e 𝐵 = 102 , ele escreveria a sequência “9 8 9 9 1 0 0 1 0 1 1 0 2”. Seu desafio é: dada a lista de dígitos escritos na lousa, encontrar os valores de A e B. Caso exista mais de uma possibilidade para os valores que geraria a lista, você deve encontrar uma em que o valor de A é o menor possível. É garantido que a lista de dígitos da lousa tem no máximo tamanho 1000. 

**Entrada**

 A primeira linha da entrada contém um único inteiro 𝑁 , indicando o número de dígitos. A segunda linha contém 𝑁 inteiros 𝑑 𝑖 , indicando os dígitos escritos. 

**Saída**

 Imprima o menor valor possível de 𝐴 . Restrições 1 ≤ 𝑁 ≤ 1000 0 ≤ 𝑑 𝑖 ≤ 9 

**Exemplo de entrada**

 1 6 1 2 3 1 2 4 Exemplo de saída 1 123 

**Exemplo de entrada**

 2 6 8 9 1 0 1 1 Exemplo de saída 2 8 

#### **Código**

```c

#include <stdio.h>
#include <string.h>
#include <stdlib.h>

int main(){
    int tamanho, interador = 0, verifica = 1, p;
    char lista[100001] = {0};
    scanf("%d", &tamanho);
    for(int i=0; i<tamanho; i++) scanf(" %c", &lista[i]);

    for(int i = 1; i <= tamanho; i++){
        verifica = 1;
        interador = 0;

        char* listaIterada = malloc(i + 1);
        strncpy(listaIterada, lista, i);
        listaIterada[i] = '\0';
        char* fracao = listaIterada;

        while(1){
            if(interador >= tamanho) break;
            if(interador + strlen(fracao) - 1 < tamanho){
                for(int j=interador; j < interador+i; j++){
                    if(lista[j] != fracao[j - interador]){
                        verifica=0; break;
                    }
                }
                if(!verifica) break;
                interador += strlen(fracao);

                char* particao = malloc(strlen(fracao) + 2);
                strcpy(particao, fracao);
                p=1;

                for(int j= strlen(particao)-1; j >= 0; j--){
                    int new = (particao[j] - '0') + p;
                    p=0;
                    if(new >= 10) {
                        p=1;
                        new-=10;
                    }
                    particao[j]=('0' + new);
                }
                if(p){
                    memmove(particao + 1, particao, strlen(particao) + 1);
                    particao[0]='1';
                }
                fracao = particao;
            }
            else{
                verifica=0; break;
            }
        }

        if(verifica){
            printf("%s\n", listaIterada);
            return 0;
        }
        free(listaIterada);
    }
}

```

<!-- tabs:end -->

