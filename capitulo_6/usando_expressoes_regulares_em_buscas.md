Usando “Expressões Regulares” em buscas
----------------------------------------------------------

         / ........... inicia uma busca (modo normal)
         \%x69 ....... código da letra `i'
         /\%x69 ...... localiza a letra `i' - hexadecimal 069
         \d .......... localiza números
         [3-8] ....... localiza números de 3 até 8
         ^ ........... começo de linha
         $ ........... final de linha
         \+ .......... um ou mais
         /^\d\+$ ..... localiza somente dígitos
         /\r$ ........ localiza linhas terminadas com ^M
         /^\s*$ ...... localiza linhas vazias ou contendo apenas espaços
         /^\t\+ ...... localiza linhas que iniciam com tabs
         \s .......... localiza espaços
         /\s\+$ ...... localiza espaços no final da linha
