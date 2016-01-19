Mapeamentos 
-----------

Mapeamentos permitem criar atalhos de teclas para quase tudo. Tudo
depende da criatividade do usuário e do quanto conhece o Vim, com eles
podemos controlar ações com quaisquer teclas, mas antes temos que saber
que para criar mapeamentos, precisamos conhecer a maneira de representar
as teclas e combinações. Alguns exemplos:

         tecla ....... tecla mapeada
         <c-x> ....... Ctrl-x
         <left> ...... seta para a esquerda
         <right> ..... seta para a direita
         <c-m-a> ..... Ctrl-Alt-a
         <cr> ........ Enter
         <Esc> ....... Escape
         <leader> .... normalmente \
         <bar> ....... | pipe
         <cword> ..... palavra sob o cursor
         <cfile> ..... arquivo sob o cursor
         <cfile> ..... arquivo sob o cursor sem extensão
         <sfile> ..... conteúdo do arquivo sob o cursor
         <left> ...... salta um caractere para esquerda
         <up> ........ equivale clicar em `seta acima'
         <m-f4> ...... a tecla alt -> m  mais a tecla f4
         <c-f> ....... Ctrl-f
         <bs> ........ backspace
         <space> ..... espaço
         <tab> ....... tab

No Vim podemos mapear uma tecla para o modo normal, realizando
determinada operação e a mesma tecla pode desempenhar outra função
qualquer em modo de inserção ou comando, veja:

         " mostra o nome do arquivo com o caminho
         map <F2> :echo expand("%:p")
         " insere um texto qualquer
         imap <F2> Nome de uma pessoa

A única diferença nos mapeamentos acima é que o mapeamento para modo de
inserção começa com ‘`i`’, assim como para o modo “comando” ‘`:`’ começa
com ‘`c`’ no caso ‘`cmap`’. O comando ‘`:echo`’ pode ser abreviado
assim: ‘`:ec`’.


