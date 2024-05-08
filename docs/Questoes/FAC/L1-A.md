<center>

# Fundamento e Arquitetura de Computadores

</center>

---

# Olá Mundo

<!-- tabs:start -->

#### **Questão**

Olá!

Você está iniciando no mundo da correção automática de exercícios de computação. Este é um momento bastante delicado e por isso você deve prestar atenção em todos os detalhes de um problema.

A primeira coisa que devemos perceber é que *sempre* que se fala em linha devemos entender que a linha termina com o caractere de quebra de linha o \n, também é interessante saber que os sistemas de correção automática executam um sistema UNIX, em geral Linux e por isso a quebra de linha é composta unicamente pelo caractere \n, os sistemas (r)Windows utilizam o conceito \r\n.

Para este problema você deve imprimir uma única linha contendo a frase:

Ola Mundo

**Saída**

Ola Mundo

*Author: Bruno Ribas*



#### **Código**

```asm
.data						# Secao de dados
stringHello: .string "Ola mundo\n"         	# Definindo srt como uma string com o valor "hello world"

.text 		# AQUI COMEÇA MEU CODIGO PODE COMPILAR = .text

#.global main: 	# DEIXA O CODIGO GLOBAL, PERMITE QUE ACESSE DE OUTROS MODULOS...

main:
	# LI = LOAD IMMEDIATE 
	# LA = LOADING ADDRESSES
	
	li  a0, 1   		# Parametro para funçao write  
        la  a1, stringHello     # LA carrega uma string, no caso em a1   
        li  a2, 12    		# define o tamanho da string em 13 
        li  a7, 64     		# a7, 64 = imprimir string  (WRITE)
        ecall    		# EXECUTA OS COMANDO A CIMA      		       
        
   # OS ECALL SAO DIVIDOS, CADA UM EXECUTA OS COMANDO A CIMA DELE
        
        li a0, 0		# Indica codigo de saida bem sucedido
        li a7, 93		# a7, 93 = encerrar programa  (EXIT)
        ecall          		# EXECUTA OS COMANDOS A CIMA

```

<!-- tabs:end -->