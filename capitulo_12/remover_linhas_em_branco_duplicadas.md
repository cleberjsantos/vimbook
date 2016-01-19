### Remover linhas em branco duplicadas  

         map ,d <Esc>:%s/\(^\n\{2,}\)/\r/g<cr>

No mapeamento acima estamos associando o atalho:

         ,d

… à ação desejada, fazer com que linhas em branco sucessivas sejam
substituídas por uma só linha em branco, vejamos como funciona:

         map ......... mapear
         ,d .......... atalho que quermos
         <Esc> ....... se estive em modo de inserção sai
         : ........... em modo de comando
         % ........... em todo o arquivo
         s ........... substitua
         \n .......... quebra de linha
         {2,} ........ duas ou mais vezes
         \r .......... trocado por \r Enter
         g ........... globalmente
         <cr> ........ confirmação do comando

As barras invertidas podem não ser usadas se o seu Vim estiver com a
opção **magic** habilitada

         :set magic

Por acaso este é um padrão portanto tente usar assim pra ver se funciona

         map ,d :%s/\n{2,}/\r/g<cr>

