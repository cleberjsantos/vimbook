### Habilitação automática na inicialização

Às vezes torna-se cansativo a digitação explícita do comando de
habilitação da verificação ortográfica sempre quando desejada. Seria
conveniente se o Vim habilitasse automaticamente a verificação para
aqueles tipos de arquivos que comumente fazem uso da verificação
ortográfica, como por exemplo arquivos “texto”. Isto é possível
editando-se o arquivo de configuração do Vim .vimrc(veja [Como Editar Preferências no Vim](capitulo_12/como_editar_preferencias_no_vim.md)) e incluindo as seguintes linhas:

         autocmd Filetype text setl spell spl=pt
         autocmd BufNewFile,BufRead *.txt setl spell spl=pt

Assim habilita-se automaticamente a verificação ortográfica usando o
dicionário da língua portuguesa (pt) para arquivos do tipo
texto e os terminados com a extensão .txt.
Mais tecnicamente, diz-se ao Vim para executar o comando
`setl spell spl=pt` sempre quando o tipo do arquivo
(Filetype) for text (texto) ou quando um
arquivo com extensão .txt for carregado
(BufRead) ou criado (BufNewFile).
