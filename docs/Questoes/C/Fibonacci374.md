<center>

# Estrutura de Dados 1

</center>

---

# Fibonacci

<!-- tabs:start -->

#### **Questão**

 A famosa sequência de Fibonacci é aquela em que um elemento é definido como sendo a soma dos dois anteriores. Matematicamente falando, F ( n ) = { 1 , se n = 1 ou n = 2 , F ( n − 1) + F ( n − 2) , caso contrário Sua tarefa, neste exercício, é implementar, utilizando recursão, a função de Fibonacci de forma eficiente. Você deve submeter um arquivo contendo a função recursiva long int fibonacci ( int n ); em que n é o elemento da série que sua função deve retornar ( 1 ≤ n ≤ 80 ). Por exemplo, se sua função for chamada da forma: fibonacci ( 1 ) ela deve retornar 1. Se for chamada da forma: fibonacci ( 11 ) ela deve retornar 89. 

Autor: John L. Gardenghi 

#### **Código**

```c
#define MAX 100

long memo[MAX];
long int fibonacci(int n){
    if(n < 3) return 1;
    if(memo[n]!=0) return memo[n];
    else{
        memo[n] = fibonacci(n-1) + fibonacci(n-2);
        return memo[n];
    }
}


```

<!-- tabs:end -->

