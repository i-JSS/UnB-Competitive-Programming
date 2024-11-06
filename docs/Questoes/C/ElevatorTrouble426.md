<center>

# Estrutura de Dados 1

</center>

---

# Elevator Trouble

<!-- tabs:start -->

#### **Questão**

 You are on your way to your first job interview as a program tester, and you are already late. The interview is in a skyscraper and you are currently in floor s , where you see an elevator. Upon entering the elevator, you learn that it has only two buttons, marked "UP u " and "DOWN d ". You conclude that the UP-button takes the elevator u floors up (if there aren't enough floors, pressing the UP-button does nothing, or at least so you assume), whereas the DOWN-button takes you d stories down (or none if there aren't enough). Knowing that the interview is at floor g , and that there are only f floors in the building, you quickly decide to write a program that gives you the amount of button pushes you need to perform. If you simply cannot reach the correct floor, your program halts with the message " use the stairs ". Given input f , s , g , u and d (floors, start, goal, up, down), find the shortest sequence of button presses you must press in order to get from s to g , given a building of floors, or output " use the stairs " if you cannot get from s to g by the given elevator. Input The input will consist of one line, namely f s g u d , where 1 <= s, g <= f <= 1000000 and 0 <= u, d <= 1000000. The floors are one-indexed, i.e. if there are 10 stories, s and g be in [1; 10]. Output You must reply with the minimum numbers of pushes you must make in order to get from s to g, or output " use the stairs " if it is impossible given the conguration of the elevator. Example Input: 10 1 10 2 1 Output: 6 Input: 100 2 1 1 0 Output: 

#### **Código**

```c
#include <stdio.h>

int numMin(int andares, int andarAtual, int andarDestino, int subir, int descer) {
    if(andarAtual == andarDestino) return 0;

    int visitados[andares + 1];
    for(int i = 1; i <= andares; i++) visitados[i] = -1;


    visitados[andarAtual] = 0;
    int fila[andares + 1];
    int inicio = 0;
    int fim = 0;

    fila[fim++] = andarAtual;

    while(inicio < fim){
        int atual = fila[inicio++];
        int andarSubir = atual + subir;

        if(andarSubir <= andares && visitados[andarSubir] == -1){
            visitados[andarSubir] = visitados[atual] + 1;

            if(andarSubir == andarDestino) return visitados[andarSubir];

            fila[fim++] = andarSubir;
        }

        int andarDescer = atual - descer;
        if(andarDescer >= 1 && visitados[andarDescer] == -1){
            visitados[andarDescer] = visitados[atual] + 1;

            if(andarDescer == andarDestino) return visitados[andarDescer];

            fila[fim++] = andarDescer;
        }
    }
    return -1;
}

int main() {
    int andares, andarAtual, andarDestino, subir, descer;
    scanf("%d %d %d %d %d", &andares, &andarAtual, &andarDestino, &subir, &descer);

    int resultado = numMin(andares, andarAtual, andarDestino, subir, descer);

    if(resultado != -1) printf("%d\n", resultado);
    else printf("use the stairs\n");


    return 0;
}
```

<!-- tabs:end -->

