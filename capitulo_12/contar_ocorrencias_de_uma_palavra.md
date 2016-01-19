### Contar ocorrências de uma palavra

         " contagem de ocorrências de uma palavra (case insensitive)
         " busca somente ocorrências exatas
         nmap <F4> <esc>mz:%s/\c\<\(<c-r>=expand("<cword>")<cr>\)\>//gn<cr>`z
         " busca parcial, ou seja acha palavra como parte de outra
         nmap <s-F4> <esc>mz:%s/\c\(<c-r>=expand("<cword>")<cr>\)//gn<cr>`z


