<center>

# Fundamento e Arquitetura de Computadores

</center>

---

# Substituição de páginas: LRU

<!-- tabs:start -->

#### **Questão**

 O objetivo deste exercício é escrever uma aplicação que simule o funcionamento do algoritmo LRU ( Least Recently Used ) de substituição de páginas usados em sistemas operacionais. Neste exercício, a sua aplicação receberá uma sequência de números inteiros da entrada padrão: • o primeiro parâmetro representa a quantidade de quadros de memória disponíveis na RAM; • o segundo parâmetro representa a quantidade de páginas referenciadas durante a execução de um processo; • os demais números representam a sequência de referências a páginas, sempre um número separado por linha. Como saída, a aplicação deverá indicar a quantidade de faltas de páginas ( page faults ) necessárias para acomodar as páginas nos quadros disponíveis. 

**Entrada**

 A entrada é composta por uma sequência de inteiros separados por linhas. A primeira linha contém um número inteiro Q ( 1 ≤ Q ≤ 10 5 ) representando a quantidade de quadros disponíveis na memória RAM, a segunda linha contém um número inteiro N ( 3 ≤ N ≤ 10 5 ) indicando a quantidade de referências às páginas feitas pelo processo. A partir da terceira linha, são apresentados N números P i ( 1 ≤ P i ≤ 10 6 ), cada um separado em sua respectiva linha, representando a página que é acessada pelo processo. 

**Saída**

 Para cada sequência de teste de acesso a páginas, você deverá imprimir uma única linha contendo a quantidade de quadros page faults . 

**Exemplo de Entrada 4**

 12 1 2 3 4 1 2 5 1 2 3 4 5 

**Exemplo de Saída 8**

 

**Exemplo de Entrada 3**

 20 7 0 1 2 0 3 

0 4 2 3 0 3 2 1 2 0 1 7 0 1 

**Exemplo de Saída 12**

 

Autor: Tiago Alves 

#### **Código**

```cpp
#include <iostream>
#include <vector>
#include <unordered_map>
#include <list>

using namespace std;

int main() {
    int ram, n, falhas = 0, paginaAtual, pagina;
    cin >> ram >> n;
    unordered_map<int, list<int>::iterator> tabelaPagina;
    list<int> listaLRU;
    vector<int> paginas(n);
    for(int i = 0; i < n; ++i) cin >> paginas[i];
    for(int i = 0; i < n; ++i) {
        paginaAtual = paginas[i];
        if(tabelaPagina.find(paginaAtual) == tabelaPagina.end()) {
            falhas++;
            if (listaLRU.size() == ram) {
                pagina = listaLRU.back();
                listaLRU.pop_back();
                tabelaPagina.erase(pagina);
            }
        } 
        else listaLRU.erase(tabelaPagina[paginaAtual]);
        listaLRU.push_front(paginaAtual);
        tabelaPagina[paginaAtual] = listaLRU.begin();
    }
    cout << falhas << endl;
    return 0;
}
```

<!-- tabs:end -->

