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

baixe os esquemas [neste
link](http://nanasi.jp/old/colorscheme_0.html) 

