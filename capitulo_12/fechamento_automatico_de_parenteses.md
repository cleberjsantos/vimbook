Funções 
-------

### Fechamento automático de parênteses 

         " --------------------------------------
         " Ativa fechamento automático para parêntese
         " Set automatic expansion of parenthesis/brackets
         inoremap ( ()<Esc>:call BC_AddChar(``)'')<cr>i
         inoremap { {}<Esc>:call BC_AddChar(``}'')<cr>i
         inoremap [ []<Esc>:call BC_AddChar(``]'')<cr>i
         `` '' ``''<Esc>:call BC_AddChar(``''")<cr>i
         "
         " mapeia Ctrl-j para pular fora de parênteses colchetes etc...
         inoremap <C-j> <Esc>:call search(BC_GetChar(), ``W'')<cr>a
         " Function for the above
         function! BC_AddChar(schar)
            if exists(``k'')
                let b:robstack = b:robstack . a:schar
            else
                let b:robstack = a:schar
            endif
         endfunction
         function! BC_GetChar()
            let l:char = b:robstack[strlen(b:robstack)-1]
            let b:robstack = strpart(b:robstack, 0, strlen(b:robstack)-1)
            return l:char
         endfunction
        
        '''Outra opção para fechamento de parênteses'''
        
         " Fechamento automático de parênteses
         imap { {}<left>
         imap ( ()<left>
         imap [ []<left>
        
         " pular fora dos parênteses, colchetes e chaves, mover o cursor
         " no modo de inserção
         imap <c-l> <Esc><right>a
         imap <c-h> <Esc><left>a


