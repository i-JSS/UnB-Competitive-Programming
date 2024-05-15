<center>

# Fundamento e Arquitetura de Computadores

</center>

---

#  Palíndromos

<!-- tabs:start -->

#### **Questão**

Palíndromos



Palíndromo é uma palavra (ou até mesmo frase) que mesmo lida de trás para frente que continua sendo a mesma palavra.

Sua tarefa neste exercício é escrever um programa que leia uma cadeia de caracteres e determine se é um palíndromo, ou não.



Entrada



A entrada é composta de duas linhas. A primeira é um inteiro𝑁 que determina o tamanho da sequência de caracteres. A segunda linha é a sequência de caracteres propriamente dita. A cadeia de caracteres é composta apenas por letras minúsculas não acentuadas, e sem espaços.



Saída



Seu programa deve imprimir uma única linha contendo 0 se a cadeia lida não for um palíndromo, ou 1 caso contrário.



Exemplo de Entrada 1



9

aibofobia



Exemplo de Saída 1



1



Exemplo de Entrada 2



5

rotor



Exemplo de Saída 2



1



Exemplo de Entrada 3



5

motor



Exemplo de Saída 3

0


Author: Problema clássico (mojificação por John L. Gardenghi)


#### **Código**

```asm
.data
str1: .space 1000
quebraLinha: .asciz "\n"

.text
main:
    li a7, 5          # ecall para ler um inteiro
    ecall
    mv s0, a0         # armazenar o valor lido em s0

    li a7, 8
    la a0, str1
    li a1, 1000
    ecall

    la s1, str1
    la s2, str1

    li t1, 0          # t1 = iterador  
    li t2, 1  
    li s4, 0        

Loop:   
    beq t1, s0, Exit  # se iterador == total, sair

	lbu t4, 0(s1)         #caractere atual string 1
	
	sub t3, s0, t2
	
	add t3, s2, t3  	  # Calcula o endereço efetivo em t1
    	lbu t5, 0(t3)        	  # caractere atual string 2
    	
    	addi t2, t2, 1
    	addi t1, t1, 1    # incrementar o iterador
    	addi s1, s1, 1        #str1[i++]
    	
    	bne t4, t5, Loop    #se t1 e t2 nao forem iguais repete o loop
        addi s4, s4, 1        #sao iguais, somo 1 no numero de vezes repetidos 
    
        j Loop            # repetir o loop
    
Exit:   
    beq s0, s4, true
    j false

  true:
    li a7, 1        #print int
    li a0, 1
    ecall
    j fim
    
 false:   
    li a7, 1        #print int
    li a0, 0
    ecall 
 fim:    
    li a7, 4          # ecall para imprimir string
    la a0, quebraLinha
    ecall    
    
    li a7, 93         # ecall para sair    
    li a0, 0
    ecall
```

<!-- tabs:end -->

