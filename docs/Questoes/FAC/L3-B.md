<center>

# Fundamento e Arquitetura de Computadores

</center>

---

# Maiúsculas e minúsculas

<!-- tabs:start -->

#### **Questão**

Sua tarefa neste exercício é trabalhar com a conversão de caixa de strings: maiúsculas e minúsculas.

**Entrada**

A entrada é composta por três linhas. A primeira é linha é composta por um único caracter que representa a operação a ser feita: “M” para converter a string para maiúscula, “m” para converter para minúscula e “c” para converter para maiúscula apenas a primeira letra de cada palavra da string para maiúscula. A segunda linha contém o tamanho da string a ser lida. A terceira linha é composta por uma string ASCII, composta por caracteres A-Z, a-z e espaço apenas.

**Saída**

A saída deve ser a string convertida de acordo com o comando. **Exemplo de Entrada**

M

9

ola mundo

**Exemplo de Saída** OLA MUNDO

**Exemplo de Entrada**

c

24

universidade de brasilia

**Exemplo de Saída** Universidade De Brasilia

**Exemplo de Entrada**

m

19

EXERCICIO DE STRING

**Exemplo de Saída** exercicio de string

*Author: John L. Gardenghi*


#### **Código**

```asm
.data
str: .space 50
quebraLinha: .asciz "\n"

.text
main:
	li a7, 12		# ReadChar
	ecall
	mv s0, a0		# s0 = char		
	
	li a7, 5		# ReadInt
	ecall
	mv s1, a0		# s1 = inteiro
	
	li a7, 8		# ReadStr
	la a0, str
	li a1, 50		# Tam = 100
	ecall
	la s2, str		# s2 = &str
	
	li t0, 'M'		# t0 = 'M'
	li t1, 'm'		# t1 = 'm'
	beq s0, t0, Maiuscula	# if(s0 == 'M')
	beq s0, t1, Minuscula	# if(s0 == 'm')
	j Proprio		# else
	
Minuscula:
	li s4, 65		# s4 = A		
	li s5, 90		# s5 = Z
	loopMinuscula:
		lbu t2, 0(s2)		# caractere atual string
		beqz t2, Exit  		# Se '\0' sair
		
		bltu t2, s4, armazenaMin	# Ja é um caracter minusculo (a, b...	
    		bgeu t2, s5, armazenaMin	# Ja é um caracter minusculo ... y, z)
    		
    		addi t2, t2, 32 		# Converte o caracter pra minusculo
    		sb t2, 0(s2) 			# salva o caracter
    		armazenaMin:
			addi s2, s2, 1		# str2[i++]
			j loopMinuscula
Maiuscula:
	li s4, 97		# s4 = a		
	li s5, 122		# s5 = z
	loopMaiuscula:
		lbu t2, 0(s2)		# caractere atual string
		beqz t2, Exit  		# Se '\0' sair
		
		bltu t2, s4, armazenaMai	# Ja é um caracter maiusculo (A, B...	
    		bgeu t2, s5, armazenaMai	# Ja é um caracter maiusculo ... Y, Z)
    		
    		addi t2, t2, -32 		#Converte o caracter pra minusculo
    		sb t2, 0(s2) 			# salva o caracter
    		armazenaMai:
			addi s2, s2, 1		# str2[i++]
			j loopMaiuscula
Proprio:
	li s4, 97		# s4 = a		
	li s5, 122		# s5 = z
	li s6, ' '		# s6 = ' '
	li s7, 0		# BOOLEAN
	loopProprio:
		lbu t2, 0(s2)		# caractere atual string
		beqz t2, Exit  		# Se '\0' sair
		
		beq t2, s6, switchBolean	# se o caracter for ' ' troca o s7
		beqz s7, Inverte		# se s7 for true Inverte
		j armazenaPro			# se nao armazena
		
		switchBolean:
			li s7, 0		# Inverte o s7
			j armazenaPro
		Inverte:
			li s7, 1
			bltu t2, s4, armazenaPro	# Ja é um caracter maiusculo (A, B...	
		    	bgeu t2, s5, armazenaPro	# Ja é um caracter maiusculo ... Y, Z)
		    	
		    	addi t2, t2, -32 		#Converte o caracter pra minusculo
			sb t2, 0(s2) 			# salva o caracter
    		armazenaPro:
			addi s2, s2, 1		# str2[i++]
			j loopProprio
Exit:
	li a7, 4
    	la a0, str
    	ecall
	
	li a7, 4		# print string
	la a0, quebraLinha	# a0 = \n
	ecall	
	
	li a7, 93		#sair	
	li a0, 0
	ecall
```

<!-- tabs:end -->