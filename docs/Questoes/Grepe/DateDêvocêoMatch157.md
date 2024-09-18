<center>

# Compiladores 1

</center>

---

# Date: Dê você o Match

<!-- tabs:start -->

#### **Questão**

 author: Edson Alves, mojificado por Bruno Ribeiro 

**Preâmbulo**

 As expectativas legais e culturais para a representação de datas e horários variam entre os países, sendo importante estar ciente das formas de datas totalmente numéricas utilizadas em um país específico para saber qual data é pretendida. Os escritores tradicionalmente escrevem datas abreviadas de acordo com o costume local, criando equivalentes totalmente numéricos para os formatos dia-mês, como "29 de março de 2024" (29/03/24, 29/03/2024, 29/3/2024, 29-03-2024, 29.03.2024, etc), e formatos mês-dia, como "29 de março de 2024" (03/29/24 ou 03/29/2024). Isso pode resultar em datas que são impossíveis de entender corretamente sem conhecer o contexto. Por exemplo, dependendo do estilo de ordenação, a data abreviada "01/11/06" pode ser interpretada como "1 de novembro de 2006" para DMY, "11 de janeiro de 2006" para MDY e "6 de novembro de 2001" para YMD. Dentre os diferentes formatos para datas está o formato DD/MM/YYYY, majoritariamente utilizado no Brasil, onde o dia e o mês são representados por exatamente dois dígitos decimais e o ano por quatro dígitos. Mesmo impondo restrições aos possíveis valores como, por exemplo, 1 ≤ DD ≤ 31 , 1 ≤ M M ≤ 12 e 1900 ≤ Y Y Y Y ≤ 2024 , ainda é possível representar datas inválidas. Por exemplo, 31/06/2023 e 29/02/2022 são datas inválidas, pois junho tem apenas 30 dias e 2022 não foi um ano bissexto, respectivamente. Sua missão é dado um arquivo que pode conter datas no formato apresentado, escreva uma expressão regular ( RegEx ) em um arquivo .grepe a qual identifique quais delas são, de fato, datas válidas. 

**Arquivo**

 O arquivo .grepe será o equivalente a execução do seguinte comando no terminal em ambiente Unix: $ grep -o -E ' regex ' input No qual regex é a expressão regular que resolve o problema e input é o arquivo com os casos a serem testados. Portanto, o arquivo deve conter única e exclusivamente apenas uma linha, a qual deve apresentar a expressão regular regex para o problema proposto. 

**Entrada**

 A entrada é composta por um único caso de teste, contendo N ( N > 0 ) linhas. As linhas podem D ( D ≥ 0 ) possíveis datas a serem analisadas. 

**Saída**

 Seu programa deverá imprimir as E ( E ≥ 0 ) datas corretas de cada caso de teste. Exemplos 

**Exemplo de entrada**

 14/06/2023 31/06/2023 29/02/2000 29/02/2022 12/34/5678 abcd 12345 ? FIM 



**Exemplo de saída**

 14/06/2023 29/02/2000 

Autor: author: Edson Alves, mojificado por Bruno Ribeiro 

#### **Código**

```grepe
((((0[1-9]|[12][0-9]|3[01])/(0[13578]|1[02]))|((0[1-9]|[12][0-9]|30)/(0[469]|11))|((0[1-9]|1[0-9]|2[0-8])/02))/((19[0-9]{2})|(20[01][0-9])|202[0-4]))|(29/02/(19((04|08)|[2468][048]|[13579][26])|20([02][048]|1[26])))


```

<!-- tabs:end -->

