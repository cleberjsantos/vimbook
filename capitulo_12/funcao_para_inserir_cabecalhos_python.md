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

