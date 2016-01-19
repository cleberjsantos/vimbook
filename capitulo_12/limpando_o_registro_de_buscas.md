### Limpando o “registro” de buscas 

A cada busca, se a opção ‘*hls*’[^1] estiver habilitada o Vim
faz um destaque colorido, para desabilitar esta opção pode-se criar um
mapeamento qualquer, no caso abaixo usando a combinação de teclas
“`<S-F11>`”.

         nno <S-F11> <Esc>:let @/=""<CR>

É um mapeamento para o modo normal que faz com que a combinação de
teclas `Shift-F11` limpe o “registro” de buscas

[^1]: hls é uma abreviação de hightlight search
