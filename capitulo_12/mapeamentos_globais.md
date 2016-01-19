### Mapeamentos globais 

Podemos fazer mapeamentos globais ou que funcionam em apenas um modo:

         map  - funciona em qualquer modo
         nmap - apenas no modo Normal
         imap - apenas no modo de Inserção

Mover linhas com *Ctrl-$\downarrow$* ou
*Ctrl-$\uparrow$*:

         " tem que estar em modo normal!
         nmap <C-Down> ddp
         nmap <C-Up> ddkP

Salvando com uma tecla de função:

         " salva com F9
         nmap <F9> :w<cr>
         " F10 - sai do Vim
         nmap <F10> <Esc>:q<cr>


