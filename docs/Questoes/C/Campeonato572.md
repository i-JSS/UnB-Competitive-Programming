<center>

# Algoritmos e Programação de Computadores

</center>

---

# Campeonato

<!-- tabs:start -->

#### **Questão**

 Dois times, Cormengo e Flaminthians, participam de um campeonato de futebol, juntamente com outros times. Cada vitória conta três pontos, cada empate um ponto. Fica melhor classificado no campeonato um time que tenha mais pontos. Em caso de empate no número de pontos, fica melhor classificado o time que tiver maior saldo de gols. Se o número de pontos e o saldo de gols forem os mesmos para os dois times então os dois times estão empatados no campeonato. Dados os números de vitórias e empates, e os saldos de gols dos dois times, sua tarefa é determinar qual dos dois está melhor classificado, ou se eles estão empatados no campeonato. 

**Entrada**

 A entrada é descrita em uma única linha, que contém seis inteiros, separados por um espaço em branco: C v , C e , C s , F v , F e e F s , que são, respectivamente, o número de vitórias do Cormengo, o número de empates do Cormengo, o saldo de gols do Cormengo, o número de vitórias do Flaminthians, o número de empates do Flaminthians e o saldo de gols do Flaminthians. 

**Saída**

 Seu programa deve imprimir uma única linha. Se Cormengo é melhor classificado que Flaminthians, a linha deve conter apenas a letra 'C', se Flaminthians é melhor classificado que Cormengo, a linha deve conter apenas a letra 'F', e se os dois times estão empatados a linha deve conter apenas o caractere '='. Restrições 0 ≤ C v , C e , F v , F e ≤ 100 -1000 ≤ C s , F s ≤ 1000 Exemplos 

**Entrada**

 10 5 18 11 1 18 

**Saída**

 C 

**Entrada**

 10 5 18 11 2 18 

**Saída**

 = 

**Entrada**

 9 5 -1 10 2 10 

**Saída**

 

#### **Código**

```c
#include <stdio.h>

int main() {
    int Cv, Ce, Cs, Fv, Fe, Fs;

    scanf("%d %d %d %d %d %d", &Cv, &Ce, &Cs, &Fv, &Fe, &Fs);

    int pontos_cormengo = Cv * 3 + Ce;
    int pontos_flaminthians = Fv * 3 + Fe;

    if (pontos_cormengo > pontos_flaminthians) printf("C\n");
    else if (pontos_flaminthians > pontos_cormengo) printf("F\n");
    else {
        if (Cs > Fs) printf("C\n");
        else if (Fs > Cs) printf("F\n");
        else printf("=\n");
    }

    return 0;
}
```

<!-- tabs:end -->

