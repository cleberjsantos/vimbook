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

