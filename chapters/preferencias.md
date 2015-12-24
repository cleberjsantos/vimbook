Como Editar Preferências no Vim {#cha:Como editar preferências no Vim}
===============================

O arquivo de preferências do Vim é nomeado <span>vimrc</span>, um
arquivo oculto que normalmente encontra-se no diretório de trabalho
(<span>*home*</span>) do usuário:

         ~/.vimrc
         /home/usuario/.vimrc

No sistema operacional Windows o arquivo costuma ser:

         ~\_vimrc
         c:\documents and settings\usuario\_vimrc

Onde colocar <span>*plugins*</span> e temas de cor {#Onde colocar plugins e temas de cor}
--------------------------------------------------

No Windows deve haver uma pasta chamada ‘<span>vimfiles</span>’ (caso
não exista deve-se criá-la), que fica em:

         c:\documents and settings\usuario\vimfiles

No GNU/Linux a pasta de arquivos do Vim é chamada <span>.vim</span>,
comumente armazenada em

         /home/user/.vim

Tanto em <span>.vim</span> como <span>vimfiles</span> encontram-se
usualmente as seguintes pastas:

         vimfiles ou .vim
            |
            +--color
            |
            +--doc
            |
            +--syntax
            |
            +--plugin

Os <span>*plugins*</span>, como se pode deduzir, devem ser colocados no
diretório denominado <span>plugin</span>. Na seção Plugins [Plugins] (p.
) estão descritos alguns <span>*plugins*</span> para o Vim.

Comentários  {#Comentários }
------------

Comentários são linhas que são ignoradas pelo interpretador Vim e servem
normalmente para descrição de comandos e ações, deixando portanto mais
legível e didático o arquivo de configuração. Uma linha é um comentário
se seu primeiro caractere é uma aspa ‘`"`’:

         " linhas começadas com aspas são comentários
         " e portanto serão ignoradas pelo Vim

Recomenda-se usar comentários ao adicionar ou modificar comandos no
arquivo <span>vimrc</span>, pois assim torna-se mais fácil futuras
leituras e modificações neste arquivo.

Efetivação das alterações no `vimrc` {#Efetivação das alterações no vimrc}
------------------------------------

As alterações no <span>vimrc</span> só serão efetivadas na próxima vez
que o Vim for aberto, a não ser que o recarregamento do arquivo de
configuração seja instruído explicitamente:

         :source ~/vimrc ....... se estiver no GNU/Linux
         :source ~/_vimrc ...... caso use o Windows
         :so arquivo ........... `so' é uma abreviação de `source'

<span>*Set*</span> {#Set}
------------------

Os comandos <span>set</span>, responsáveis por atribuir valores à
variáveis, podem ser colocados no `.vimrc`:

         set nu

ou digitados como comandos:

         :set nu

    set number ............... "mostra numeração de linhas
    set nu ................... "simplificação de `number'
    set showmode ............. "mostra o modo em que estamos
    set showcmd .............. "mostra no status os comandos inseridos
    set tabstop=4 ............ "tamanho das tabulações
    set ts=4 ................. "simplificação de `tabstop'
    set shiftwidth=4 ......... "quantidade de espaços de uma
                                tabulação
    set sw=4 ................. "simplificação de `shiftwidth'
    syntax on ................ "habilita cores
    syn on ................... "simplificação de `syntax'
    colorscheme tema ......... "esquema de cores `syntax highlight'
    autochdir ................ "configura o diretório de trabalho
    set hls .................. "destaca com cores os termos procurados
    set incsearch ............ "habilita a busca incremental
    set ai ................... "auto identação
    set aw ................... "salva automaticamente ao trocar de
                                `buffer'
    set ignorecase ........... "ignora maiúsculas e minúsculas nas
                                buscas
    set ic ................... "simplificação de ignorecase
    set smartcase ............ "numa busca em maiúsculo habilita
                                `case'
    set scs .................. "sinônimo de `smartcase'
    set backup ............... "habilita a criação de arquivos de
                                backup
    set bk ................... "simplificação de `backup'
    set backupext=.backup .... "especifica a extensão do arquivo de
                                backup
    set bex=.backup .......... "simplificação de backupext
    set backupdir=~/.backup,./ "diretório(s) para arquivos de backup
    set bdir ................. "simplificação de `backupdir'
    set nobackup ............. "evita a criação de arquivos de backup
    ste nobk ................. "simplificação de `nobackup'
    set cursorline ........... "abreviação de cursor line (destaca
                                linha  atual)
    set cul .................. "simplificação de `cursorline'
    set ttyfast .............. "melhora o redraw de janelas.
    set columns=88 ........... "deixa a janela com 88 colunas.
    set mousemodel=popup ..... "exibe o conteúdo de folders e
                                sugestões spell
    set viminfo=%,'50,\"100,/100,:100,n "armazena opções (buffers)

Se ao iniciar o vim obtivermos mensagens de erros e houver dúvida se o
erro é no vim ou em sua configuração, pode-se inicia-lo sem que o mesmo
carregue o arquivo ‘`.vimrc`’.

        :vim -u NONE

Ajustando parágrafos em modo normal
-----------------------------------

[sec:Ajustando parágrafos em modo normal]

O comando ‘`gqap`’ ajusta o parágrafo atual em modo normal. usando a
opção ‘<span>:set nojoinspaces</span>’ o vim colocará dois espaços após
o ponto final ao se ajustar os parágrafos.

geralmente usamos ‘`^I`’ para representar uma tabulação \<Tab\>, e ‘`$`’
para indicar o fim de linha. Mas é possível customizar essas opções.
sintaxe:

        
         set listchars=key:string,key:string                        

          - eol:{char} 
          Define o caracter a ser posto depois do fim da linha  

          - tab:{char1}{char2} 
          O tab é mostrado pelo primeiro caracter {char1} e     
          seguido por {char2}                                   

          - trail:{char}                                            
          Esse caracter representa os espaços em branco.        
                                                                    
          - extends:{char}                                          
          Esse caracter representa o início do fim da linha      
          sem quebrá-la                                          
          Está opção funciona com a opção nowrap habilitada       
                                                                    
         "exemplo 1:
         "set listchars=tab:>-,trail:.,eol:#,extends:@
         
         "exemplo 2:
         "set listchars=tab:>-
         
         "exemplo 3:
         "set listchars=tab:>-
         
         "exemplo 4:
         set nowrap    "Essa opção desabilita a quebra de linha
         "set listchars=extends:+
         
         Caso esteja usando o gvim pode setar um esquema de cores
         set colo desert

Exibindo caracteres invisíveis {#Exibindo caracteres invisíveis}
------------------------------

         :set list

Definindo registros previamente {#Definindo registros previamente}
-------------------------------

Definindo uma macro de nome `s` para ordenar e retirar linhas duplicadas

         let @s=":sort u"

Para executar o registro `s` definido acima faça:

         @s

O Vim colocará no comando

         :sort -u

Bastando pressionar `<Enter>`. Observação: Este registro prévio pode
ficar no `vimrc` ou ser digitado em comando “:”

         :5,20sort u
         "da linha 5 até a linha 20 ordene e retire duplicados
         
         :sort n
         " ordene meu documento considerando números
         " isto é útil pois se a primeira coluna contiver
         " números a ordenação pode ficar errada caso não usemos
         " o parâmetro ``n''

Mapeamentos {#Mapeamentos}
-----------

Mapeamentos permitem criar atalhos de teclas para quase tudo. Tudo
depende da criatividade do usuário e do quanto conhece o Vim, com eles
podemos controlar ações com quaisquer teclas, mas antes temos que saber
que para criar mapeamentos, precisamos conhecer a maneira de representar
as teclas e combinações. Alguns exemplos:

         tecla ....... tecla mapeada
         <c-x> ....... Ctrl-x
         <left> ...... seta para a esquerda
         <right> ..... seta para a direita
         <c-m-a> ..... Ctrl-Alt-a
         <cr> ........ Enter
         <Esc> ....... Escape
         <leader> .... normalmente \
         <bar> ....... | pipe
         <cword> ..... palavra sob o cursor
         <cfile> ..... arquivo sob o cursor
         <cfile> ..... arquivo sob o cursor sem extensão
         <sfile> ..... conteúdo do arquivo sob o cursor
         <left> ...... salta um caractere para esquerda
         <up> ........ equivale clicar em `seta acima'
         <m-f4> ...... a tecla alt -> m  mais a tecla f4
         <c-f> ....... Ctrl-f
         <bs> ........ backspace
         <space> ..... espaço
         <tab> ....... tab

No Vim podemos mapear uma tecla para o modo normal, realizando
determinada operação e a mesma tecla pode desempenhar outra função
qualquer em modo de inserção ou comando, veja:

         " mostra o nome do arquivo com o caminho
         map <F2> :echo expand("%:p")
         " insere um texto qualquer
         imap <F2> Nome de uma pessoa

A única diferença nos mapeamentos acima é que o mapeamento para modo de
inserção começa com ‘`i`’, assim como para o modo “comando” ‘`:`’ começa
com ‘`c`’ no caso ‘`cmap`’. O comando ‘`:echo`’ pode ser abreviado
assim: ‘`:ec`’.

### Recarregando o arquivo de configuração {#sec:Recarregando o arquivo de configuração}

Cada alteração no arquivo de configuração do Vim só terá efeito na
próxima vez que você abrir o Vim a menos que você coloque isto dentro do
mesmo

         " recarregar o vimrc
         " Source the .vimrc or _vimrc file, depending on system
         if &term == "win32" || "pcterm" || has("gui_win32")
            map ,v :e $HOME/_vimrc<CR>
            nmap <F12> :<C-u>source ~/_vimrc <BAR> echo "Vimrc recarregado!"<CR>
         else
            map ,v :e $HOME/.vimrc<CR>
            nmap <F12> :<C-u>source ~/.vimrc <BAR> echo "Vimrc recarregado!"<CR>
         endif

Agora basta pressionar “`<F12>`” em modo normal e as alterações passam a
valer instantaneamente, e para chamar o ‘`vimrc`’ basta usar.

         ,v

Os mapeamentos abaixo são úteis para quem escreve códigos HTML, permitem
inserir caracteres reservados do HTML usando uma barra invertida para
proteger os mesmos, o Vim substituirá os “barra alguma coisa” pelo
caractere correspondente.

         inoremap \&amp; &amp;amp;
         inoremap \&lt; &amp;lt;
         inoremap \&gt; &amp;gt;
         inoremap \. &amp;middot;

O termo <span>*inoremap*</span> significa: em modo de inserção não
remapear, ou seja ele mapeia o atalho e não permite que o mesmo seja
remapeado, e o mapeamento só funciona em modo de inserção, isso
significa que um atalho pode ser mapeado para diferentes modos de
operação.\

Veja este outro mapeamento:

         map <F11> <Esc>:set nu!<cr>

Permite habilitar ou desabilitar números de linha do arquivo corrente. A
exclamação ao final torna o comando booleano, ou seja, se a numeração
estiver ativa será desabilitada, caso contrário será ativada. O “`<cr>`”
ao final representa um <span>Enter</span>.

### Limpando o “registro” de buscas {#Limpando o ``registro'' de buscas}

A cada busca, se a opção ‘<span>hls</span>’[^1] estiver habilitada o Vim
faz um destaque colorido, para desabilitar esta opção pode-se criar um
mapeamento qualquer, no caso abaixo usando a combinação de teclas
“`<S-F11>`”.

         nno <S-F11> <Esc>:let @/=""<CR>

É um mapeamento para o modo normal que faz com que a combinação de
teclas `Shift-F11` limpe o “registro” de buscas

### Destacar palavra sob o cursor  {#Destacar palavra sob o cursor }

         nmap <s-f> :let @/=">"<CR>

O atalho acima ‘`s-f`’ corresponde a ‘`Shift-f`’.

### Contar ocorrências de uma palavra

[sub:Contar ocorrências de uma palavra]

         " contagem de ocorrências de uma palavra (case insensitive)
         " busca somente ocorrências exatas
         nmap <F4> <esc>mz:%s/\c\<\(<c-r>=expand("<cword>")<cr>\)\>//gn<cr>`z
         " busca parcial, ou seja acha palavra como parte de outra
         nmap <s-F4> <esc>mz:%s/\c\(<c-r>=expand("<cword>")<cr>\)//gn<cr>`z

### Remover linhas em branco duplicadas  {#Remover linhas em branco duplicadas }

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
opção <span>*magic*</span> habilitada

         :set magic

Por acaso este é um padrão portanto tente usar assim pra ver se funciona

         map ,d :%s/\n{2,}/\r/g<cr>

### Mapeamento para Calcular Expressões {#sub:Mapeamento para Calcular Expressões}

Os mapeamentos abaixo exibem o resultado das quatro operações básicas
(soma, subtração, multiplicação e divisão). O primeiro para o modo
normal no qual posiciona-se o cursor no primeiro caractere da expressão
tipo “<span>5\*9</span>” e em seguida pressiona-se
“<span>Shift-F1</span>”, o segundo para o modo <span>*insert*</span> em
que, após digitada a expressão pressiona-se o mesmo atalho.

        " calculadora
        map <s-f1> <esc>0"myEA=<c-r>=<c-r>m<enter><esc>
        imap <s-f1> <space><esc>"myBEa=<c-r>=<c-r>m<enter><del>

Para efetuar cálculos com maior precisão e também resolver problemas
como potências raízes, logaritmos pode-se mapear comandos externos, como
a biblioteca matemática da linguagem de programação Python. [Neste
link](http://vim.wikia.com/wiki/Scientific_calculator) @CientificCalculator
há um manual que ensina a realizar este procedimento, ou acesse o
capítulo [Uma calculadora diferente] na página  .

### Mapeamentos globais {#sub:Mapeamentos globais}

Podemos fazer mapeamentos globais ou que funcionam em apenas um modo:

         map  - funciona em qualquer modo
         nmap - apenas no modo Normal
         imap - apenas no modo de Inserção

Mover linhas com <span>Ctrl-$\downarrow$</span> ou
<span>Ctrl-$\uparrow$</span>:

         " tem que estar em modo normal!
         nmap <C-Down> ddp
         nmap <C-Up> ddkP

Salvando com uma tecla de função:

         " salva com F9
         nmap <F9> :w<cr>
         " F10 - sai do Vim
         nmap <F10> <Esc>:q<cr>

### Convertendo as iniciais de um documento para maiúsculas {#Convertendo as iniciais de um documento para maiúsculas}

         " MinusculasMaiusculas: converte a primeira letra de cada
         " frase para MAIÚSCULAS
         nmap ,mm :%s/\C\([.!?][])"']*\($\|[ ]\)\_s*\)\(\l\)/\1\U\3/g<CR>
         " Caso queira confirmação coloque uma letra ``c'' no final da 
         " linha acima:
         " (...) \3/gc<CR>

Autocomandos  {#Autocomandos }
-------------

Autocomandos habilitam comandos automáticos para situações específicas.
Para executar determinada ação ao iniciar um novo arquivo o autocomando
deverá obedecer este padrão:

         au BufNewFile tipo ação

Veja um exemplo:

         au BufNewFile,BufRead *.txt source ~/.vim/syntax/txt.vim

No exemplo acima o Vim aplica autocomandos para arquivos novos
“<span>BufNewfile</span>” ou existentes “<span>BufRead</span>”
terminados em `txt`, e para estes tipos carrega um arquivo de
<span>*syntax*</span>, ou seja, um esquema de cores específico.

         " http://aurelio.net/doc/vim/txt.vim    coloque em ~/.vim/syntax
         au BufNewFile,BufRead *.txt source ~/.vim/syntax/txt.vim

Para arquivos do tipo texto ‘<span>.txt</span>’ use um arquivo de
<span>*syntax*</span> em particular.

O autocomando abaixo coloca um cabeçalho para <span>*scripts*</span>
<span>bash</span> caso a linha 1 esteja vazia, observe que os arquivos
em questão tem que ter a extensão ‘<span>.sh</span>’.

         au BufNewFile,BufRead *.sh if getline(1) == "" | normal ,sh

Para configurar o vim de modo que o diretório corrente fique no
<span>*<span>path</span>*</span> coloque este código no ‘`vimrc`’.

         "fonte: wikia - wiki sobre o vim
         if exists('+autochdir')
           set autochdir
         else
           autocmd BufEnter * silent! lcd %:p:h:gs/ /\\ /
         endif

### Exemplos práticos de autocomandos {#sub:Exemplo prático de autocomandos}

#### Detectando indentação fora do padrão

Há situações em que é necessária a uniformização de ações, por exemplo,
em códigos Python deve-se manter um padrão para a indentação, ou será
com espaços ou será com tabulações, não se pode misturar os dois pois o
interpretador retornaria um erro. Outra situação em que misturar espaços
com tabulações ocasiona erros é em códigos LaTeX, ao compilar o
documento a formatação não sai como desejado. Até que se perceba o erro
leva um tempo. Para configurar o vim de forma que ele detecte este tipo
de erro ao entrar no arquivo:

         au! VimEnter * match ErrorMsg /^\t\+/

         " explicação para o autocomando acima
         au! ............... automaticamente
         VimEnter .......... ao entrar no vim
         * ................. para qualquer tipo de arquivo
         match ErrorMsg .... destaque como erro
         / ................. inicio de um padrão
         ^ ................. começo de linha
         \t ................ tabulação
         \+ ................ uma vez ou mais
         / ................. fim do padrão de buscas

Para evitar que este erro se repita, ou seja, que sejam adicionados no
começo de linha espaços no lugar de tabulações adiciona-se ao \~/.vimrc

         set expandtab

É perfeitamente possível um autocomando que faça direto a substituição
de tabulações por espaços, mas neste caso não é recomendado que o
autocomando se aplique a todos os tipos de aquivos.

#### Inserindo automaticamente modelos de documento

Pode-se criar um autocomando para inserir um modelo de documento ‘html’
por exemplo de forma automática, ou seja, se você criar um novo
documento do tipo ‘html’ o vim colocará em seu conteúdo um modelo
pre-definido.

         au BufNewFile *.html 0r ~/.vim/skel/skel.html

Funções {#sec:Funções}
-------

### Fechamento automático de parênteses {#sec:Fechamento automático de parênteses}

         " --------------------------------------
         " Ativa fechamento automático para parêntese
         " Set automatic expansion of parenthesis/brackets
         inoremap ( ()<Esc>:call BC_AddChar(``)'')<cr>i
         inoremap { {}<Esc>:call BC_AddChar(``}'')<cr>i
         inoremap [ []<Esc>:call BC_AddChar(``]'')<cr>i
         `` '' ``''<Esc>:call BC_AddChar(``''")<cr>i
         "
         " mapeia Ctrl-j para pular fora de parênteses colchetes etc...
         inoremap <C-j> <Esc>:call search(BC_GetChar(), ``W'')<cr>a
         " Function for the above
         function! BC_AddChar(schar)
            if exists(``k'')
                let b:robstack = b:robstack . a:schar
            else
                let b:robstack = a:schar
            endif
         endfunction
         function! BC_GetChar()
            let l:char = b:robstack[strlen(b:robstack)-1]
            let b:robstack = strpart(b:robstack, 0, strlen(b:robstack)-1)
            return l:char
         endfunction
        
        '''Outra opção para fechamento de parênteses'''
        
         " Fechamento automático de parênteses
         imap { {}<left>
         imap ( ()<left>
         imap [ []<left>
        
         " pular fora dos parênteses, colchetes e chaves, mover o cursor
         " no modo de inserção
         imap <c-l> <Esc><right>a
         imap <c-h> <Esc><left>a

### Função para barra de status {#Função para barra de status}

         set statusline=%F%m%r%h%w\
            [FORMAT=%{&ff}]\
            [TYPE=%Y]\
            [ASCII=\%03.3b]\
            [HEX=\%02.2B]\
            [POS=%04l,%04v][%p%%]\ [LEN=%L]

Caso este código não funcione acesse [este
link](http://vim.wikia.com/wiki/Writing_a_valid_statusline) @StatusLine.

### Rolar outra janela {#Rolar outra janela}

Se você dividir janelas tipo

         Ctrl-w n

pode colocar esta função no seu `.vimrc`

         " rola janela alternativa
         fun! ScrollOtherWindow(dir)
         if a:dir == ``n''
            let move = ``>''
         elseif a:dir == ``p''
            let move = ``>''
         endif
         exec ``p'' . move . ``p''
         endfun
         nmap <silent> <M-Down> :call ScrollOtherWindow(``n'')<CR>
         nmap <silent> <M-Up> :call ScrollOtherWindow(``p'')<CR>

Esta função é acionada com o atalho <span>Alt-$\uparrow$</span> e
<span>Alt-$\downarrow$</span>.

### Função para numerar linhas {#Função para numerar linhas}

No site wikia há um código de função para [numerar
linhas](http://vim.wikia.com/wiki/Number_a_group_of_lines) @NumerarLinhas

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
link](http://nanasi.jp/old/colorscheme_0.html) @EsquemasDeCor.

### Uma função para inserir cabeçalho de script {#Uma função para inserir cabeçalho de script bash}

para chamar a função basta pressionar ‘`,sh`’ em modo normal

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

### Função para inserir cabeçalhos Python {#Função para inserir cabeçalhos Python}

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

### Função para pular para uma linha {#Função para pular para uma linha}

         "ir para linha
         " ir para uma linha específica
         function! GoToLine()
         let ln = inputdialog("ir para a linha...")
         exe ``:'' . ln
         endfunction
         "no meu caso o mapeamento é com Ctrl-l
         "use o que melhor lhe convier
         imap <S-l> <C-o>:call GoToLine()<CR>
         nmap <S-l> :call GoToLine()<CR>

### Função para gerar backup {#Função para gerar backup}

A função abaixo é útil para ser usada quando você vai editar um arquivo
gerando modificações significativas, assim você poderá restaurar o
backup se necessário

         " A mapping to make a backup of the current file.
         fun! WriteBackup()
            let fname = expand("%:p") . "__" . strftime("%d-%m-%Y--%H.%M.%S")
            silent exe ":w " . fname
            echo "Wrote " . fname
         endfun
         nnoremap <Leader>ba :call WriteBackup()<CR>

O atalho “<span>\<leader\></span>” em geral é a barra invertida
“$\backslash$”, na dúvida “<span>:help \<leader\></span>”.

Como adicionar o Python ao <span>*path*</span> do Vim? {#Como adicionar o Python ao path do Vim?}
------------------------------------------------------

Coloque o seguinte
[script](http://vim.wikia.com/wiki/Automatically_add_Python_paths_to_Vim_path) @PythonPath
em:

         * ~/.vim/after/ftplugin/python.vim    (on Unix systems)
         %* $HOME/vimfiles/after/ftplugin/python.vim    (on Windows systems)

         python << EOF
         import os
         import sys
         import vim
         for p in sys.path:
             # Add each directory in sys.path, if it exists.
             if os.path.isdir(p):
                 # Command `set' needs backslash before each space.
                 vim.command(r``s'' % (p.replace(`` '', r`` '')))
         EOF

Isto lhe permite usar ‘<span>gf</span>’ ou <span>Ctrl-w Ctrl-F</span>
para abrir um arquivo sob o cursor

Criando um menu {#Criando um menu}
---------------

Como no Vim podemos ter infinitos comandos fica complicado memorizar
tudo é aí que entram os menus, podemos colocar nossos plugins e atalhos
favoritos em um menu veja este exemplo

         amenu Ferramentas.ExibirNomeDoTema :echo g:colors_name<cr>

O comando acima diz:

         amenu ........................ cria um menu
         Ferramentas.ExibirNomeDoTema . Menu plugin submenu ExibirNomeDoTema
         :echo g:colors_name<cr> ...... exibe o nome do tema atual

Caso haja espaços no nome a definir você pode fazer assim

         amenu Ferramentas.Exibir\ nome\ do\ tema :echo g:colors_name<cr>

Criando menus para um modo específico {#Criando menus para um modo específico}
-------------------------------------

         :menu .... Normal, Visual e Operator-pending
         :nmenu ... Modo Normal
         :vmenu ... Modo Visual
         :omenu ... Operator-pending modo
         :menu! ... Insert e Comando
         :imenu ... Modo de inserção
         :cmenu ... Modo de comando
         :amenu ... Todos os modos

Exemplo de menu {#Exemplo de menu}
---------------

         " cores
         menu T&emas.cores.quagmire :colo quagmire<CR>
         menu T&emas.cores.inkpot :colo inkpot<CR>
         menu T&emas.cores.google :colo google<CR>
         menu T&emas.cores.ir_black :colo ir_black<CR>
         menu T&emas.cores.molokai :colo molokai<CR>
         " Fontes
         menu T&emas.fonte.Inconsolata :set gfn=Inconsolata:h10<CR>
         menu T&emas.fonte.Anonymous :set anti gfn=Anonymous:h8<CR>
         menu T&emas.fonte.Envy\ Code :set anti gfn=Envy_Code_R:h10<CR>
         menu T&emas.fonte.Monaco :set gfn=monaco:h9<CR>
         menu T&emas.fonte.Crisp :set anti gfn=Crisp:h12<CR>
         menu T&emas.fonte.Liberation\ Mono :set gfn=Liberation\ Mono:h10<CR>

O comando “<span>:update</span>” Atualiza o menu recém modificado.
Quando o comando “<span>:amenu</span>” É usado sem nenhum argumento o
Vim mostra os menus definidos atualmente. Para listar todas as opções de
menu para ‘`Plugin`’ por exemplo digita-se no modo de comandos
“<span>:amenu Plugin</span>”.

#### Ocultando as barras de ferramentas e menu

        :set guioptions-=m  ........ oculta menus
        :set guioptions-=T  ........ oculta icones

        obs: para exibir novamente repita o comando 
        substituindo o sinal de menos por mais.

Outros mapeamentos {#Outros mapeamentos}
------------------

Destaca espaços e tabulações redundantes:

         highlight RedundantWhitespace ctermbg=red guibg=red
         match RedundantWhitespace /\s\+$\| \+\ze\t/

Explicando com detalhes

         \s ..... espaço
         \+ ..... uma ou mais vezes
         $ ...... no final da linha
         \| ..... ou
         `` '' .. espaço (veja imagem acima)
         \+ ..... uma ou mais vezes
         \ze .... até o fim
         \t ..... tabulação

Portanto a expressão regular acima localizará espaços ou tabulações no
final de linha e destacará em vermelho.

         "Remove espaços redundantes no fim das linhas
         map <F7> <Esc>mz:%s/\s\+$//g<cr>`z

Um detalhe importante

         mz ... marca a posição atual do cursor para retornar no final do comando
         `z ... retorna à marca criada

Se não fosse feito isto o cursor iria ficar na linha da última
substituição!

         "Abre o vim explorer
         map <F6> <Esc>:vne .<cr><bar>:vertical resize -30<cr><bar>:set nonu<cr>

Podemos usar “Expressões Regulares[^2]” em buscas do Vim veja um exemplo
para retirar todas as tags HTML

         "mapeamento para retirar tags HTML com Ctrl-Alt-t
         nmap <C-M-t> :%s/<[^>]*>//g <cr>
         " Quebra a linha atual no local do cursor com F2
         nmap <F2> a<CR><Esc>
         " join lines  -- Junta as linhas com Shift-F2
         nmap <S-F2> A<Del><Space>

Para mais detalhes sobre buscas acesse o capítulo “[cha:Buscas e
substituições] na página ”.

Complementação com “tab” {#Complementação com ``tab''}
------------------------

         "Word completion
         "Complementação de palavras
         
         set dictionary+=/usr/dict/words
         set complete=.,w,k
         
         "------ complementação de palavras ----
         "usa o tab em modo de inserção para completar palavras
         
         function! InsertTabWrapper(direction)
            let col = col(``.'') - 1
            if !col || getline(``.'')[col - 1] !~ '\k'
               return ``>''
            elseif ``d'' == a:direction
               return ``>''
            else
               return ``>''
            endif
         endfunction
         
         inoremap <tab> <c-r>=InsertTabWrapper (``d'')<cr>
         inoremap <s-tab> <c-r>=InsertTabWrapper (``d'')<cr>

Abreviações {#Abreviações}
-----------

Abreviações habilitam auto-texto para o Vim. O seu funcionamento
consiste de três campos, o primeiro é o modo no qual a abreviação
funcionará, o segundo é a palavra que irá disparar a abreviação e o
terceiro campo é a abreviação propriamente dita. Para que em <span>*modo
de comando ‘:’*</span> a palavra ‘salvar’ funcione para salvar os
arquivos, adiciona-se a seguinte abreviação ao ‘<span>\~/.vimrc</span>’.

        cab salvar w<cr>
        "<cr> corresponde ao <Enter>

Abaixo abreviações para o modo de inserção:

         iab slas Sérgio Luiz Araújo Silva
         iab Linux GNU/Linux
         iab linux GNU/Linux

Evitando arquivos de backup no disco {#Evitando arquivos de backup no disco}
------------------------------------

Nota-se em algumas situações que existem alguns arquivos com o mesmo
nome dos arquivos que foram editados, porém com um til (\~) no final.
Esses arquivos são <span>*backups*</span> que o Vim gera antes de
sobrescrever os arquivos, e podem desde ocupar espaço significativo no
disco rígido até representar falha de segurança, como por exemplo
arquivos <span>.php\~</span> que não são interpretados pelo servidor web
e expõem o código-fonte.

Para que os <span>*backups*</span> sejam feitos enquanto os arquivos
estejam sendo escritos, porém não mantidos após terminar a escrita,
utiliza-se no `.vimrc`:

         set nobackup
         set writebackup

Fonte: [Site do Eustáquio
Rangel](http://eustaquiorangel.com/posts/520) @SiteEustaquioRangel01.

Mantendo apenas um Gvim aberto {#Mantenddo apenas um Gvim aberto}
------------------------------

Essa dica destina-se apenas à versão do Vim que roda no ambiente
gráfico, ou seja, o Gvim, pois ela faz uso de alguns recursos que só
funcionam nesse ambiente. A meta é criar um comando que vai abrir os
arquivos indicados em abas novas sempre na janela já existente.

Para isso deve-se definir um <span>*script*</span> que esteja no seu
<span>*path*</span>[^3] do sistema (e que possa ser executado de alguma
forma por programas do tipo <span>*launcher*</span> no modo gráfico) que
vai ser utilizado sempre que quisermos abrir nossos arquivos dessa
maneira. Para efeito do exemplo, o nome do arquivo será
<span>tvim</span> (de <span>*tabbed vim*</span>), porém pode ser nomeado
com o nome que for conveniente.

A única necessidade para essa dica funcionar é a versão do Vim ter
suporte para o argumento <span>–serverlist</span>, o que deve ser
garantido nas versões presentes na época em que esse documento foi
escrito. Para fazer uma simples verificação se o comando está
disponível, deve ser digitado em um terminal:

         vim --serverlist
         gvim --serverlist

Se ambos os comandos acima resultaram em erro, o procedimento não poderá
ser implementado. Do contrário, deve-se utilizar o comando que teve um
retorno válido (<span>vim</span> ou <span>gvim</span>) para criar o
<span>*script*</span>. Supondo que foi o comando <span>gvim</span> que
não retornou um erro, criamos o <span>*script*</span> da seguinte forma:

         #!/bin/bash
         if [ $# -ne 1 ]
         then
            echo "Sem arquivos para editar."
            exit
         fi
         gvim --servername $(gvim --serverlist | head -1) --remote-tab $1

Desse modo, se for digitado <span>tvim</span> sem qualquer argumento, é
exibida a mensagem de erro, do contrário, o arquivo é aberto na cópia
corrente do Gvim, em uma nova aba, por exemplo:

         tvim .vimrc

Fonte: [Site do Eustáquio
Rangel](http://eustaquiorangel.com/posts/477) @SiteEustaquioRangel02

Referências
-----------

\* <http://www.dicas-l.com.br/dicas-l/20050118.php>

[^1]: hls é uma abreviação de hightlight search

[^2]: <http://guia-er.sourceforge.net>

[^3]: Diretórios nos quais o sistema busca pelos comandos
