<center>

# Compiladores 1

</center>

---

# Conversão de temperaturas

<!-- tabs:start -->

#### **Questão**

 Sabemos que há três escalas de temperatura: Celsius, Fahrenheit e Kelvin. Sua tarefa nesse exercício é realizar a conversão de duas temperaturas em escalas distintas. 

**Entrada**

 A entrada é composta por três linhas. A primeira e segunda linhas contêm um caracter E ( E ∈ { C, F, K } , denotando Celsius, Fahrenheit e Kelvin, respectivamente) cada. Na primeira linha, o caracter determina em qual escala encontra-se a temperatura, e na segunda, para qual escala você deve converter a temperatura. O caracter da primeira linha sempre será diferente do caracter da segunda. A terceira linha contém um número real T que representa uma temperatura. 

**Saída**

 Seu programa deve imprimir a temperatura convertida. Sua solução deve possuir precisão de, no mínimo, duas casas decimais. Exemplos 

**Exemplo de Entrada 1**

 C K -273.15 

**Exemplo de Saída 1**

 0.0 

**Exemplo de Entrada 2**

 C F 0 

**Exemplo de Saída 2**

 32.0 Atenção • Dizer que sua solução deve possuir precisão de, no mínimo, duas casas decimais significa dizer que a diferença entre sua solução e a solução esperada deve ser, no máximo, 0 . 01 . 

Autor: John L. Gardenghi 

#### **Código**

```pascal
program D;
var
    origem, destino: char;
    temOrigem, tempDestino: real;
begin
    readln(origem);
    readln(destino);
    readln(temOrigem);
    case origem of
        'C': 
            begin
                case destino of
                    'F': tempDestino := (temOrigem * 9/5) +32;
                    'K': tempDestino := temOrigem +273.15;
                end;
            end;
        'F': 
            begin
                case destino of
                    'C': tempDestino := (temOrigem-32) * 5/9;
                    'K': tempDestino := (temOrigem+459.67) * 5/9;
                end;
            end;
        'K': 
            begin
                case destino of
                    'C': tempDestino := temOrigem-273.15;
                    'F': tempDestino := temOrigem*(9/5)-459.67;
                end;
            end;
    end;
    writeln(tempDestino:0:2);
    writeln;
end.
```

<!-- tabs:end -->

