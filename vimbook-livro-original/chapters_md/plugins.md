Plugins {#Plugins}
=======

“<span>*Plugins*</span>”[^1] são um meio de estender as funcionalidades
do Vim, há “<span>*plugins*</span>” para diversas tarefas, desde wikis
para o Vim até ferramentas de auxílio a navegação em arquivos com é o
caso do “<span>*plugin*</span>”
[NerdTree](http://www.vim.org/scripts/script.php?script_id=1658) @PluginNerdTree,
que divide uma janela que permite navegar pelos diretórios do sistema a
fim de abrir arquivos a serem editados.

Como testar um plugin sem instalá-lo? {#Como testar um plugin sem instala-lo?}
-------------------------------------

         :source <path>/<plugin>

Caso o plugin atenda as necessidades, pode-se instalá-lo. Este
procedimento também funciona para temas de cor!

No GNU/Linux

         ~/.vim/plugin/

No Windows

         ~/vimfiles/plugin/

Obs: Caso ainda não exista o diretório, ele pode ser criado pelo próprio
usuário

Exemplo no GNU/Linux

         + /home/usuario/
                     |
                     |
                     + .vim
                       |
                       |
                       + plugin

Obs: Alguns plugins dependem da versão do Vim, para saber qual a que
está atualmente instalada:

         :ve[rsion]

Atualizando a documentação dos plugins {#sec:Atualizando a documentação dos plugins}
--------------------------------------

Caso seja adicionado algum arquivo de documentação em ‘`~/.vim/doc`’
pode-se gerar novamente as tags “links” para navegação de ajuda.

        :helptags $VIMRUNTIME/doc
        :helptags ~/.vim/doc

Plugin para LaTeX {#Plugin para LaTeX}
-----------------

Um plugin completo para LaTeXestá acessível
[aqui](http://vim-latex.sourceforge.net/) @PluginLatex. Uma vez
adicionado o plugin você pode inserir seus <span>*templates*</span> em:

         ~/.vim/ftplugin/latex-suite/templates

Criando <span>*folders*</span> para arquivos LaTeX {#Criando folders para arquivos LaTeX}
--------------------------------------------------

         set foldmarker=\\begin,\\end
         set foldmethod=marker

Adicionar marcadores (<span>*labels*</span>) às seções de um documento
LaTeX

         :.s/^\(\\section\)\({.*}\)/\1\2\r\\label\2
         
         : ........... comando
         / ........... inicia padrão de busca
         ^ ........... começo de linha
         \(palavra\) . agrupa um trecho
         \(\\section\) agrupa `\section'
         \\ .......... torna \ literal
         { ........... chave literal
         .* .......... qualquer caractere em qualquer quantidade
         } ........... chave literal
         / ........... finaliza parão de busca
         \1 .......... repeter o grupo 1 \(\\section\) 
         \2 .......... repete o grupo 2 \({.*\}\)
         \r .......... insere quebra de linha
         \\ .......... insere uma barra invertida
         \2 .......... repete o nome da seção

Criando seções LaTeX {#Criando seções latex}
--------------------

o comando abaixo substitui

         ==seção==

por

         \section{seção}

         :.s/^==\s\?\([^=]*\)\s\?==/\\section{\1}/g
         
         : ......... comando
         . ......... linha atual
         s ......... substitua
         ^ ......... começo de linha
         == ........ dois sinais de igual
         \s\? ...... seguido ou não de espaço
         [^=] ...... não pode haver = (^ dentro de [] é negação)
         * ......... diz que o que vem antes pode vir zero ou mais vezes
         \s\? ...... seguido ou não de espaço
         \\ ........ insere uma barra invertida
         \1 ........ repete o primeiro trecho entre ()

Plugin para manipular arquivos
------------------------------

Acesse o plugin neste
[link](http://www.vim.org/scripts/script.php?script_id=2337#0.1.9) @PluginParaArquivos01.
Para entender este plugin acesse um vídeo [neste
link](http://www.screencast.com/t/P6nJkJ0DE) @PluginParaArquivos02.

Complementação de códigos {#Complementação de códigos}
-------------------------

O “<span>*plugin*</span>” snippetsEmu é um misto entre complementação de
códigos e os chamados modelos ou <span>*templates*</span>. Insere um
trecho de código pronto, mas vai além disso, permitindo saltar para
trechos do modelo inserido através de um atalho configurável de modo a
agilizar o trabalho do programador. [Link para
baixar](http://www.vim.org/scripts/script.php?script_id=1318) @PluginSnippetsEmu.

### Instalação {#Instalação}

Um artigo ensinando como instalar o “<span>*plugin*</span>” snippetsEmu
pode ser lido [nesse artigo na
internet](http://vivaotux.blogspot.com/2008/03/instalando-o-plugin-snippetsemu-no-vim.html) @SilvasnipptsEmu.
Outro plugin muito interessante para complementação é o
“autocompletepopup” que complementa mostrando um popup durante a
digitação, o mesmo pode ser obtido [neste
link](http://www.vim.org/scripts/script.php?script_id=1879) @NishidaAutoCompletePopup,
em seguida coloca-se esta linha ao vimrc:

         let g:AutoComplPop_CompleteoptPreview = 1

A linha acima faz com que o vim abra uma janela pequena com a
documentação de cada método que está sendo digitado.

Um wiki para o Vim {#sec:Um wiki para o Vim}
------------------

O “<span>*plugin*</span>” wikipot implementa um wiki para o Vim no qual
você define um “link” com a notação WikiWord, onde um “link” é uma
palavra que começa com uma letra maiúscula e tem outra letra maiúscula
no meio Obtendo o plugin [neste
link](http://www.vim.org/scripts/script.php?script_id=1018) @PluginPotWiki.

Acessando documentação do Python no Vim {#Acessando documentação do Python no Vim}
---------------------------------------

Obtenha um plugin para esta tarefa em seu [site
oficial](http://www.vim.org/scripts/script.php?script_id=910) @PluginDocPython.

Formatando textos planos com syntax {#Formatando textos planos com syntax}
-----------------------------------

Um plugin que adiciona syntaxe colorida a textos planos pode ser obtido
[neste
link](http://www.vim.org/scripts/script.php?script_id=2208&rating=helpful#1.3) @PluginTextoPlano.
Veja como instalar o este plugin no capítulo [sec:Um wiki para o Vim].

Movimentando em <span>*camel case*</span> {#Movimentando em camel case}
-----------------------------------------

O <span>*plugin*</span>
[<span>CamelCaseMotion</span>](http://www.vim.org/scripts/script.php?script_id=1905) @PluginCamelCaseMotion
auxilia a navegação em palavras em [<span>*camel
case*</span>](http://en.wikipedia.org/wiki/Camel_case) @WikipediaCamelCase
ou separadas por sublinhados, através de mapeamentos similares aos que
fazem a movimentação normal entre strings, e é um recurso de grande
ajuda quando o editor é utilizado para programação.

Após instalado o plugin, os seguintes atalhos ficam disponíveis:

,w

:   Movimenta para a próxima posição <span>*camel*</span> dentro da
    string

,b

:   Movimenta para a posição <span>*camel*</span> anterior dentro da
    string

,e

:   Movimenta para o caractere anterior à próxima posição
    <span>*camel*</span> dentro da string

Fonte: [Blog do Eustáquio
Rangel](http://eustaquiorangel.com/posts/522) @SiteEustaquioRangel03

Aumentar a fonte {#sec:Aumentar a fonte}
----------------

[font size
plugin](http://www.vim.org/scripts/script.php?script_id=2809) @AumentarFonte

Plugin FuzzyFinder {#sec:Plugin FuzzyFinder}
------------------

Este plugin é a implementação de um recurso do editor Texmate[^2]. Sua
proposta é acessar de forma rápida:

1.  Arquivos `:FuzzyFinderFile`

2.  Arquivos recém editados `:FuzzyFinderMruFile`

3.  Comandos recém utilizados `:FuzzyFinderMruCmd`

4.  Favoritos `:FuzzyFinderAddBookmark, :FuzzyFinderBookmarks`

5.  Navegação por diretórios `:FuzzyFinderDir`

6.  Tags <span>:FuzzyFinderTag</span>

Para ver o plugin em ação acesse este [video](http://vimeo.com/2938498)
para obte-lo acesse [este
endereço](http://www.vim.org/scripts/script.php?script_id=1984), para
instalá-lo basta copiar para o diretório <span> /.vim/plugin</span>.

O plugin EasyGrep {#sec:O plugin EasyGrep}
-----------------

Usuários de sistemas <span>*Unix Like*</span>[^3], já conhecem o poder
do comando <span>grep</span>, usando este comando procuramos palavras
dentro de arquivos, este plugin simplifica esta tarefa, além de permitir
a utilização da versão do <span>grep</span> nativa do Vim
<span>vimgrep</span>, assim usuários do Windows também podem usar este
recurso. Um comando <span>grep</span> funciona mais ou menos assim:

         grep [opções] "padrão" /caminho

Mas no caso do plugin <span>*EasyGrep*</span> fica assim:

         :Grep foo  ........ procura pela palavra 'foo'
         :GrepOptions ...... exibe as opções de uso do plugin

O plugin pode ser obtido no seguinte
[endereço](http://www.vim.org/scripts/script.php?script_id=2438#0.9), já
sua instalação é simples, basta copiar o arquivo obtido no link acima
para a pasta:

         ~/.vim/plugin .......... no caso do linux
         ~/vimfiles/plugin ...... no caso do windows

Um vídeo de exemplo (na verdade uma animação gif) pode ser visto
[aqui](http://downloads.veryspeedy.net/vim/EasyGrep.gif).

O plugin <span>*SearchComplete*</span>
--------------------------------------

Para que o vim complete opções de busca “com a tecla \<tab\>”, digita-se
uma palavra parcialmente e o plugin atua, exibindo palavras que tem o
mesmo início, por exemplo:

         /merca<tab>
         /mercado
         /mercantil
         /mercadológico

Cada vez que se pressiona a tecla <span>\<tab\></span> o cursor saltará
para a próxima ocorrência daquele fragmento de palavra. Pode-se obter o
plugin <span>*SearchComplete*</span> no seguinte
[endereço](http://www.vim.org/scripts/script.php?script_id=474), e para
instalá-lo basta copiá-lo para a pasta apropriada:

         ~/vimfiles/plugin .......... no windows
         ~/.vim/plugin .............. no Gnu/Linux

Há outro plugin similar chamado <span>CmdlineComplete</span> disponível
[neste link](http://www.vim.org/scripts/script.php?script_id=2222).

O plugin <span>*AutoComplete*</span> {#sec:O Plugin AutoComplete}
------------------------------------

Este plugin trabalha exibindo sugestões no modo de inserção, à medida
que o usuário digita aparece um <span>*popup*</span> com sugestões para
possíveis complementos, bastando pressionar <span>\<Enter\></span> para
aceitar as sugestões. Neste
[link](http://www.vim.org/scripts/script.php?script_id=1879), você pode
fazer o <span>*download*</span> do plugin.

O plugin <span>*Ctags*</span> {#sec:O Plugin Ctags}
-----------------------------

<span>*Ctags*</span> em si é um programa externo que indexa arquivos de
código fonte. Ele lê o código fonte em busca de identificadores,
declarações de função, variáveis, e constrói seu índex de referências
cruzadas. Mas vamos ao plugin, mesmo por que não estamos no CtagsBook.

Primeiro precisamos ter o arquivos de tags. Para tal, usamos o comando:

        ctags -R <arquivos>

Normalmente o parâmetro \<arquivos\> pode ser uma expressão regular do
tipo \*.[ch] e afins. Depois de obter o arquivo de tags, você já pode
sair usando os atalhos do plugin para navegar pelo código fonte. Com o
cursor em cima de um identificador, usando o atalho ‘`ctrl+]`’ o cursor
pula diretamente para a sua declaração. O atalho ‘`ctrl+o`’ volta o
cursor para a posição inicial.

Quando navegando por um código fonte muito extenso com vários
diretórios, é mapear o caminho dos arquivos usando o caminho absoluto
deles no seu diretório de trabalho deste jeito:

         find $(pwd) -regex ".*py$" | xargs ctags

Assim você pode copiar o arquivo de tags para todos os diretórios e
mesmo assim conseguir usar os atalhos do plugin para navegar no código
fonte.

Pode-se obter o programa <span>*Ctags*</span> neste
[link](http://ctags.sourceforge.net/). O plugin de <span>*Ctags*</span>
para o Vim está neste
[link](http://vim.sourceforge.net/scripts/script.php?script_id=12)”, e
para instalá-lo basta copiá-lo para a pasta apropriada:

         ~/vimfiles/plugin .......... no windows
         ~/.vim/plugin .............. no Gnu/Linux

O Plugin <span>*Project*</span>
-------------------------------

O plugin project acessível através deste
[link](http://www.vim.org/scripts/script.php?script_id=69) cria toda uma
estrutura de gerenciamento de projetos, para programadores é uma
funcionalidade extremamente necessária, costuma-se trabalhar com vários
arquivos da mesma família “extensão”, e ao clicar em um dos arquivos do
projeto o mesmo é aberto instantaneamente.

         :Project ......... abre uma janela lateral para o projeto
         \C ............... inicia a criação de um projeto (recursivamente)
         \c ............... inicia a criação de um projeto na pasta local

Após digitar o atalho de criação do projeto aparecerá uma janela para
designar um nome para o mesmo, em seguida digita-se o caminho para o
diretório do projeto, após isto digita-se ‘.’ (ponto) como parâmetro,
cria-se um filtro como ‘<span>.py</span>’. Para criar uma entrada
(acesso ao plugin) no menu do Gvim colocamos a seguinte linha no
‘<span>vimrc</span>’.

         amenu &Projetos.togle <Plug>ToggleProject<cr>

Pode-se definir um projeto manualmente assim:

         nome=~/docs/ CD=. filter="*.txt" {

         }

Ao recarregar o Vim pode-se abrir o <span>*Plugin*</span>
“<span>:Projetc</span>” e pressionar o atalho ‘`\r`’ para que o mesmo
gere um índice dos arquivos contidos no caminho indicado.

O plugin pydiction {#sec:O plugin pydiction}
------------------

Um que completa códigos python assim:

        import sys
        sys.<tab>

O plugin contém dois arquivos:

1.  <span>pydiction.py</span> deve ser colocado no <span>path</span>

2.  <span>pydiction</span> deve ser colocado em um lugar de sua
    preferência

Deve-se adicionar algumas linhas do <span>.vimrc</span>. No exemplo
abaixo o dicionário é adicionado ao diretório <span> /.vim/dict</span>

    if has("autocmd")
        autocmd FileType python set complete+=k/.vim/dict/pydiction isk+=.,(
    endif " has("autocmd") 

Pode-se obter o plugin [neste
link](http://www.vim.org/scripts/script.php?script_id=850).

O plugin FindMate {#sec:O plugin FindMate}
-----------------

Um plugin que agiliza a busca por arquivos na pasta pessoal, disponível
neste [link](http://snipt.net/voyeg3r/findmate-plugin-for-vim/). Basta
coloca-lo na pasta “<span>/home/usuario/.vim/plugins/</span>” e digitar
duas vezes vírgula e ele substituirá para:

        :FindMate 

Digita-se então uma palavra e \<Enter\> para se obter a lista de
arquivos que correspondem ao padrão.

Atualizando a documentação dos plugins {#sec:Atualizando a documentacao dos plugins}
--------------------------------------

Caso seja adicionado algum arquivo de documentação em em ‘`~/.vim/doc`’
pode-se gerar novamente as tags “links” para navegação de ajuda.

       :helptags ~/.vim/doc

[^1]: Plugins são recursos que se adicionam aos programas

[^2]: Editor de textos da Apple com muitos recursos

[^3]: Sistemas da família Unix tipo o GNU/Linux
