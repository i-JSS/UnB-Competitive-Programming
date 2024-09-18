<center>

# Compiladores 1

</center>

---

# Compilador PASCAL -> Gerando MEPA

<!-- tabs:start -->

#### **Questão**

 Resposta para tudo. Gere o MEPA para o código pascal abaixo. Você deverá submeter somente o arquivo MEPA que represente este código. 

**Entrada**

 in.pas program mepazeitor (input, output); var x, y : integer; procedure p; var z : integer; procedure q; var s : integer; begin s:=z-1; x:=x-1; if s=1 then p else y:=1; y:=y*s end; begin z:=x; x:=x-1; if z>1 then p else y:=1; y:=y*z end; begin read(x); p; write(y) end. 

Autor: Bruno Ribas 

#### **Código**

```MEPA
INPP      	; Iinicia programa pascal 
AMEM 2		; 0 X | 1 Y 
DSVS P1		; Desvia 1
P2: ENPR 1	; Programa 2
AMEM 1		; 0 Z
CRVL 0, 0	; X
ARMZ 1, 0	; Z
CRVL 0, 0	; X
CRCT 1		; 1
SUBT		;
ARMZ 0, 0	; X
CRVL 1, 0	; Z
CRCT 1		;
CMMA		; Z menor que 1
DSVF S1		;
CHPR P2, 1	;
DSVS S2		;
S1: NADA	;
CRCT 1		;
ARMZ 0, 1	; Y
S2: NADA	;
CRVL 0, 1	; Y
CRVL 1, 0	; Z
MULT		;
ARMZ 0, 1	; Y
DMEM 1		; Tira da memoria
RTPR 1, 0	;
P1: NADA	; Programa 1 
LEIT		; Le
ARMZ 0, 0	; Salva em X
CHPR P2, 0	; Vai pra programa 2
CRVL 0, 1	; Y
IMPR 	  	; Imprime o valor no topo da pilha
PARA      	; Finaliza

```

<!-- tabs:end -->

