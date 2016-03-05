Uma calculadora diferente
-------------------------

Sempre que for necessário digitar o resultado de uma expressão
matemática (portanto no modo de inserção) pode-se usar o atalho
“`Ctrl-r =`”, ele ativa o registro de expressões, na linha de
comando do Vim aparece um sinal de igual, digita-se então uma expressão
matemática qualquer tipo “`35\*6`” e em seguida pressiona-se
“`Enter`”, o Vim coloca então o resultado da expressão no
lugar desejado. Portanto não precisa-se recorrer a nenhuma calculadora
para fazer cálculos. Pode-se fazer uso do “Registro de Expressões”
dentro de macros, ou seja, ao gravar ações pode-se fazer uso deste
recurso, aumentando assim sua complexidade e poder! Para ler sobre
“macros” acesse a seção [sec:Gravando comandos] na . Para saber mais
sobre o “registro de expressões” leia a seção [sec:Registro de
expressões "=].

Na seção [sec:Calculadora Científica com o Vim] “Calculadora Científica
com o vim” página  há uma descrição sobre como fazer cálculos com maior
precisão e complexidade.

Se a intenção for apenas exibir um calculo na barra de comandos é
possível fazer algo assim:

        :echo 5.2 * 3


