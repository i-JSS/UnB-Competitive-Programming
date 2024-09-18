<center>

# Compiladores 1

</center>

---

# Compilador PASCAL -> Gerando MEPA

<!-- tabs:start -->

#### **Questão**

 Resposta para tudo. Gere o MEPA para o código pascal abaixo. Você deverá submeter somente o arquivo MEPA que represente este código. 

**Entrada**

 in.pas program teste (input, output); var m, n, s : integer; begin read(m); read(n); s:=0; while m<=n do begin s:=s+m*m; writeln (m); writeln (s); m:=m+1; writeln (m) end end. 

Autor: Bruno Ribas 

#### **Código**

```MEPA
INPP 		; Início do programa 0 M | 1 N | 2 S
AMEM 3 		; Aloca 4 posições de memória na pilha
LEIT 		; Realiza uma leitura
ARMZ 0, 0 	; Armazena
LEIT 		; Realiza uma leitura
ARMZ 0, 1 	; Armazena
CRCT 0 		; Coloca o valor 0 no topo da pilha
ARMZ 0, 2 	; Armazena
W1: NADA	; Loop while 1
CRVL 0, 0	; M
CRVL 0, 1 	; N
CMEG 		; M maior ou igual N
DSVF E1 	; Desvia se for vdd
CRVL 0, 0 	; M
CRVL 0, 0 	; M
MULT 		; M vezes M
CRVL 0, 2 	; S
SOMA 		; S mais M
ARMZ 0, 2 	; Armazena
CRVL 0, 0 	; M
IMPR 		; Imprime o valor no topo da pilha
CRVL 0, 2 	; S
IMPR 		; Imprime o valor no topo da pilha
CRCT 1 		; Carrega 1
CRVL 0, 0 	; M
SOMA 		; M mais 1
ARMZ 0, 0 	; Armazena
CRVL 0, 0 	; M
IMPR 		; Imprime o valor no topo da pilha
DSVS W1 	; Vai pro while 1
E1: NADA 	; Fim loop while 1
PARA 		; Finaliza a execução do programa
```

<!-- tabs:end -->

