Repetição de Comandos {#Repetição de comandos}
=====================

Para repetir a última edição saia do modo de Inserção e pressione ponto
(.):

         .

Para inserir um texto que deve ser repetido várias vezes:

1.  Posicione o cursor no local desejado;

2.  Digite o número de repetições;

3.  Entre em modo de inserção;

4.  Digite o texto;

5.  Saia do modo de inserção (tecle <span>Esc</span>).

Por exemplo, se você quiser inserir oitenta traços numa linha, em vez de
digitar um por um, você pode digitar o comando:

         80i-<Esc>

Veja, passo a passo, o que aconteceu:

Antes de entrar em modo de inserção usamos um quantificador

         `80'

depois iniciamos o modo de inserção

         i

depois digitamos o caractere a ser repetido

         -

e por fim saímos do modo de inserção

         <Esc>

Se desejássemos digitar 10 linhas com o texto

         isto é um teste

deveríamos então fazer assim:

         <Esc> .. para ter certeza que ainda estamos no modo normal
         10 ..... quantificador antes
         i ...... entrar no modo de inserção
         isto é um teste <Enter>
         <Esc> .. voltar ao modo normal

Repetindo a digitação de uma linha 
-----------------------------------

         modo de inserção
         Ctrl-y .......... repete a linha acima 
         Ctrl-e .......... repetira linha abaixo 
         Ctrl-x Ctrl-l ... repete linhas completas

O atalho <span>Ctrl-x Ctrl-l</span> só funcionará para uma linha
semelhante, experimente digitar:

         uma linha qualquer com algum conteúdo
         uma linha <Ctrl-x Ctrl-l>

e veja o resultado

Guardando trechos em “registros” {#sec:Guardando trechos em ``registros''}
--------------------------------

Os registradores ‘<span>a-z</span>’ são uma espécie de área de
transferência múltipla.

Deve-se estar em modo normal e então digitar aspas duplas e uma das 26
letras do alfabeto, em seguida uma ação por exemplo, ‘<span>y</span>’
(copiar) ‘<span>d</span>’ (apagar). Depois, mover o cursor para a linha
desejada e colar com `"rp`, onde ‘<span>r</span>’ corresponde ao
registrador para onde o trecho foi copiado.

         "ayy ... copia a linha atual para o registrador `a'
         "ap  ... cola o conteúdo do registrador `a' abaixo
         "bdd ... apaga a linha atual para o registrador `b'

Gravando comandos {#sec:Gravando comandos}
-----------------

Imagine que você tem o seguinte trecho de código:

         stdio.h
         fcntl.h
         unistd.h
         stdlib.h

e quer que ele fique assim:

         #include "stdio.h"
         #include "fcntl.h"
         #include "unistd.h"
         #include "stdlib.h"

Não é possível simplesmente executar repetidas vezes um comando do Vim,
pois é preciso incluir texto tanto no começo quanto no fim da linha? É
necessário mais de um comando para isso. É aí que entram as macros.
Pode-se gravar até 26 macros, já que elas são guardadas nos registros do
Vim, que são identificados pelas letras do alfabeto. Para começar a
gravar uma macro no registro ‘a’, digitamos

         qa

No modo Normal. Tudo o que for digitado a partir de então, será gravado
no registro ‘a’ até que seja concluído com o comando `<Esc>q` novamente
(no modo Normal). Assim, soluciona-se o problema:

         <Esc> ....... para garantir que estamos no modo normal
         qa .......... inicia a gravação da macro `a'
         I ........... entra no modo de inserção no começo da linha
         #include " .. insere #include "
         <Esc> ....... sai do modo de inserção
         A" .......... insere o último caractere
         <Esc> ....... sai do modo de inserção
         j ........... desce uma linha
         <Esc> ....... sai do modo de inserção
         q ........... para a gravação da macro

Agora só é preciso posicionar o cursor na primeira letra de uma linha
como esta

         stdio.h

E executar a macro do registro ‘a’ quantas vezes for necessário, usando
o comando `@a`. Para executar quatro vezes, digite:

         4@a

Este comando executa quatro vezes o conteúdo do registro ‘a’.

Caso tenha sido executada, a macro pode ser repetida com o comando

         @@

Repetindo substituições 
------------------------

Caso seja feito uma substituição em um intervalo como abaixo

         :5,32s/isto/aquilo/g

Pode-se repetir esta substituição em qualquer linha que estiver apenas
usando este símbolo

         &

O Vim substituirá na linha corrente ‘isto’ por ‘aquilo’. Podendo repetir
a última substituição globalmente assim:

         g&

Repetindo comandos {#Repetindo comandos}
------------------

         @:

O atalho acima repete o último comando no próprio modo de comandos

<span>*Scripts*</span> Vim {#Scripts Vim}
--------------------------

Usando um <span>*script*</span> para modificar um nome em vários
arquivos: Crie um arquivo chamado <span>subst.vim</span> contendo os
comandos de substituição e o comando de salvamento <span>:wq</span>.

         %s/bgcolor="eeeeee"/bgcolor="ffffff"/g
         wq

Para executar um <span>*script*</span>, digite o comando

         :source nome_do_script.vim

O comando <span>:source</span> também pode ser abreviado com
<span>:so</span> bem como ser usado para testar um esquema de cor:

        :so tema.vim

Usando o comando `bufdo` {#Usando o comando bufdo}
------------------------

Com o comando <span>:bufdo</span>, pode-se executar um comando em um
conjunto de arquivos de forma rápida. No exemplo a seguir, serão abertos
todos os arquivos HTML do diretório atual, será efetuado uma
substituição e em seguida serão todos salvos.

         vim *.html
         :bufdo %s/bgcolor="eeeeee"/bgcolor="ffffff"/ge | :wall
         :qall

O comando <span>:wall</span> salva “<span>*write*</span>” todos
“<span>*all*</span>” os arquivos abertos pelo comando
<span>vim \*.html</span>. Opcionalmente você pode combinar
“<span>:wall</span>” e “<span>:qall</span>” com o comando
<span>:wqall</span>, que salva todos os arquivos abertos e em seguida
sai do Vim. A opção ‘<span>e</span>’ faz com que o vim não exiba
mensagens de erro caso o <span>*buffer*</span> em questão não contenha o
padrão a ser substituído.

Colocando a última busca em um comando 
---------------------------------------

Observação: lembre-se `Ctrl = ^`

         :^r/

Inserindo o nome do arquivo no comando 
---------------------------------------

         :^r%

Inserindo o último comando 
---------------------------

         ^r:

Se preceder com “:” você repete o comando, equivale a acessar o
histórico de comandos com as setas

         :^r:

Inserindo a palavra sob o cursor em um comando
----------------------------------------------

O comando abaixo pode ser usado para pegar por exemplo, a palavra que
está atualmente sob o cursor, e coloca-la em um comando de busca.

        ^r^w

Para repetir exatamente a última inserção 
------------------------------------------

         i<c-a>
