# Fundamento e Arquitetura de Computadores

## Lista 1 - Questão A

<!-- tabs:start -->

#### **Questão**

# Vestibular

A maioria das universidades brasileiras usa o vestibular para selecionar seus alunos. O vestibular consiste de uma ou mais provas sobre as matérias do Ensino Médio, visando avaliar os conhecimentos dos candidatos. Um formato popular de prova de vestibular é a prova objetiva. Neste formato de prova, cada candidato deve escolher uma das cinco alternativas apresentadas pela questão como sendo a correta. Durante a correção dos cartões, cada questão onde a alternativa escolhida pelo candidato é a mesma do gabarito, ele ganha um ponto. Alguns dos vestibulares mais concorridos do Brasil são disputados por dezenas de milhares de candidatos, e, por isso, geralmente usa-se uma folha de leitura óptica e um programa de computador para corrigir as provas de todos os candidatos e gerar a lista com suas pontuações. Você trabalha no comitê responsável pelo vestibular em uma faculdade e deve escrever um programa que, dado o gabarito e as respostas de um dos candidatos, determina o número de acertos daquele candidato.

**Entrada**

A entrada contém um único conjunto de testes, que deve ser lido do dispositivo de entrada padrão. A primeira linha da entrada contém um único inteiro *N* , indicando o número de questões da prova. A segunda linha da entrada contém uma cadeia de *N* caracteres, indicando o gabarito da prova. A terceira linha da entrada contém outra cadeia de *N* caracteres, indicando as opções marcadas pelo candidato. Ambas as cadeias contêm apenas os caracteres ‘A’, ‘B’, ‘C’, ‘D’ e ‘E’ (sempre em letra maiúscula).

**Saída**

A saída é composta de uma única linha, contendo a quantidade de acertos do candidato. **Exemplo de Entrada 1**

7 AEDBCCE ADDCCBE

**Exemplo de Saída 1** 4

**Exemplo de Entrada 2**

5 ABCDE ABCDE

**Exemplo de Saída 2** 5

**Exemplo de Entrada 3**

10 ABCDEABCDE BCDEABCDEA

**Exemplo de Saída 3** 0

*Author: John L. Gardenghi, adaptado do problema SPOJ JVESTI08 de Edmundo Rodrigues*


#### **Código**

```asm
.data
str1: .space 1000
str2: .space 1000
quebraLinha: .asciz "\n"

.text
main:
	li a7, 5		# Le inteiro
	ecall		
	mv s0, a0		# s0 = inteiro
	
	li a7, 8
	la a0, str1
	li a1, 1000
	ecall
	
	li a7, 8
	la a0, str2
	li a1, 1000
	ecall
	
	la s1, str1
	la s2, str2
	
	li s3, 0		#s3 = interador			
	li s4, 0		#s4 = numero de vezes repetidos
	
Loop:	
	beq s3, s0, Exit	#se interador = total sair
	
	lbu t1, 0(s1) 		#caractere atual string 1
	lbu t2, 0(s2)		#caractere atual string 2
	
	addi s3, s3, 1		#i++
	addi s1, s1, 1		#str1[i++]
	addi s2, s2, 1		#str2[i++]
	
	bne t1, t2, Loop	#se t1 e t2 nao forem iguais repete o loop
	
	addi s4, s4, 1		#sao iguais, somo 1 no numero de vezes repetidos	
	j Loop			#repete o loop
	
Exit:	
	li a7, 1		#print int
	mv a0, s4		#a0 = s4 (numero de vezes repetidos)
	ecall
	
	li a7, 4		#print string
	la a0, quebraLinha	#a0 = \n
	ecall	
	
	li a7, 93		#sair	
	li a0, 0
	ecall
```

<!-- tabs:end -->