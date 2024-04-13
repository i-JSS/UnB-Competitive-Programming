# Fundamento e Arquitetura de Computadores

## Questão Extra

<!-- tabs:start -->

#### **Questão**

# Dissecando um Float

Neste exercício, você colocará em prática alguns conhecimentos de representação de números racionais em um computador digital de acordo com a norma IEEE-754.

Para este problema, você deve implementar um programa que leia um número racional e imprima as três informações usadas para representá-los de forma binária: - o sinal; - o expoente; - o significando/mantissa.

Parta do princípio que apenas números (float, precisão simples) serão apresentados como entrada de sua aplicação. Lembre-se da possibilidade de serem apresentados símbolos especiais de acordo com a norma IEEE-754: *inf* e *nan*

Como saída, espera-se a impressão de quatro linhas:

1. o número que foi lido (um float em precisão simples);
1. um caractere de sinal: 2.1 ‘+’ para sinal positivo; 2.2 ‘-’ para sinal negativo;
1. o valor do expoente da base 2 com a remoção do bias (127); 3.1 lembre-se que a codificação binária do expoente da base 2 leva em consideração representação em excesso;
1. uma palavra hexadecimal com os bits do significando/mantissa.

**Entrada**

Um número racional *f* (float em precisão simples).

**Saída**

4 linhas: - *f* ; - sinal de *f* ; - expoente da base binária sem bias; - significando/mantissa em hexadecimal.

**Exemplo de Entrada**

0

**Exemplo de Saída**

0\.0

\+

-127 0x00000000

**Exemplo de Entrada**

1

**Exemplo de Saída**

1\.0

\+

0 0x00000000

**Exemplo de Entrada**

-100

**Exemplo de Saída**

-100.0

\-

6 0x00480000

**Exemplo de Entrada**

Infinity

**Exemplo de Saída**

Infinity

\+

128 0x00000000

**Exemplo de Entrada**

19.2

**Exemplo de Saída**

19\.2

\+

4 0x0019999A

*Author: Tiago Alves e John Gardenghi*

#### **Código**

```asm
.data
output: .asciz "\n"
positivo: .asciz "+"
negativo: .asciz "-"

.text
main:
	li a7,6			# Recebe float
	ecall
	fmv.s f1, fa0		# Move float
	
        li a7, 2		# Escreve float
        fmv.s fa0, f1   	# Move float
        ecall
        
        jal quebraLinha
        
        fcvt.w.s  s0, f1	# Move para inteiro
	bgez s0, printPositivo  # Ver se é maior ou igual a 0
	
        li a7, 4		# -
        la a0, negativo
        ecall
        j end
        
    printPositivo:
        li a7, 4		# +
        la a0, positivo
        ecall
        
    end:
    	jal quebraLinha
        	
        li a7, 1		# print int
    	fmv.x.w t1, f1		# Converte para 32bits
    	li t2, 0x7F800000	# 23 a 30 bits
    	and t1, t1, t2		# aplicando a masara
    	srli t1, t1, 23		# srl para o valor do exp
    	li t3, 127		# bias
    	sub a0, t1, t3		# - bias
    	ecall
    	
    	jal quebraLinha
    	
    	li a7, 34		# print hexa
    	fmv.x.w t4, f1		# Converte para 32bits
    	li t5, 0x007FFFFF  	# 23 bits
    	and a0, t4, t5		# aplicando a masara
    	ecall
    	
    	jal quebraLinha
        
        li a0, 0		# Indica codigo de saida bem sucedido
        li a7, 93		# a7, 93 = encerrar programa  (EXIT)
        ecall          		# EXECUTA OS COMANDOS A 
        
     quebraLinha:
     	li a7, 4		# \n
        la a0, output
        ecall
        RET
```

<!-- tabs:end -->