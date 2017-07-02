Registros {#Registros}
=========

O Vim possui nove tipos de registros, cada tipo tem uma utilidade
específica, por exemplo você pode usar um registro que guarda o último
comando digitado, pode ainda imprimir dentro do texto o nome do próprio
arquivo, armazenar porções distintas de texto (área de transferência
múltipla) etc. Vamos aos detalhes.

-   O registro sem nome “”

-   10 registros nomeados de “9”

-   O registro de pequenas deleções "-

-   26 registros nomeados de “z” ou de “Z”

-   4 registros somente leitura

-   O registro de expressões "=

-   Os registro de seleção e “\*, ”+ and " 

-   O registro “o”

-   Registro do último padrão de busca "/

O registro sem nome “” {#O registro sem nome ``''}
----------------------

Armazena o conteúdo de ações como:

         d ....... deleção
         s ....... substituição
         c ....... modificação `change'
         x ....... apaga um caractere
         yy ...... copia uma linha inteira

Para acessar o conteúdo deste registro basta usar as letras
“<span>p</span>” ou “<span>P</span>” que na verdade são comandos para
colar abaixo da linha atual e acima da linha atual (em modo normal).

Registros nomeados de 0 a 9 {#Registros nomeados de 0 a 9}
---------------------------

O registro zero armazena o conteúdo da última cópia ‘<span>yy</span>’, à
partir do registro 1 vão sendo armazenadas as deleções sucessivas de
modo que a mais recente deleção será armazenada no registro 1 e os
registros vão sendo incrementados em direção ao nono. Deleção menores
que uma linha não são armazenadas nestes registros, caso em que o Vim
usa o registro de pequenas deleções ou que se tenha especificado algum
outro registro.

Registro de pequenas deleções "- {#Registro de pequenas deleções "-}
--------------------------------

Quando se <span>*deleta*</span> algo menor que uma linha o Vim armazena
os dados deletados neste registro.

Registros nomeados de “a até z” ou “A até Z” {#Registros nomeados de ``a até z'' ou ``A até Z''}
--------------------------------------------

Pode-se armazenar uma linha em modo normal assim:

         "ayy

Desse modo o Vim guarda o conteúdo da linha no registro ‘<span>a</span>’
caso queira armazenar mais uma linha no registro ‘<span>a</span>’ use
este comando:

         "Add

Neste caso a linha corrente é apagada ‘<span>dd</span>’ e adicionada ao
final do registro “a”.

         "ayip .. copia o parágrafo atual para o registro ``a''
         "a ..... registro a
         y ...... yank (copia)
         ip ..... inner paragraph (este parágrafo)

Registros somente leitura “: . % \#” {#Registros somente leitura}
------------------------------------

         ": ..... armazena o último comando
         ". ..... armazena uma cópia do último texto inserido
         "% ..... contém o nome do arquivo corrente
         "# ..... contém o nome do arquivo alternativo

Uma forma prática de usar registros em modo de inserção é usando:
`Ctrl-r`

         Ctrl-r % .... insere o nome do arquivo atual
         Ctrl-r : .... insere o último comando digitado
         Ctrl-r / .... insere a última busca efetuada
         Ctrl-r a .... insere o registro `a'

Em modo de inserção pode-se repetir a última inserção de texto
simplesmente pressionando:

         Ctrl-a

Registro de expressões "= {#sec:Registro de expressões "=}
-------------------------

         "=

O registro de expressões permite efetuar cálculos diretamente no editor,
usando o atalho “<span>Ctrl-r =</span>” <span>*no modo de
inserção*</span>, o editor mostrará um sinal de igualdade na barra de
status e o usuário digita então uma expressão matemática como uma
multiplicação “<span>6\*9</span>” e em seguida pressiona
<span>Enter</span> para que o editor finalize a operação. Veja um vídeo
demonstrando sua utilização [neste
link](http://vimeo.com/2967392) @RegistroDeExpressoes.

Para entender melhor como funciona o registro de expressões tomemos um
exemplo. Para fazer uma sequência como abaixo:

         linha 1 tem o valor 150,
         linha 2 tem o valor 300,
         linha 3 tem o valor 450,
         ...

Acompanhe os passos para a criação de uma macro permite fazer uma
sequência de quantas linhas forem necessárias com o incremento proposto
acima.

         <Esc>  ......... sai do modo de inserção
         qa ............. inicia a macro
         yy ............. copia a primeira linha
         p .............. cola a linha copiada
         w .............. pula para o número `1'
         <Ctrl-a> ....... incrementa o número (agora 2)
         4w ............. avança 4 palavras até 150
         "ndw ........... apaga o `150' para o registro "n
         a .............. entra em modo de inserção
         Ctrl-r = ....... abre o registro de expressões
         Ctrl-r n + 150   insere dentro do registro de expressões
                          o registro "n
        <Enter>  ........ executa o registro de expressões
        <Esc> ........... sai do modo de inserção
        0 ............... vai para o começo da linha
        q ............... para a gravação da macro

Agora posicione o cursor no começo da linha e pressione “`10@a`”.

Na seção [sub:Mapeamento para Calcular Expressões] página há mais dicas
sobre o uso do registro de expressões cálculos matemáticos.

Registros de arrastar e mover {#Registros de arrastar e mover}
-----------------------------

O registro

         "*

é responsável por armazenar o último texto selecionado (p.e., através do
mouse). Já o registro

         "+

é o denominado “área de transferência”, normalmente utilizado para se
transferir conteúdos entre aplicações—este registro é preenchido, por
exemplo, usando-se a típica combinação <span>Ctrl-v</span> encontrada em
muitas aplicações. Finalmente, o registro

         "~

armazena o texto colado pela operação mais recente de
“arrastar-e-soltar” (<span>*drag-and-drop*</span>).

Registro buraco negro "\_ {#Registro buraco negro}
-------------------------

Use este registro quando não quiser alterar os demais registros, por
exemplo: se você deletar a linha atual,

         dd

Esta ação irá colocar a linha atual no registro numerado 1, caso não
queira alterar o conteúdo do registro 1 apague para o buraco negro
assim:

         "_dd

Registros de buscas “/” {#Registros de buscas ``/''}
-----------------------

Se desejar inserir em uma substituição uma busca prévia, você poderia
fazer assim em modo de comandos:

         :%s,<Ctrl-r>/,novo-texto,g

Observação: veja que estou trocando o delimitador da busca para deixar
claro o uso do registro de buscas “/”. Pode-se usar um registro nomeado
de ‘<span>a-z</span>’ assim:

        let @a="new"
        :%s/old/\=@a/g ...... substitui 'old' por new
        \=@a ................ faz referência ao registro `a'

Manipulando registros {#Manipulando registros}
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

E o nome do arquivo será inserido

Listando os registros atuais {#Listando os registros atuais}
----------------------------

Digitando o comando

         :reg

ou ainda

         :ls

O Vim mostrará os registros numerados e nomeados atualmente em uso

Listando arquivos abertos {#Listando arquivos abertos}
-------------------------

Suponha que você abriu vários arquivos <span>txt</span> assim:

         vim *.txt

Para listar os arquivos aberto faça:

         :buffers

Usando o comando acima o Vim exibirá a lista de todos os arquivos
abertos, após exibir a lista você pode escolher um dos arquivos da
lista, algo como:

         :buf 3

Para editar arquivos em sequência faça as alterações no arquivo atual e
acesso o próximo assim:

         :wn

O comando acima diz $\rightarrow$ ‘<span>w gravar</span>’ $\rightarrow$
‘<span>n próximo</span>’

Dividindo a janela com o próximo arquivo da lista de <span>*buffers*</span> {#Dividindo a janela com o próximo arquivo da lista de buffers}
---------------------------------------------------------------------------

         :sn

O comando acima é uma abreviação de <span>*split next*</span>, ou seja,
dividir e próximo.

Como colocar um pedaço de texto em um registro? {#Como colocar um pedaço de texto em um registro?}
-----------------------------------------------

         <Esc> ...... vai para o modo normal
         "a10j ...... coloca no registro `a' as próximas 10 linhas
                      `10j'

Pode-se fazer:

         <Esc> ...... para ter certeza que está em modo normal
         "ap ........ registro a `paste', ou seja, cole

Em modo de inserção faz-se:

         Ctrl-r a

Há situações em que se tem caracteres não “*ascii* ” que são complicados
de se colocar em uma busca ou substituição, nestes casos pode-se usar os
seguintes comandos:

        "ayl ............. copia para o registro `a' o caractere sob
                           o cursor
        :%s/<c-r>a/char .. subsitui o conteúdo do registro `a' por
                           char

Pode-se ainda usar esta técnica para copiar rapidamente comentários do
“`bash`[^1]”, representados pelo caracteres `#`, em <span>*modo
normal*</span> usando o atalho “`0yljP`”.

        0 ............... posiciona o cursor no início a linha
        yl .............. copia o caractere sob o cursor
        j ............... desce uma linha
        P ............... cola o caractere copiado

Como criar um registro em modo visual? {#Como criar um registro em modo visual?}
--------------------------------------

Inicie a seleção visual com o atalho

         Shift-v ..... seleciona linhas inteiras

pressione a letra “`j`” até chegar ao ponto desejado, agora faça

         "ay

pressione “`v`” para sair do modo visual.

Como definir um registro no `vimrc`? {#Como definir um registro no vimrc?}
------------------------------------

Se você não sabe ainda como editar preferências no Vim leia antes o
capítulo [cha:Como editar preferências no Vim].

Você pode criar uma variável no <span>vimrc</span> assim:

         let var="foo" ...... define foo para var
         echo var ........... mostra o valor de var

Pode também dizer ao Vim algo como...

         :let @d=strftime("c")<Enter>

Neste caso estou dizendo a ele que guarde na variável ‘<span>d</span>’
at d, o valor da data do sistema ‘<span>strftime(“c”)</span>’ ou então
cole isto no <span>vimrc</span>:

         let @d=strftime("c")<cr>

A diferença entre digitar diretamente um comando e adicioná-lo ao
<span>vimrc</span> é que uma vez no <span>vimrc</span> o registro em
questão estará sempre disponível, observe também as sutis diferenças, um
<span>Enter</span> inserido manualmente é apenas uma indicação de uma
ação que você fará pressionando a tecla especificada, já o comando
mapeado vira “`<cr>`”, veja ainda que no <span>vimrc</span> os dois
pontos “`:`” somem.

Pode mapear tudo isto

         let @d=strftime("c")<cr>
         imap ,d <cr-r>d
         nmap ,d "dp

As atribuições acima correspondem a:

1.  Guarda a data na variável ‘<span>d</span>’

2.  Mapeamento para o modo de inserção “<span>imap</span>” digite
    <span>,d</span>

3.  Mapeamento para o modo normal “<span>nmap</span>” digite
    <span>,d</span>

E digitar <span>,d</span> normalmente

Desmistificando o <span>strftime</span>

         " d=dia m=mes Y=ano H=hora M=minuto c=data-completa
         :h strftime ........ ajuda completa sobre o comando

e inserir em modo normal assim:

         "dp

ou usar em modo de inserção assim:

         Ctrl-r d

Como selecionar blocos verticais de texto? {#Como selecionar blocos verticais de texto?}
------------------------------------------

         Ctrl-v

agora use as letras <span>h,l,k,j</span> como setas de direção até
finalizar podendo guardar a seleção em um registro que vai de
‘<span>a</span>’ a ‘<span>z</span>’ exemplo:

         "ay

Em modo normal você pode fazer assim para guardar um parágrafo inteiro
em um registro

         "ayip

O comando acima quer dizer

         para o registro `a' ......  "a
         copie ......................  `y'
         o parágrafo atual .......... `inner paragraph'

Referências {#Referências}
-----------

-   <http://rayninfo.co.uk/vimtips.html>

-   <http://aprendolatex.wordpress.com>

-   <http://pt.wikibooks.org/wiki/Latex>

[^1]: Interpretador de comandos do GNU/Linux
