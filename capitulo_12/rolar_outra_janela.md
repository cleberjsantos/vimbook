### Rolar outra janela

Se você dividir janelas tipo

         Ctrl-w n

pode colocar esta função no seu `.vimrc`

         " rola janela alternativa
         fun! ScrollOtherWindow(dir)
         if a:dir == ``n''
            let move = ``>''
         elseif a:dir == ``p''
            let move = ``>''
         endif
         exec ``p'' . move . ``p''
         endfun
         nmap <silent> <M-Down> :call ScrollOtherWindow(``n'')<CR>
         nmap <silent> <M-Up> :call ScrollOtherWindow(``p'')<CR>

Esta função é acionada com o atalho *Alt-⬆* e
*Alt-⬇*.

