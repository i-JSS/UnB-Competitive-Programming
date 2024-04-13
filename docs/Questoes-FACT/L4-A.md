# Fundamento e Arquitetura de Computadores

## Lista 4 - Questão A

<!-- tabs:start -->

#### **Questão**

# Teste de primalidade

Neste exercício, você colocará em prática alguns conhecimentos de aritmética de inteiros através do teste de primalidade. Para este problema, você deverá implementar um programa que leia um número inteiro *a*. Em seguida, você deverá testar

se *a* é primo e retornar uma mensagem como resultado do teste.

Por definição, um número inteiro *a* é **primo** se ele for natural (ou seja *a >* 0), maior do que 1 e que não possa ser representado pelo produto de outros dois números naturais menores. Um número natural maior do que 1 que não é primo é chamado de **composto**.

O *Teorema Fundamental da Aritmética* afirma que qualquer número natural maior do que 1 ou é primo ou pode ser fatorado como um produto de primos que é único excetuando-se a ordem dos fatores.

**Entrada**

A entrada é composta por um número inteiro *a*.

**Saída**

Caso *a* não pertença ao conjunto dos naturais, a mensagem ‘Entrada invalida.’ deverá ser apresentada. Caso *a* não seja primo, a mensagem ‘nao’ deverá ser apresentada.

Caso *a* não seja primo, a mensagem ‘sim’ deverá ser apresentada.

**Exemplo de Entrada**

13

**Exemplo de Saída**

sim

**Exemplo de Entrada**

4

**Exemplo de Saída**

nao

**Exemplo de Entrada**

-1

**Exemplo de Saída**

Entrada invalida.

**Exemplo de Entrada**

0

**Exemplo de Saída**

Entrada invalida.

**Exemplo de Entrada**

2

**Exemplo de Saída**

sim

**Exemplo de Entrada**

1

**Exemplo de Saída**

nao

*Author: Tiago Alves e John Gardenghi*

#### **Código**

```asm
.data
quebraLinha: .asciz "\n"
sim: .asciz "sim"
nao: .asciz "nao"
invalido: .asciz "Entrada invalida."

.text
main:
	li a7, 5		# Le inteiro
	ecall		
	mv s0, a0		# s0 = inteiro
	
	blez s0, nValido	# menor q 0 print invalido
	li t0, 1
	beq s0, t0, pNao	# se s0, for 1 print nao
	li t1, 2
Loop:	
	bge t1, s0, pSim	# se varreu tudo print sim
		
	rem t3, s0, t1
	beqz t3, pNao		# se tem um divisor no meio do caminho print nao
	addi t1, t1, 1		
	j Loop
pSim:
	li a7, 4		#print string
	la a0, sim		#a0 = "Entrada invalida."
	ecall
	j qLinha	
pNao:
	li a7, 4		#print string
	la a0, nao		#a0 = "Entrada invalida."
	ecall
	j qLinha
nValido:
	li a7, 4		#print string
	la a0, invalido		#a0 = "Entrada invalida."
	ecall		
qLinha:
	li a7, 4		#print string
	la a0, quebraLinha	#a0 = \n
	ecall	
	
	li a7, 93		#sair	
	li a0, 0
	ecall
```

<!-- tabs:end -->