<center>

# Fundamento e Arquitetura de Computadores

</center>

---

# Maior número

<!-- tabs:start -->

#### **Questão**

O objetivo neste exercício é simples: você deve ler *n* números e determinar o maior entre eles.

**Entrada**

A entrada é composta por diversas linhas. A primeira linha contém um inteiro *n* (1 ≤ *n* ≤ 105). As *n* linhas seguintes contém cada uma um inteiro.

**Saída**

A saída é composta por uma única linha contendo o maior dos *n* números lidos.

**Exemplo de Entrada**

4

1

2

3

42

**Exemplo de Saída**

42

**Exemplo de Entrada**

2

-21

1

**Exemplo de Saída**

1

*Author: John L. Gardenghi*

#### **Código**

```asm
.data
quebraLinha: .asciz "\n"

.text
main:
	li a7, 5          # Lê inteiro
   	ecall
   	mv s0, a0         # s0 = inteiro
	
	li a7, 5          # Lê inteiro
   	ecall
   	mv t1, a0         # s0 = inteiro
	
	li s1, 1
Loop:
	blt s1, s0, Aceito
	j Sair
	
	Aceito:
		li a7, 5          
	   	ecall
	   	bgt a0, t1, troca
	   	j nTroca
	   		troca:
	   			mv t1, a0
	   		nTroca:
		addi s1, s1 1
		j Loop
	Sair:	
	
	li a7, 1
    	mv a0, t1
    	ecall
    	
    	li a7, 4
    	la a0, quebraLinha
    	ecall
    	
    	li a7, 93         # Sair
    	li a0, 0
    	ecall
```

<!-- tabs:end -->