Buscas e Substituições {#cha:Buscas e substituições}
======================

Para fazer uma busca, certifique-se de que está em modo normal,
pressione “/” e digite a expressão a ser procurada.\

Para encontrar a primeira ocorrência de “foo” no texto:

         /foo

Para repetir a busca basta pressionar a tecla “`n`” e para repetir a
busca em sentido oposto “`N`”.

         /teste/+3

Posiciona o cursor três linhas após a ocorrência da palavra “teste”\

         /\<casa\>

A busca acima localiza ‘<span>casa</span>’ mas não
‘<span>casamento</span>’. Em expressões regulares, `\<` e `\>` são
representadas por `\b`, que representa, por sua vez, borda de palavras.
Ou seja, \`<span>casa,</span>\`, \`<span>casa!</span>\` seriam
localizado, visto que sinais de pontuação não fazem parte da palavra.

Usando “Expressões Regulares” em buscas {#Usando ``Expressões Regulares'' em buscas}
---------------------------------------

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

### Evitando escapes ao usar Expressões regulares

O Vim possui um modo chamado “<span>*very magic*</span>” para uso em
expressões regulares que evita o uso excessivo de escapes, alternativas
etc. Usando apenas uma opção: veja “`:h /\v`”.

Em um trecho com dígitos + texto + dígitos no qual se deseja manter só
as letras.

         12345aaa678
         12345bbb678
         12345aac678

Sem a opção “<span>*very magic*</span>” faríamos:

         :%s/\d\{5\}\(\D\+\)\d\{3\}/\1/

Já com a opção “<span>*very magic*</span>” “`\v`” usa-se bem menos
escapes:

         :%s/\v\d{5}(\D+)\d{3}/\1/

         " explicação do comando acima
         : ......... comando
         % ......... em todo arquivo
         s ......... substitua
         / ......... inicia padrão de busca
         \v ........ use very magic mode
         \d ........ dígitos
         {5} ....... 5 vezes 
         ( ........ inicia um grupo
         \D ........ seguido de não dígitos
         )  ........ fecha um grupo     
         + ......... uma ou mais vezes
         \d ........ novamente dígitos
         {3} ....... três vezes 
         / ......... inicio da substituição
         \1 ........ referencia o grupo 1

Analisando o exemplo anterior, a linha de raciocínio foi a de “manter o
texto entre os dígitos”, o que pode ser traduzido, em uma outra forma de
raciocínio, como “remover os dígitos”.

         :%s/\d//g

         " explicação do comando acima
         % ......... em todo arquivo
         s ......... substitua
         / ......... inicia padrão de busca
         \d ........ ao encontrar um dígito
         / ......... subtituir por
         vazio ..... exato, substituir por vazio
         /g ........ a expressão se torna gulosa

Por guloso - `/g` - se entende que ele pode e deve tentar achar mais de
uma ocorrência do padrão de busca na mesma linha. Caso não seja gulosa,
a expressão irá apenas casar com a primeira ocorrência em cada linha.

#### Classes <span>*POSIX*</span> para uso em Expressões Regulares

Ao fazermos substituições em textos poderemos nos deparar com erros,
pois [a-z] não inclui caracteres acentuados, as classes
<span>*POSIX*</span> são a solução para este problema, pois adequam o
sistema ao idioma local, esta é a mágica implementada por estas classes.

         [:lower:] ...... letras minúsculas incluindo acentos
         [:upper:] ...... letras maiúsculas incluindo acentos
         [:punct:] ...... ponto, virgula, colchete, etc

Para usar estas classes fazemos:

         :%s/[[:lower:]]/\U&/g

         Explicando o comando acima:
         : ....... modo de comando
         % ....... em todo o arquivo atual
         s ....... substitua
         / ....... inicia o padrão a ser buscado
         [ ....... inicia um grupo
         [: ...... inicia uma classe POSIX
         lower ... letras minúsculas
         :] ...... termina a classe POSIX
         ] ....... termina o grupo
         / ....... inicia substituição
         \U ...... para maiúsculo
         & ....... correponde ao que foi buscado

Nem todas as classes <span>*POSIX*</span> conseguem pegar caracteres
acentuados, portanto deve-se habilitar o destaque colorido para buscas
usando:

         :set hlsearch .... destaque colorido para buscas
         :set incsearch ... busca incremental

Dessa forma podemos testar nossas buscas antes de fazer uma
substituição.

Para aprender mais sobre Expressões Regulares leia:

-   [Guia sobre Espressões
    Regulares](http://guia-er.sourceforge.net) @JargasRegex

-   <span>:help regex</span>

-   <span>:help pattern</span>

Uma forma rápida para encontrar a próxima ocorrência de uma palavra sob
o cursor é teclar ‘`*`’. Para encontrar uma ocorrência anterior da
palavra sob o cursor, existe o `#` (em ambos os casos o cursor deve
estar posicionado sobre a palavra que deseja procurar). As duas opções
citadas localizam apenas se a palavra corresponder totalmente ao padrão
sob o cursor, pode-se bucar por trechos de palavras que façam parte de
palavras maiores usando-se ‘`g*`’. Pode-se ainda exibir “dentro do
contexto” todas as ocorrências de uma palavra sob o cursor usando-se o
seguinte atalho em modo normal:

         [ Shift-i

Destacando padrões {#sec:Destacando padrões}
------------------

Você pode destacar linhas com mais de 30 caracteres assim:

         :match ErrorMsg /\%>30v/ . destaca linhas maiores que 30 caracteres
         :match none .............. remove o destaque

Inserindo linha antes e depois
------------------------------

Suponha que se queira um comando, considere “`,t`”, que faça com que a
linha indentada corrente passe a ter uma linha em branco antes e depois;
isto pode ser obtido pelo seguinte mapeamento:

         :map ,t <Esc>:.s/^\(\s\+\)\(.*\)/\r\1\2\r/g<cr>

Explicando:

         : ................ entra no modo de comando
         map ,t ........... mapeia ,t para a função desejada
         <Esc> ............ ao executar sai do modo de inserção
         s/isto/aquilo/g .. substitui isto por aquilo
         : ................ inicia o modo de comando
         . ................ na linha corrente
         s ................ substitua
         ^ ................ começo de linha
         \s\+ ............. um espaço ou mais (barras são escapes)
         .* ............... qualquer coisa depois
         \(grupo\) ........ agrupo para referenciar com \1
         \1 ............... repete na substituição o grupo 1
         \r ............... insere uma quebra de linha
         g ................ em todas as ocorrências da linha
         <cr> ............. Enter

Obtendo informações do arquivo
------------------------------

         ga ............. mostra o código do caractere em decimal hexa e octal
         ^g ............. mostra o caminho e o nome do arquivo
         g^g ............ mostra estatísticas detalhadas do arquivo

Obs: O código do caractere pode ser usado para substituições,
especialmente em se tratando de caracteres de controle como tabulações
“`^I`” ou final de linha DOS/Windows “`\%x0d`”. Você pode apagar os
caracteres de final de linha Dos/Windows usando uma simples
substituição, veja mais adiante:

         :%s/\%x0d//g

Uma forma mais prática de substituir o terminador de linha DOS para o
terminador de linha Unix:

        :set ff=unix
        :w

Na seção [cha:Como editar preferências no Vim] página  há um código para
a barra de status que faz com que a mesma exiba o código do caractere
sob o cursor na seção [Função para barra de status]. O caractere de
final de linha do Windows/DOS pode ser inserido com a seguinte
combinação de teclas:

         i ............ entra em modo de inserção
         <INSERT> ..... entra em modo de inserção
         Ctrl-v Ctrl-m  insere o simbolo ^M (terminador de linha DOS)

Trabalhando com registradores {#Trabalhando com registradores}
-----------------------------

Pode-se guardar trechos do que foi copiado ou apagado para registros
distintos (área de transferência múltipla). Os registros são indicados
por aspas seguido por uma letra. Exemplos: <span>"a</span>,
<span>"b</span>, <span>"c</span>, etc.

Como copiar o texto para um registrador? É simples: basta especificar o
nome do registrador antes:

         "add ... apaga linha para o registrador a
         "bdd ... apaga linha para o registrador b
         "ap .... cola" o conteúdo do registrador a
         "bp .... cola" o conteúdo do registrador b
         "x3dd .. apaga 3 linhas para o registrador ``x''
         "ayy  .. copia linha para o registrador `a'
         "a3yy .. copia 3 linhas para o registrador `a'
         "ayw  .. copia uma palavra para o registrador `a'
         "a3yw .. copia 3 palavras para o registrador `a'

No “modo de inserção”, como visto anteriormente, pode-se usar um atalho
para colar rapidamente o conteúdo de um registrador.

         Ctrl-r (registro)

Para colar o conteúdo do registrador ‘<span>a</span>’

         Ctrl-r a

Para copiar a linha atual para a área de transferência

         "+yy

Para colar da área de transferência

         "+p

Para copiar o arquivo atual para a área de transferência
“<span>*clipboard*</span>”:

         :%y+

Edições complexas  {#Edições complexas }
------------------

Trocando palavras de lugar: Posiciona-se o cursor no espaço antes da 1ª
palavra e digita-se:

         deep

Trocando letras de lugar:

         xp .... com a letra seguinte
         xh[p .. com a letra anterior

Trocando linhas de lugar:

         ddp ... com a linha de baixo
         ddkP .. com a linha de cima

Tornando todo o texto maiúsculo

         gggUG
         ggVGU

Indentando 
-----------

         >> ..... Indenta a linha atual
         ^t ..... Indenta a linha atual em modo de inserção
         ^d ..... Remove indentação em modo de inserção
         >ip .... indenta o parágrafo atual

Corrigindo a indentação de códigos {#Corrigindo a indentação de códigos}
----------------------------------

Selecione o bloco de código, por exemplo

         vip  ..... visual ``inner paragraph'' (selecione este parágrafo)
         =  ....... corrige a indentação do bloco de texto selecionado
         ggVG= .... corrige a identação do arquivo inteiro

Usando o File Explorer {#Usando o file explorer}
----------------------

O Vim navega na árvore de diretórios com o comando

         vim .

Use o ‘<span>j</span>’ para descer e o ‘<span>k</span>’ para subir ou
<span>Enter</span> para editar o arquivo selecionado. Pressionando
<span>F1</span> ao abrir o FileExplorer do Vim, você encontra dicas
adicionais sobre este modo de operação do Vim.

Selecionando ou deletando conteúdo de tags HTML {#Selecionando ou deletando conteúdo de tags html}
-----------------------------------------------

         <tag> conteúdo da tag </tag>
         basta usar (em modo normal) as teclas
         vit ............... visual `inner tag | esta tag'

Este recurso também funciona com parênteses

         vi( ..... visual select
         vi" ..... visual select
         di( ..... delete inner (, ou seja, seu conteúdo

Substituições  {#Substituições }
--------------

Para fazer uma busca, certifique-se de que está em modo normal, em
seguida digite use o comando ‘<span>s</span>’, conforme será explicado.

Para substituir “foo” por “bar” na linha atual:

         :s/foo/bar

Para substituir “foo” por “bar” da primeira à décima linha do arquivo:

         :1,10 s/foo/bar

Para substituir “foo” por “bar” da primeira à última linha do arquivo:

         :1,$ s/foo/bar

Ou simplesmente:

         :% s/foo/bar

         $ ... significa para o Vim final do arquivo
         % ... representa o arquivo atual

O comando ‘<span>s</span>’ possui muitas opções que modificam seu
comportamento.

Exemplos  {#Exemplos }
---------

Busca usando alternativas:

         /end\(if\|while\|for\)

Buscará ‘<span>if</span>’, ‘<span>while</span>’ e ‘<span>for</span>’.
Observe que é necessário ‘escapar’ os caracteres `\(`, `\`| e `\)`, caso
contrário eles serão interpretados como caracteres comuns.

Quebra de linha

         /quebra\nde linha

Ignorando maiúsculas e minúsculas

         /\cpalavra

Usando `\c` o Vim encontrará “<span>*<span>palavra</span>*</span>”,
“<span>*<span>Palavraa</span>*</span>” ou até mesmo
“<span>*<span>PALAVRA</span>*</span>”. Uma dica é colocar no seu arquivo
de configuração “vimrc” veja o capítulo [cha:Como editar preferências no
Vim] na página .

         set ignorecase .. ignora maiúsculas e minúsculas na bucsca
         set smartcase ... se busca contiver maiúsculas ele passa a 
                           considerá-las
         set hlsearch .... mostra o que está sendo buscado em cores
         set incsearch ... ativa a busca incremental

se você não sabe ainda como colocar estas preferências no arquivo de
configuração pode ativa-las em modo de comando precedendo-as com dois
pontos, assim:

         :set ignorecase<Enter>

Substituições com confirmação:

         :%s/word/palavra/c ..... o `c' no final habilita a confirmação

Procurando palavras repetidas

         /\<\(\w*\) \1\>

Multilinha

         /Hello\_s\+World

Buscará ‘World’, separado por qualquer número de espaços, incluindo
quebras de linha. Buscará as três sequências:

         Hello World

         Hello    World

         Hello
         World

Buscar linhas de até 30 caracteres de comprimento

         /^.\{,30\}$

         ^  ..... representa começo de linha
         .  ..... representa qualquer caractere

         :%s/<[^>]*>//g ... apaga tags HTML/XML
         :%g/^$/d ......... apaga linhas vazias
         :%s/^[\ \t]*\n//g  apaga linhas vazias

Remover duas ou mais linhas vazias entre parágrafos diminuindo para uma
só linha vazia.

         :%s/\(^\n\{2,}\)/\r/g

Você pode criar um mapeamento e colocar no seu <span> /.vimrc</span>

         map ,s <Esc>:%s/\(^\n\{2,}\)/\r/g<cr>

No exemplo acima, ‘<span>,s</span>’ é um mapeamento para reduzir linhas
em branco sucessivas para uma só\

Remove não dígitos (não pega números)

         :%s/^\D.*//g

Remove final de linha DOS/Windows `^M` que tem código hexadecimal igual
a ‘<span>0d</span>’

         :%s/\%x0d//g

Troca palavras de lugar usando expressões regulares:

         :%s/\(.\+\)\s\(.\+\)/\2 \1/

Modificando todas as tags HTML para minúsculo:

         :%s/<\([^>]*\)>/<\L\1>/g

Move linhas 10 a 12 para além da linha 30:

         :10,12m30

O comando global “g” {#sec:O comando global ``g''}
--------------------

Buscando um padrão e gravando em outro arquivo:

         :'a,'b g/^Error/ . w >> errors.txt

Apenas imprimir linhas que contém determinada palavra, isto é útil
quando você quer ter uma visão sobre um determina aspecto do seu arquivo
vejamos:

         :set nu ..... habilita numeração
         :g/Error/p .. apenas mostra as linhas correspondentes

Para mostrar o as linhas correspondentes a um padrão, mesmo que a
numeração de linha não esteja habilitada use
“<span>:g/padrão/\#</span>”.

numerar linhas:

         :let i=1 | g/^/s//\=i."\t"/ | let i=i+1

Outro modo de inserir números de linha

        :%s/^/\=line('.').'  '

        : ............ comando
        % ............ em todo o arquivo
        s ............ substituição
        / ............ inicio da busca
        ^ ............ começo de linha
        / ............ inicio da substituição
        \=line('.') .. corresponde ao nº da linha atual
        .'  ' ........ concatena um espaço após o nº

Para copiar linhas começadas com <span>*Error*</span> para o final do
arquivo faça:

         :g/^Error/ copy $

Obs: O comando ‘<span>copy</span>’ pode ser abreviado ‘<span>co</span>’
ou ainda pode-se usar ‘<span>t</span>’ para mais detalhes:

         :h co

Como adicionar um padrão copiado com ‘<span>yy</span>’ após um
determinado padrão?

        :g/padrao/+put!
        :g/padrao/.put='teste'

Entre as linhas que contiverem ‘<span>fred</span>’ e ‘<span>joe</span>’
substitua:

         :g/fred/,/joe/s/isto/aquilo/gic

As opções ‘gic’ correspondem a <span>*global*</span>, <span>*ignore
case*</span> e <span>*confirm*</span>, podendo ser omitidas deixando só
o <span>*global*</span>.\

Pegar caracteres numéricos e jogar no final do arquivo:

         :g/^\d\+.*/m $

Inverter a ordem das linhas do arquivo:

         :g/^/m0

Apagar as linhas que contém <span>Line commented</span>:

         :g/Line commented/d

Apagar todas as linhas comentadas

          :g/^\s*#/d

Copiar determinado padrão para um registro:

         :g/pattern/ normal "Ayy

Copiar linhas que contém um padrão e a linha subsequente para o final:

         :g/padrão/;+1 copy $

Deletar linhas que não contenham um padrão:

         :v/dicas/d  ..... deleta linhas que não contenham `dicas'

Incrementar números no começo da linha:

         :.,20g/^\d/exe "normal! \<c-a>"

Sublinhar linhas começadas com <span>*Chapter*</span>:

         :g/^Chapter/t.|s/./-/g

         : ........ comando
         g ........ global
         / ........ inicio de um padrão
         ^ ........ começo de linha
         Chapter .. palavra literal
         / ........ fim do parão
         t ........ copia
         . ........ linha atual
         s ........ substitua
         / ........ inicio de um padrão
         . ........ qualquer caractere
         / ........ início da substituição
         - ........ por traço
         / ........ fim da substituição
         g ........ em todas as ocorrências

Dicas 
------

Para colocar a última busca em uma substituição faça:

         :%s/Ctrl-r//novo/g

A dupla barra corresponde ao ultimo padrão procurado, e portanto o
comando abaixo fará a substituição da ultima busca por casinha:

         :%s//casinha/g

Filtrando arquivos com o vimgrep {#Filtrando arquivos com o vimgrep}
--------------------------------

Por vezes sabemos que aquela anotação foi feita, mas no momento
esquecemos em qual arquivo está, no exemplo abaixo procuramos a palavra
dicas à partir da nossa pasta pessoal pela palavra ‘dicas’ em todos os
arquivos com extensão ‘<span>txt</span>’.

         ~/ ............ equivale a /home/user
         :lvimgrep /dicas/gj ~/**/*.txt | ls
         :vimgrep /dicas/gj **/*.txt | copen
         :vimgrep dicas **/*.txt | copen
         :h lvim ....... ajuda sobre o comando

Copiar a partir de um ponto
---------------------------

         :19;+3 co $

O Vim sempre necessita de um intervalo (inicial e final) mas se usar-mos
‘;’ ele considera a primeira linha como segundo ponto do intervalo, e no
caso acima estamos dizendo (nas entrelinhas) linhas 19 e 19+3\

De forma análoga pode-se usar como referência um padrão qualquer:

         :/palavra/;+10 m 0

O comando acima diz: à partir da linha que contém “palavra” incluindo as
10 próximas linhas mova ‘<span>m</span>’ para a primeira linha ‘0’, ou
seja, antes da linha 1.

Dicas das lista vi-br
---------------------

Fonte: [Grupo vi-br do
yahoo](http://groups.yahoo.com/group/vi-br/message/853) @ViBr01

Problema: Essa deve ser uma pergunta comum. Suponha o seguinte conteúdo
de arquivo:

         ... // várias linhas
         texto1000texto    // linha i
         texto1000texto    // linha i+1
         texto1000texto    // linha i+2
         texto1000texto    // linha i+3
         texto1000texto    // linha i+4
         ... // várias linhas

Gostaria de um comando que mudasse para

         ... // várias linhas
         texto1001texto    // linha i
         texto1002texto    // linha i+1
         texto1003texto    // linha i+2
         texto1004texto    // linha i+3
         texto1005texto    // linha i+4
         ... // várias linhas

Ou seja, somasse 1 a cada um dos números entre os textos especificando
como range as linhas i,i+4

         :10,20! awk 'BEGIN{i=1}{if (match($0, ``+'')) print ``o''
         (substr($0, RSTART, RLENGTH) + i++) ``o'``}''

Mas muitos sistemas não tem <span>awk</span>, e logo a melhor solução
mesmo é usar o Vim:

         :let i=1 | 10,20 g/texto\d\+texto/s/\d\+/\=submatch(0)+i/ | let i=i+1

Observação: 10,20 é o intervalo, ou seja, da linha 10 até a linha 20

         :help /
         :help :s
         :help pattern

O plugin
[Visincr](http://vim.sourceforge.net/scripts/script.php?script_id=670) @Visincr
Possibilita incrementos em modo visual de diversas formas, um vídeo
demonstrativos pode ser visto neste link: <http://vimeo.com/4457161>

Junção de linhas com Vim {#sec:Junção de linhas com Vim}
------------------------

Fonte: [dicas-l da
unicamp](http://www.dicas-l.com.br/dicas-l/20081228.php) @dicas-lJuncaoDeLinhas\
Colaboração: Rubens Queiroz de Almeida

Recentemente precisei combinar, em um arquivo, duas linhas consecutivas.
O arquivo original continha linhas como:

         Matrícula: 123456
         Senha: yatVind7kned
         Matrícula: 123456
         Senha: invanBabnit3

E assim por diante. Eu precisava converter este arquivo para algo como:

         Matrícula: 123456 - Senha: yatVind7kned
         Matrícula: 123456 - Senha: invanBabnit3

Para isto, basta executar o comando:

         :g/^Matrícula/s/\n/ - /

Explicando:

         s/isto/aquilo/g .. substitui isto por aquilo
         g ................ comando global
         /................. inicia padrão de busca
         ^ ................ indica começo de linha
         Matrícula ........ palavra a ser buscada
         s ................ inicia substituição
         /\n/ - / ......... troca quebra de linha `\n', por `-'

Buscando em um intervalo de linhas
----------------------------------

[sec:Buscando em um intervalo de linhas] Para buscar entre as linhas 10
e 50 por um padrão qualquer fazemos:

        /padrao\%>10l\$<50l

Esta e outras boas dicas podem ser lidas no site
[vim-faq](http://vimdoc.sourceforge.net/htmldoc/vimfaq.html) @VimFaq.
