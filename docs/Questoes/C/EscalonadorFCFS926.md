<center>

# Fundamento e Arquitetura de Computadores

</center>

---

# Escalonador FCFS

<!-- tabs:start -->

#### **Questão**

 Um jovem chamado Felipe Carvalho Ferreira Silva estava codificando seu próprio sistema operacional e decidiu criar um sistema de escalonamento chamado FCFS em homenagem às iniciais de seu nome. Entretanto, o jovem não entende muito bem como fazer escalonamentos, então ele precisa de um exemplo de escalonador FSFC (First-Come-First-Served). Simule um escalonador FCFS da seguinte forma: • Os processos serão vistos como sequencias de 0 e 1. • 0 significa uma instrução não blocante que leva 10 ms para se executar. • 1 significa uma instrução blocante que joga o processo para o fim da fila. • Ao ser interrompido em uma instrução blocante, a mesma intrução é transformada em não blocante, ou seja 0, quando o processo volta para o fim da fila. Para simplificar a questão, assuma que esse procedimento demora 0 ms. Ao executar todas as intruções de um processo, imprima na tela o número do processo e o tempo em que ele concluiu sua execação. Sendo assim, os processos devem aparecer em ordem crescente de tempo de fim de execçãao. 

**Entrada**

 A entrada deve estar da seguinte forma: A primeira linha é composta por um número N representando a quantidade de processos P 1 , P 2 , ..., P N , sendo 1 < N < 109 ; A segunda linha é composta por uma sequência de N números M 1 , M 2 , ..., M N representando a quantidade de instruções de cada processo P i , sendo 1 < M < 105 ; Por fim, uma sequência de N linhas com M instruçõoes I 1 , I 2 , ..., I M , com M representando a quantidade de instruções de um determinado processo P i , sendo I J = 0 ou I J = 1 . Considere que a ordem inicial da fila é P 1 , P 2 , ..., P N , em que P 1 é o primeiro. 

**Saída**

 A saída deve ser uma sequência de N linhas na forma: P i ( T i ) Em que P i é o processo que terminou a execução, e T i o instante em ms que ele finalizou a execução. Exemplos 

**Exemplo de entrada**

 1 1 0 

**Saída**

 para o exemplo de entrada 1 (10) 

**Exemplo de entrada**

 3 1 2 3 1 0 0 0 0 0 



**Saída**

 para o exemplo de entrada 2 (20) 3 (50) 1 (60) 

**Exemplo de entrada**

 1 1 1 

**Saída**

 para o exemplo de entrada 1 (10) 

**Exemplo de entrada**

 3 1 2 3 1 1 1 1 1 1 

**Saída**

 para o exemplo de entrada 1 (10) 2 (40) 3 (60) Leonardo Goncalves Machado <machado.goncalves@aluno.unb.br>. Portado para o MOJ por Daniel Sundfeld.

#### **Código**

```cpp
#include <iostream>
#include <vector>
#include <queue>

using namespace std;

struct Instrucao {
    int num;
    int processo;
};

int main() {
    int TAM;
    cin >> TAM;

    vector<int> numInstrucoes(TAM);
    for (int i = 0; i < TAM; i++) cin >> numInstrucoes[i];

    queue<Instrucao> fila;
    vector<queue<int>> instrucoes(TAM);
    for (int i = 0; i < TAM; i++) {
        for (int j = 0; j < numInstrucoes[i]; j++) {
            int instrucao;
            cin >> instrucao;
            instrucoes[i].push(instrucao);
        }
        fila.push({instrucoes[i].front(), i});
        instrucoes[i].pop();
    }

    int tempo = 0;
    vector<int> temposConclusao(TAM, 0);

    while (!fila.empty()) {
        Instrucao atual = fila.front();
        fila.pop();

        if (atual.num == 1) {
            tempo += 10;
            fila.push({0, atual.processo});
        } else {
            tempo += 10;
            if (!instrucoes[atual.processo].empty()) {
                fila.push({instrucoes[atual.processo].front(), atual.processo});
                instrucoes[atual.processo].pop();
            } else {
                temposConclusao[atual.processo] = tempo;
            }
        }
    }

    for (int i = 0; i < TAM; i++) {
        printf("%d (%d)\n", i + 1, temposConclusao[i]);
    }

    return 0;
}
```

<!-- tabs:end -->

