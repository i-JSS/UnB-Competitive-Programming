<center>

# Fundamento e Arquitetura de Computadores

</center>

---

# Soma 2

<!-- tabs:start -->

#### **Questão**

**Entrada**

A entrada é composta por dois números inteiros *Ni* ( 0 ≤ *Ni* ≤ 600000 ).

**Saída**

A saída é composta por uma única linha contendo a somas dos dois números inteiros lidos, veja abaixo alguns exemplos de entradas e saídas.

**Exemplo de Entrada**

3 5

**Exemplo de Saída**

8

**Exemplo de Entrada**

100 505

**Exemplo de Saída**

605

*Author: Bruno Ribas*


#### **Código**

```asm
.data
output: .asciz "\n"

.text
main:
	li a7,5
	ecall
	mv t0, a0
	
	li a7, 5
	ecall
	mv t1, a0
	
        add t2, t0, t1
        
        li a7, 1		# Escreve inteiro
        mv a0, t2		# Move o conteudo de um registrador para outro (mv destino, origem)
        ecall
        
        li a7, 4
        la a0, output
        ecall
        
        li a0, 0		        # Indica codigo de saida bem sucedido
        li a7, 93		        # a7, 93 = encerrar programa  (EXIT)
        ecall          		    # EXECUTA OS COMANDOS A CIMA
```

<!-- tabs:end -->