Hábitos para Edição Efetiva {#cha:Hábitos para edição efetiva}
===========================

Um dos grandes problemas relacionados com os softwares é sua
subutilização. Por inércia o usuário tende a aprender o mínimo para a
utilização de um programa e deixa de lado recursos que poderiam lhe ser
de grande valia. O mantenedor do Vim, Bram Moolenaar[^1], recentemente
publicou vídeos e manuais sobre os “7 hábitos para edição efetiva de
textos”[^2], este capítulo pretende resumir alguns conceitos mostrados
por Bram Moolenaar em seu artigo.

Mova-se rapidamente no texto {#sec:Mova-se rapidamente no texto}
----------------------------

O capítulo [cha:Movendo-se no Documento], “Movendo-se no Documento”,
página  mostra uma série de comandos para agilizar a navegação no texto.
Memorizando estes comandos ganha-se tempo considerável, um exemplo
simples em que o usuário está na linha 345 de um arquivo decide ver o
conteúdo da linha 1 e em seguida voltar à linha 345:

         gg ....... vai para a linha 1
         '' ....... retorna ao último ponto em que estava

Fica claro portanto que a navegação rápida é um dos requisitos para
edição efetiva de documentos.

Use marcas
----------

veja a seção [sec:UsandoMarcas] na página .

         ma ..... em modo normal cria uma marca `a'
         'a ..... move o cursor até a marca `a'
         d'a .... deleta até a marca `a'
         y'a .... copia até a marca `a'

         gg ... vai para a linha 1 do arquivo
         G .... vai para a última linha do arquivo
         0 .... vai para o início da linha
         $ .... vai para o fim da linha
         fx ... pula até a próxima ocorrência de ``x''
         dfx .. deleta até a próxima ocorrência de ``x''
         g, ... avança na lista de alterações
         g; ... retrocede na lista de alterações
         p .... cola o que foi deletado/copiado abaixo
         P .... cola o que foi deletado/copiado acima
         H .... posiciona o cursor no primeiro caractere da tela
         M .... posiciona o cursor no meio da tela
         L .... posiciona o cursor na última linha da tela

         * ........ localiza a palavra sob o cursor
         % ........ localiza fechamentos de chaves, parênteses etc.
         g* ....... localiza palavra parcialmente

         '.  apostrofo + ponto retorna ao último local editado
         '' retorna ao local do ultimo salto

Suponha que você está procurando a palavra ‘argc’:

         /argc

Digita ‘n’ para buscar a próxima ocorrência

         n

Um jeito mais fácil seria:

         "coloque a linha abaixo no seu vimrc
         :set hlsearch

Agora use asterisco para destacar todas as ocorrências do padrão
desejado e use a letra ‘n’ para pular entre ocorrências, caso deseje
seguir o caminho inverso use ‘N’.

Use quantificadores {#Use quantificadores}
-------------------

Em modo normal você pode fazer

         10j ..... desce 10 linhas
         5dd ..... apaga as próximas 5 linhas
         :50 ..... vai para a linha 50
         50gg .... vai para a linha 50

Edite vários arquivos de uma só vez  {#Edite vários arquivos de uma só vez }
------------------------------------

O Vim pode abrir vários arquivos que contenham um determinado padrão. Um
exemplo seria abrir dezenas de arquivos HTML e trocar a ocorrência
`bgcolor="ffffff"` Para `bgcolor="eeeeee"` Usaríamos a seguinte
sequência de comandos:

         vim *.html  .............................. abre os arquivos
         :bufdo :%s/bgcolor=`ffffff'/bgcolor=`eeeeee'/g   substituição
         :wall .................................... salva todos
         :qa[ll] .................................... fecha todos

Ainda com relação à edição de vários arquivos poderíamos abrir alguns
arquivos <span>txt</span> e mudar de um para o outro assim:

         :wn

O ‘<span>w</span>’ significa gravar e o ‘<span>n</span>’ significa
<span>*next*</span>, ou seja, gravaríamos o que foi modificado no
arquivo atual e mudaríamos para o próximo.

Veja também “Movendo-se no documento”, capítulo [cha:Movendo-se no
Documento] página 

Não digite duas vezes {#Não digite duas vezes}
---------------------

-   O Vim complementa com ‘<span>tab</span>’. Veja mais na seção
    [Complementação com “tab”] na página .

-   Use macros. Detalhes na seção [sec:Gravando comandos] página .

-   Use abreviações coloque abreviações como abaixo em seu `~/.vimrc`.
    Veja mais na seção [Abreviações].

-   As abreviações fazem o mesmo que auto-correção e auto-texto em
    outros editores

<!-- -->

         iab tambem também
         iab linux GNU/Linux

No modo de inserção você pode usar:

         Ctrl-y  ........ copia caractere a caractere a linha acima
         Ctrl-e  ........ copia caractere a caractere a linha abaixo
         Ctrl-x Ctrl-l .. completa linhas inteiras

Para um trecho muito copiado coloque o seu conteúdo em um registrador:

         "ayy ... copia a linha atual para o registrador `a'
         "ap  ... cola o registrador `a'

Crie abreviações para erros comuns no seu arquivo de configuração
( /.vimrc):

         iabbrev teh the
         syntax keyword WordError teh

As linhas acima criam uma abreviação para erro de digitação da palavra
‘the’ e destaca textos que você abrir que contenham este erro.

Use dobras {#sec:Use folders}
----------

O Vim pode ocultar partes do texto que não estão sendo utilizadas
permitindo uma melhor visualização do conteúdo. Mais detalhes no
capítulo [cha:Folders] página .

Use autocomandos {#Use autocomandos}
----------------

No arquivo de configuração do Vim `~/.vimrc` pode-se pode criar comandos
automáticos que serão executados diante de uma determinada
circunstância. O comando abaixo será executado em qualquer arquivo
existente, ao abrir o mesmo, posicionando o cursor no último local
editado:

         "autocmd BufEnter * lcd %:p:h
         autocmd BufReadPost *
           \ if line("'\"") > 0 && line("'\"") <= line("$") |
           \   exe "normal g`\"" |
           \ endif

Grupo de comandos para arquivos do tipo ‘<span>html</span>’. Observe que
o autocomando carrega um arquivo de configuração do Vim exclusivo para o
tipo <span>html/htm</span> e no caso de arquivos novos
‘<span>BufNewFile</span>’ ele já cria um esqueleto puxando do endereço
indicado:

    augroup html
     au! <--> Remove all html autocommands
      au!
      au BufNewFile,BufRead *.html,*.shtml,*.htm set ft=html
      au BufNewFile,BufRead,BufEnter  *.html,*.shtml,*.htm so ~/docs/vim/.vimrc-html
      au BufNewFile *.html 0r ~/docs/vim/skel.html
      au BufNewFile *.html*.shtml,*.htm /body/+  " coloca o cursor após o corpo <body>
      au BufNewFile,BufRead *.html,*.shtml,*.htm set noautoindent
    augroup end

Use o File Explorer {#Use o file explorer}
-------------------

O Vim pode navegar em pastas assim:

         vim .

Você pode usar ‘<span>j</span>’ e ‘<span>k</span>’ para navegar e
<span>Enter</span> para editar o arquivo selecionado:

Torne as boas práticas um hábito  {#Torne as boas práticas um hábito }
---------------------------------

Para cada prática produtiva procure adquirir um hábito e mantenha-se
atento ao que pode ser melhorado. Imagine tarefas complexas, procure um
meio melhor de fazer e torne um hábito.

Referências
-----------

-   <http://www.moolenaar.net/habits_2007.pdf> por Bram Moolenaar

-   <http://vim.wikia.com/wiki/Did_you_know>

[^1]: http://www.moolenaar.net

[^2]: http://br-linux.org/linux/7-habitos-da-edicao-de-texto-efetiva
