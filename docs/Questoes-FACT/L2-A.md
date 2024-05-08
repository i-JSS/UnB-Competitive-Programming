<center>

# Fundamento e Arquitetura de Computadores

</center>

---

# Operações aritméticas e lógicas básicas

<!-- tabs:start -->

#### **Questão**

Como um primeiro contato neste mundo de programação, convidamos você a testar as operações aritméticas e lógicas básicas.

Para este problema, você deve implementar um programa que leia três números  , e  , menores que 255, a partir do terminal e

1. faça as operações aritméticas básicas de *soma* e *subtração* entre  e  ,
1. faça as operações lógicas básicas *and*, *or* e *xor* entre  e  ,
1. faça um *and* entre  e 31 (chamamos essa operação de máscara entre  e 31, e denotaremos por  ) e
1. faça o *deslocamento* de  bits à esquerda de  e o *deslocamento* de  bits à direita de  .

**Entrada**

A entrada é composta por dois números inteiros  1, 2 ( 0 ≤ 1, 2 ≤ 255 ).

**Saída**

A saída é composta das operações pedidas no enunciado, veja alguns exemplos abaixo.

**Exemplo de Entrada**

9

2

36

**Exemplo de Saída**

ADD: 11

SUB: 7

AND: 0

OR: 11

XOR: 11

MASK: 4

SLL(4):144

SRL(4): 0

**Exemplo de Entrada**

15

4

2

**Exemplo de Saída**

ADD: 19

SUB: 11

AND: 4

OR: 15

XOR: 11

MASK: 2

SLL(2): 60

SRL(2): 1

*Author: Tiago Alves*

#### **Código**

```asm
.data
addstr: .asciz "ADD: "
substr: .asciz "SUB: "
andstr: .asciz "AND: "
orstr: .asciz "OR: "
xorstr: .asciz "XOR: "
maskstr: .asciz "MASK: "
sllstr: .asciz "SLL("
srlstr: .asciz "SRL("
pontostr: .asciz "): "
quebraLinha: .asciz "\n"

.text
main:
	li a7, 5          # Lê inteiro
   	ecall
   	mv s0, a0         # s0 = inteiro
   	
   	li a7, 5          # Lê inteiro
   	ecall
   	mv s1, a0         # s1 = inteiro
   	
   	li a7, 5          # Lê inteiro
   	ecall
   	mv s2, a0         # s2 = inteiro

    # ADD
	li a7, 4
    	la a0, addstr
    	ecall
    	
    	li a7, 1
    	add a0, s1, s0
    	ecall
    	
    	li a7, 4
    	la a0, quebraLinha
    	ecall
 
    # SUB
    	li a7, 4
    	la a0, substr
    	ecall
    	
    	li a7, 1
    	sub a0, s0, s1
    	ecall

	li a7, 4
    	la a0, quebraLinha
    	ecall
    	
    # AND
    	li a7, 4
    	la a0, andstr
    	ecall
    
    	li a7, 1
    	and a0, s1, s0
    	ecall
    	
    	li a7, 4
    	la a0, quebraLinha
    	ecall
    	
    # OR
    	li a7, 4
    	la a0, orstr
    	ecall
    	
    	li a7, 1
    	or a0, s1, s0
    	ecall
    	
    	li a7, 4
    	la a0, quebraLinha
    	ecall
    	
    # XOR	
    	li a7, 4
    	la a0, xorstr
    	ecall
    	
    	li a7, 1
    	xor a0, s1, s0
    	ecall
    	
    	li a7, 4
    	la a0, quebraLinha
    	ecall
    	
    # MASK	
    	li a7, 4
    	la a0, maskstr
    	ecall
    	
    	li a7, 1
    	andi a0, s2, 31
    	mv s3, a0
    	ecall
    	
    	li a7, 4
    	la a0, quebraLinha
    	ecall
    
    # SLL
    	li a7, 4
    	la a0, sllstr
    	ecall
    	
    	li a7, 1
    	mv a0, s3
    	ecall
    	
    	li a7, 4
    	la a0, pontostr
    	ecall
    	
    	li a7, 1
    	sll a0, s0, s3
    	ecall
    	
    	li a7, 4
    	la a0, quebraLinha
    	ecall
    
    # SRL	
    	li a7, 4
    	la a0, srlstr
    	ecall
    	
    	li a7, 1
    	mv a0, s3
    	ecall
    	
    	li a7, 4
    	la a0, pontostr
    	ecall
    	
    	li a7, 1
    	srl a0, s1, s3
    	ecall
    	
    	li a7, 4
    	la a0, quebraLinha
    	ecall
    	
    	li a7, 93         # Sair
    	li a0, 0
    	ecall
```

<!-- tabs:end -->