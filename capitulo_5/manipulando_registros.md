Manipulando registros
---------------------

         :let @a=@_   ... limpa o registro a
         :let @a=``'' ... limpa o registro a
         :let @a=@"   ... salva registro sem nome *N*
         :let @*=@a   ... copia o registro para o buffer de colagem
         :let @*=@:   ... copia o ultimo comando para o buffer de
                          colagem
         :let @*=@/   ... copia a última busca para o buffer de
                          colagem
         :let @*=@%   ... copia o nome do arquivo para o buffer de
                          colagem
         :reg         ... mostra o conteúdo de todos os registros

Em modo de inserção

         <C-R>-   ....... Insere o registro de pequenas deleções
         <C-R>[0-9a-z] .. Insere registros 0-9 e a-z
         <C-R>%        .. Insere o nome do arquivo
         <C-R>=somevar .. Insere o conteúdo de uma variável
         <C-R><C-A> ..... Insere `Big-Words' veja seção 2.1

Um exemplo: pré-carregando o nome do arquivo no registro `n`.

coloque em seu `~/.vimrc`

         let @n=@%

Como foi atribuído ao registro `n` o conteúdo de @%, ou seja, o nome do
arquivo, você pode fazer algo assim em modo de inserção:

         Ctrl-r n

E o nome do arquivo será inserido.
