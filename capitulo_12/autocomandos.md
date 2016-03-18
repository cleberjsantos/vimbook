Autocomandos
------------

Autocomandos habilitam comandos automáticos para situações específicas.
Para executar determinada ação ao iniciar um novo arquivo o autocomando
deverá obedecer este padrão:

         au BufNewFile tipo ação

Veja um exemplo:

         au BufNewFile,BufRead *.txt source ~/.vim/syntax/txt.vim

No exemplo acima o Vim aplica autocomandos para arquivos novos
“*BufNewfile*” ou existentes “*BufRead*”
terminados em `txt`, e para estes tipos carrega um arquivo de
**syntax**, ou seja, um esquema de cores específico.

         " http://aurelio.net/doc/vim/txt.vim    coloque em ~/.vim/syntax
         au BufNewFile,BufRead *.txt source ~/.vim/syntax/txt.vim

Para arquivos do tipo texto ‘*.txt*’ use um arquivo de
**syntax** em particular.

O autocomando abaixo coloca um cabeçalho para **scripts**
*bash* caso a linha 1 esteja vazia, observe que os arquivos
em questão tem que ter a extensão *.sh*.

         au BufNewFile,BufRead *.sh if getline(1) == "" | normal ,sh

Para configurar o vim de modo que o diretório corrente fique no
**path** coloque este código no `vimrc`.

         "fonte: wikia - wiki sobre o vim
         if exists('+autochdir')
           set autochdir
         else
           autocmd BufEnter * silent! lcd %:p:h:gs/ /\\ /
         endif


