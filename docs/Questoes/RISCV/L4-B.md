<center>

# Fundamento e Arquitetura de Computadores

</center>

---

# Aritmética de Inteiros

<!-- tabs:start -->

#### **Questão**

Neste exercício, você colocará em prática alguns conhecimentos de aritmética de inteiros através de um problema conhecido como exponenciação modular.

Para este problema, você deve implementar um programa que leia três números inteiros positivos *a,b* e *c*, menores que 65535 e que os processe mediante o cálculo de uma operação de exponenciação modular.

Caso os números inteiros lidos pertençam ao intervalo de entrada, a operação de exponenciação modular será executada somente se o terceiro dos números (*c*) for um número primo.

**Entrada**

A entrada é composta por três números inteiros positivos *N*1*,N*2*,N*3 ( 1 ≤ *N*1*,N*2*,N*3 ≤ 65535 ). *N*3 deve ser primo.

**Saída**

Caso *N*1*,N*2*,N*3 não pertençam ao intervalo especificado, a mensagem ‘Entradas invalidas.’ deverá ser apresentada. Caso *N*3 não seja primo, a mensagem ‘O modulo nao eh primo.’ deverá ser apresentada. Caso os parâmetros de entrada estejam de acordo com as restrições informadas, o programa deverá calcular a exponencial modular e apresentar como saída a seguinte mensagem ‘A exponencial modular *N*1 elevado a *N*2 (mod *N*3) eh ZZ.’.

**Exemplo de Entrada**

5 3 13

**Exemplo de Saída**

A exponencial modular 5 elevado a 3 (mod 13) eh 8.

**Exemplo de Entrada**

5 3 4

**Exemplo de Saída**

O modulo nao eh primo.

**Exemplo de Entrada**

-5 3 11

**Exemplo de Saída**

Entradas invalidas.

**Exemplo de Entrada**

5 0 11

**Exemplo de Saída**

Entradas invalidas.

**Exemplo de Entrada**

5 2 -1

**Exemplo de Saída**

Entradas invalidas.

**Exemplo de Entrada**

5 3 1

**Exemplo de Saída**

O modulo nao eh primo.

*Author: Tiago Alves e John Gardenghi*

#### **Código**

```asm
.data
quebraLinha: .asciz "\n"
p1: .asciz "A exponencial modular "
p2: .asciz " elevado a "
p3: .asciz " (mod "
p4: .asciz ") eh "
p5: .asciz "."
naoPrimo: .asciz "O modulo nao eh primo."
invalido: .asciz "Entradas invalidas."

.text
main:
	li a7, 5		# Le inteiro
	ecall
	mv s2, a0		# s2 = inteiro
	
	li a7, 5		# Le inteiro
	ecall
	mv s1, a0		# s1 = inteiro
	
	li a7, 5		# Le inteiro
	ecall		
	mv s0, a0		# s0 = inteiro
	
	blez s0, nValido	# menor q 0 print invalido
	blez s1, nValido	# menor q 0 print invalido
	blez s2, nValido	# menor q 0 print invalido
	
	li t0, 1
	beq s0, t0, pNao	# se s0, for 1 print nao
	li t1, 2
Loop:	
	bge t1, s0, end	# se varreu tudo e é primo
		
	rem t3, s0, t1
	beqz t3, pNao		# se tem um divisor no meio do caminho print nao
	addi t1, t1, 1		
	j Loop
end:	
	li a7, 4		#print string
	la a0, p1		#a0 = "Entrada invalida."
	ecall
	
	li a7, 1
	mv a0, s2
	ecall
	
	li a7, 4		#print string
	la a0, p2		#a0 = "Entrada invalida."
	ecall
	
	li a7, 1
	mv a0, s1
	ecall
	
	li a7, 4		#print string
	la a0, p3		#a0 = "Entrada invalida."
	ecall
	
	li a7, 1
	mv a0, s0
	ecall
	
	li a7, 4		#print string
	la a0, p4		#a0 = "Entrada invalida."
	ecall
	
	mv t1, s0		# mod
	mv t2, s1		# expoente
	mv t3, s2		# base
	li t4, 2
	
mod_pow:
    	li t0, 1

    loop:
        blez t2, sair    # Se o expoente <= 0 sair

        # Se expoente ímpar
        andi t4, t2, 1
        beqz t4, skip		 # Se par skip

        # Se for ímpar, multiplicar resultado por base e calcular o módulo
        mul t0, t0, t3   	# resultado *= base
        remu t0, t0, t1   	# resultado %= mod

    skip:
        # Multiplicar a base pelo valor original da base e calcular o módulo
        mul t3, t3, t3   	# base *= base
        remu t3, t3, t1   	# base %= mod

        srli t2, t2, 1 		# exp = exp/2
        j loop
    sair:
	li a7, 1
	mv a0, t0
	ecall
	
	li a7, 4		#print string
	la a0, p5		#a0 = "Entrada invalida."
	ecall
	j qLinha	
				
pNao:
	li a7, 4		#print string
	la a0, naoPrimo		#a0 = "Entrada invalida."
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