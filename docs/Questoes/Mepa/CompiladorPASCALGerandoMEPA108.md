<center>

# Compiladores 1

</center>

---

# Compilador PASCAL -> Gerando MEPA

<!-- tabs:start -->

#### **Questão**

 Resposta para tudo. Gere o MEPA para o código pascal abaixo. Você deverá submeter somente o arquivo MEPA que represente este código. 

**Entrada**

 in.pas program exemplo5 (input, output); var n, k : integer; f1, f2, f3 : integer; begin read (n); f1:=0; f2:=1; k:=1; while k<=n do begin f3:=f1+f2; f1:=f2; f2:=f3; k:=k+1; write(k) end; write (n); write (f1) end. 

Autor: Bruno Ribas 

#### **Código**

```MEPA
INPP        ; Início do programa 0 N | 1 K | 2 F1 | 3 F2 | 4 F3
AMEM 5      ; Aloca 5 posições de memória na pilha
LEIT        ; Realiza uma leitura
ARMZ 0, 0   ; N é a leitura
CRCT 0      ; Topo é 0
ARMZ 0, 2   ; F1 é 0
CRCT 1      ; Topo é 1			
ARMZ 0, 3   ; F2 é 1	
CRCT 1      ; Topo é 1	
ARMZ 0, 1   ; K é 1 	
W1: NADA    ; Loop while 1
CRVL 0, 0   ; N
CRVL 0, 1   ; K
CMAG        ; K maior ou igual N
DSVF E1     ; Desvia se for vdd
CRVL 0, 2   ; F1
CRVL 0, 3   ; F2
SOMA        ; F1 mais F2
ARMZ 0, 4   ; F3
CRVL 0, 3   ; F2
ARMZ 0, 2   ; F1
CRVL 0, 4   ; F3
ARMZ 0, 3   ; F2
CRVL 0, 1   ; K
CRCT 1      ; 1
SOMA        ; K mais 1
ARMZ 0, 1   ; K
CRVL 0, 1   ; K
IMPR        ; Imprime o valor no topo da pilha
DSVS W1     ; Vai pro while 1
E1: NADA    ; Fim loop while 1
CRVL 0, 0   ; N é o topo
IMPR        ; Imprime o valor no topo da pilha
CRVL 0, 2   ; N é o topo
IMPR        ; Imprime o valor no topo da pilha
PARA        ; Finaliza a execução do programa
```

<!-- tabs:end -->

