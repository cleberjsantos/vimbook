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

### Função para barra de status

         set statusline=%F%m%r%h%w\
            [FORMAT=%{&ff}]\
            [TYPE=%Y]\
            [ASCII=\%03.3b]\
            [HEX=\%02.2B]\
            [POS=%04l,%04v][%p%%]\ [LEN=%L]

Caso este código não funcione acesse [este
link](http://vim.wikia.com/wiki/Writing_a_valid_statusline) 

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

### Função para numerar linhas

No site wikia há um código de função para [numerar
linhas](http://vim.wikia.com/wiki/Number_a_group_of_lines) 

### Função para trocar o esquema de cores

         function! <SID>SwitchColorSchemes()
           if exists(``e'')
            if g:colors_name == 'native'
              colorscheme billw
            elseif g:colors_name == 'billw'
              colorscheme desert
            elseif g:colors_name == 'desert'
              colorscheme navajo-night
            elseif g:colors_name == 'navajo-night'
              colorscheme  zenburn
            elseif g:colors_name == 'zenburn'
              colorscheme bmichaelsen
            elseif g:colors_name == 'bmichaelsen'
              colorscheme wintersday
            elseif g:colors_name == 'wintersday'
              colorscheme summerfruit
            elseif g:colors_name == 'summerfruit'
              colorscheme native
            endif
           endif
         endfunction
         map <silent> <F6> :call <SID>SwitchColorSchemes()<CR>

baixe os esquemas [neste link](http://nanasi.jp/old/colorscheme_0.html) 

### Uma função para inserir cabeçalho de script

para chamar a função basta pressionar `,sh` em modo normal

         " Cria um cabeçalho para scripts bash
         fun! InsertHeadBash()
            normal(1G)
            :set ft=bash
            :set ts=4
            call append(0, ``h'')
            call append(1, ``:'' . strftime("%a %d/%b/%Y hs %H:%M"))
            call append(2, "# ultima modificação:``(''%a %d/%b/%Y hs %H:%M"))
            call append(3, "# NOME DA SUA EMPRESA")
            call append(3, "# Propósito do script")
            normal($)
         endfun
         map ,sh :call InsertHeadBash()<cr>

### Função para inserir cabeçalhos Python

         " função para inserir cabeçalhos Python
         fun! BufNewFile_PY()
          normal(1G)
          :set ft=python
          :set ts=2
          call append(0, "#!/usr/bin/env python")
          call append(1, "# # -*- coding: ISO-8859-1 -*-")
          call append(2, ``:'' . strftime("%a %d/%b/%Y hs %H:%M"))
          call append(3, `` '' . strftime("%a %d/%b/%Y hs %H:%M"))
          call append(4, "# Instituicao: <+nome+>")
          call append(5, "# Proposito do script: <+descreva+>")
          call append(6, "# Autor: <+seuNome+>")
          call append(7, "# site: <+seuSite+>")
          normal gg
         endfun
         autocmd BufNewFile *.py call BufNewFile_PY()
         map ,py :call BufNewFile_PY()<cr>A

         " Ao editar um arquivo será aberto no último ponto em
         " que foi editado

         autocmd BufReadPost *
           \ if line('``\''``('''\``'') <= line(``$'') |
           \   exe ''normal g`\``" |
           \ endif

         " Permite recarregar o Vim para que modificações no
         " Próprio vimrc seja ativadas com o mesmo sendo editado
         nmap <F12> :<C-u>source $HOME/.vimrc <BAR> echo "Vimrc recarregado!"<CR>

Redimensionar janelas

         " Redimensionar a janela com
         " Alt-seta à direita e esquerda
         map <M-right> <Esc>:resize +2 <CR>
         map <M-left> <Esc>:resize -2 <CR>

### Função para pular para uma linha

         "ir para linha
         " ir para uma linha específica
         function! GoToLine()
         let ln = inputdialog("ir para a linha...")
         exe ``:'' . ln
         endfunction
         "no meu caso o mapeamento é com Ctrl-l
         "use o que melhor lhe convier
         imap <S-l> <C-o>:call GoToLine()<CR>
         nmap <S-l> :call GoToLine()<CR>

### Função para gerar backup

A função abaixo é útil para ser usada quando você vai editar um arquivo
gerando modificações significativas, assim você poderá restaurar o
backup se necessário

         " A mapping to make a backup of the current file.
         fun! WriteBackup()
            let fname = expand("%:p") . "__" . strftime("%d-%m-%Y--%H.%M.%S")
            silent exe ":w " . fname
            echo "Wrote " . fname
         endfun
         nnoremap <Leader>ba :call WriteBackup()<CR>

O atalho “*<leader>*” em geral é a barra invertida
`\`, na dúvida “*:help <leader>*”.


