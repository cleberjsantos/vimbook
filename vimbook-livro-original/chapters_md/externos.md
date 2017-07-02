Comandos Externos
=================

O Vim permite executar comandos externos para processar ou filtrar o
conteúdo de um arquivo. De forma geral, fazemos isso digitando (no modo
normal):

         :!ls .... visualiza o conteúdo do diretório

Lembrando que anexando um simples ponto, a saída do comando torna-se o
documento que está sendo editado:

         :.!ls .... imprime na tela o conteúdo do diretório

A seguir, veja alguns exemplos de utilização:

Ordenando
---------

Podemos usar o comando <span>*sort*</span> que ordena o conteúdo de um
arquivo dessa forma:

         :5,15!sort ..... ordena da linha 5 até a linha 15

O comando acima ordena da linha 5 até a linha 15.

O comando <span>*sort*</span> existe tanto no Windows quanto nos
sistemas Unix. Digitando simplesmente <span>*sort*</span>, sem
argumentos, o comportamento padrão é de classificar na ordem alfabética
(baseando-se na linha inteira). Para mais informações sobre argumentos
do comando <span>*sort*</span>, digite:

         sort --help ou man sort (no Unix) ou
         sort /? (no Windows).

Removendo linhas duplicadas
---------------------------

         :%!uniq

O caractere “%” representa a região equivalente ao arquivo atual
inteiro. A versão do Vim 7 em diante tem um comando <span>*sort*</span>
que permite remover linhas duplicadas <span>*uniq*</span> e ordenar, sem
a necessidade de usar comandos externos, para mais detalhes:

         :h sort

Ordenando e removendo linhas duplicadas no Vim 7
------------------------------------------------

         :sort u

Quando a ordenação envolver números faz-se:

         :sort n

<span>*Beautifiers*</span>
--------------------------

A maior parte das linguagens de programação possui ferramentas externas
chamadas <span>*beautifiers*</span>, que servem para embelezar o código,
através da indentação e espaçamento. Por exemplo, para embelezar um
arquivo HTML é possível usar a ferramenta “tidy[^1]”, do W3C:

         :%!tidy

Editando comandos longos no Linux {#Editando comandos longos no Linux}
---------------------------------

É comum no ambiente GNU/Linux a necessidade de digitar comandos longos
no terminal, para facilitar esta tarefa pode-se seguir estes passos:

1.  Definir o Vim como editor padrão do sistema editando o arquivo
    ‘<span>.bashrc</span>[^2]’:

                       #configura o vim como editor padrão
                       export EDITOR=vim
                       export VISUAL=vim
                    

2.  No terminal usar a combinação de teclas ‘<span>Ctrl-x-e</span>’.
    Esta combinação de teclas abre o editor padrão do sistema onde se
    deve digitar o comando longo, ao sair do editor o terminal executa o
    comando editado.

Compilando e verificando erros
------------------------------

Se o seu projeto já possui um <span>Makefile</span>, então você pode
fazer uso do comando <span>:make</span> para poder compilar seus
programas no conforto de seu Vim:

         :make

A vantagem de fazer isso é poder usar outra ferramenta bastante
interessante, a janela de <span>*quickfix*</span>:

         :cw[indow]

O comando <span>cwindow</span> abrirá uma janela em um
<span>*split*</span> horizontal com a listagem de erros e
<span>*warnings*</span>. Você poderá navegar pela lista usando os
cursores e ir diretamente para o arquivo e linha da ocorrência.

Modificando o compilador, o comando <span>make</span> pode mudar sua
ação.

        :compiler javac
        :compiler gcc
        :compiler php

Note que <span>*php*</span> não tem um compilador. Logo, quando
executado, o <span>make</span> irá verificar por erros de sintaxes.

        :compiler

O comando acima lista todos os compiladores suportados.

Grep {#sec:Grep}
----

Do mesmo jeito que você usa <span>grep</span> na sua linha de comando
você pode usar o <span>grep</span> interno do Vim. Exatamente do mesmo
jeito:

         :grep <caminho> <padrão> <opções>

Use a janela de <span>*quickfix*</span>[^3] aqui também para exibir os
resultados do <span>grep</span> e poder ir diretamente a eles.

Indent
------

<span>Indent</span>[^4] é um programa que indenta seu código fonte de
acordo com os padrões configurados no seu arquivo
<span>HOME/.indent.pro</span>. Vou pressupor que você já saiba usar o
<span>indent</span> e como fazer as configurações necessárias para ele
funcionar, então vamos ao funcionamento dele no Vim:

Para indentar um bloco de código, primeiro selecione-o com o modo
<span>*visual line*</span> (com <span>V</span>), depois é só entrar com
o comando como se fosse qualquer outro comando externo:

         :!indent

No caso, como foi selecionado um bloco de código, irão aparecer alguns
caracteres extras, mas o procedimento continua o mesmo:

         :'<,'>!indent

Calculadora Científica com o Vim {#sec:Calculadora Científica com o Vim}
--------------------------------

Para usar a função de Calculadora Científica no Vim usamos uma
ferramenta externa, que pode ser o comando ‘<span>bc</span>’ do
GNU/Linux, ou uma linguagem de programação como <span>*Python*</span> ou
<span>*Ruby*</span>, veremos como habilitar a calculadora usando o
<span>*Python*</span>. Obviamente esta linguagem de programação deve
estar instalada no sistema em que se deseja usar seus recursos. Deve-se
testar se a versão do Vim tem suporte ao Python “`:version`”, em seguida
colocam-se os mapeamentos no “.vimrc”.

         :command! -nargs=+ Calc :py print <args>
         :py from math import *

Feito isto pode-se usar o comando “<span>:Calc</span>” como visto
abaixo:

         :Calc pi
         :Calc cos(30)
         :Calc pow(5,3)
         :Calc 10.0/3
         :Calc sum(xrange(1,101))
         :Calc [x**2 for x in range(10)] 

Editando saídas do Shell {#sec:Editando saídas do Shell}
------------------------

Muitas vezes, precisamos manipular saídas do shell antes de enviá-las
por e-mail, reportar ao chefe ou até mesmo salvá-las. Utilizando

         vim -
         ou
         gvim -

a saída do Shell é redirecionada para o (G)Vim automaticamente, não
sendo necessário redirecioná-la para um arquivo temporário e, logo após,
abrí-lo para editá-lo e modificá-lo. Quem trabalha com sistemas de
controle de versão como svn pode visualizar as diferenças entre o código
que está sendo editado e o que está no repositório com sintaxe colorida
desta forma:

        svn diff | view -

Outra situação em que se pode combinar o vim com saidas do shell é com o
comando ‘`grep`’. Usando-se a opção ‘`-l`’ do grep listamos apenas os
arquivos que correspondem a um padrão.

        grep -irl voyeg3r .
        ./src/img/.svn/entries
        ./src/Makefile
        ./src/vimbook.tex

Pode-se em seguida chamar o vim usando substituição de comandos, como o
comando ‘`!!`’ corresponde ao último comando, e neste caso a saida
corresponde a uma lista de arquivos que contém o padrão a ser editado
faz-se:

        vim ${!!}

Log do Subversion
-----------------

A variável de ambiente <span>*\$SVN\_EDITOR*</span> pode ser usada para
se especificar o caminho para o editor de texto de sua preferência, a
fim de usá-lo na hora de dar um <span>*commit*</span> usando o
<span>*subversion*</span>.

         export SVN_EDITOR=/usr/bin/vim
         svn commit

Será aberto uma sessão no Vim, que depois de salva, será usada para LOG
do commit.

Referências
-----------

-   <http://www.dicas-l.com.br/dicas-l/20070119.php>

-   <http://vim.wikia.com/wiki/Scientific_calculator>

-   <http://docs.python.org/library/cmath.html>

-   <http://docs.python.org/library/math.html>

[^1]: http://tidy.sourceforge.net/

[^2]: Arquivo de configuração do bash

[^3]: <span>:cope</span>

[^4]: http://www.gnu.org/software/indent
