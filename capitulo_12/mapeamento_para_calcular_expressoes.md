### Mapeamento para Calcular Expressões 

Os mapeamentos abaixo exibem o resultado das quatro operações básicas
(soma, subtração, multiplicação e divisão). O primeiro para o modo
normal no qual posiciona-se o cursor no primeiro caractere da expressão
tipo “*5\*9*” e em seguida pressiona-se
“*Shift-F1*”, o segundo para o modo **insert** em
que, após digitada a expressão pressiona-se o mesmo atalho.

        " calculadora
        map <s-f1> <esc>0"myEA=<c-r>=<c-r>m<enter><esc>
        imap <s-f1> <space><esc>"myBEa=<c-r>=<c-r>m<enter><del>

Para efetuar cálculos com maior precisão e também resolver problemas
como potências raízes, logaritmos pode-se mapear comandos externos, como
a biblioteca matemática da linguagem de programação Python. [Neste
link](http://vim.wikia.com/wiki/Scientific_calculator) @CientificCalculator
há um manual que ensina a realizar este procedimento, ou acesse o
capítulo [Uma calculadora diferente] na página  .


