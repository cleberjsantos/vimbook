Editando {#Editando}
========

A principal função de um editor de textos é editar textos. Parece óbvio,
mas em meio a inúmeros recursos extras essa simples e crucial função
perde-se entre todos os demais.

Abrindo o arquivo para a edição
-------------------------------

Portanto, a primeira coisa a fazer é abrir um arquivo. Como visto, para
abrir um arquivo com Vim, digite em um terminal:

         vim texto.txt

onde <span>texto.txt</span> é o nome do arquivo que deseja-se criar ou
editar.

Caso deseje abrir o arquivo na linha 10, usa-se:

         vim +10 /caminho/para/o/arquivo

se quiser abrir o arquivo na linha que contém um determinado padrão ,
digite:

         vim +/padrão arquivo

Caso o padrão tenha espaços no nome coloque entre aspas ou use
<span>*escape*</span> “$\backslash$” a fim de não obter erro.

Se o vim for aberto sem indicação de arquivo pode-se indicar o arquivo a
ser editado em modo de comando desta forma:

        :e /home/usuario/arquivo

Escrevendo o texto
------------------

O Vim é um editor que possuí diferentes modos de edição. Entre eles está
o modo de inserção, que é o modo onde escreve-se o texto naturalmente.

Para se entrar em modo de inserção, estando em modo normal, pode-se
pressionar qualquer uma das teclas abaixo:

         i ..... entra no modo de inserção antes do caractere atual
         I ..... entra no modo de inserção no começo da linha
         a ..... entra no modo de inserção após o caractere atual
         A ..... entra no modo de inserção no final da linha
         o ..... entra no modo de inserção uma linha abaixo
         O ..... entra em modo de inserção uma linha cima
         <Esc> . sai do modo de inserção

Uma vez no modo de inserção todas as teclas são exatamente como nos
outros editores simples, caracteres que constituem o conteúdo do texto
sendo digitado. O que inclui as teclas de edição de caracteres.

Para salvar o conteúdo escrito, digite a tecla `<Esc>` para sair do modo
de inserção e digite o comando ‘`:w`’ para gravar o conteúdo. Caso
queira sair do editor, digite o comando: ‘`:q`’ caso tenha ocorrido
modificações no arquivo desde que ele foi salvo pela última vez haverá
uma mensagem informando que o documento foi modificado e não foi salvo,
nesse caso, digite o comando \``:q!` para fechar o Vim <span>**sem
salvar**</span> as últimas modificações feitas. Caso queira salvar e
sair do arquivo, digite o comando ‘`:wq`’

Nesse ponto, conhece-se o vim de forma suficiente para editar qualquer
coisa nele. Daqui por diante o que existe são as formas de realizar a
edição do arquivo com maior naturalidade e produtividade.

O usuário iniciante do Vim pode cometer o erro de tentar decorar todos
os comandos que serão apresentados. <span>**Não faça isso**</span>.
Tentar decorar comando é exatamente o caminho contrário da naturalidade
exigida por um editor texto para aumentar a produtividade.

Ao contrário, sugere-se que leia-se todo o conteúdo. Identifique quais
são as atividades de maior recorrência no estilo individual de escrita e
busque como realizar tais funções com mais fluência nesse editor. A
prática levará ao uso de fluente desse comandos principais, abrindo
espaço para os demais comandos.

Isso não impede que o usuário experimente cada comando conforme for
lendo. De fato, essa prática pode ajudar a selecionar as formas de
edição que lhe são mais simpáticas ao uso.

Copiar, Colar e Deletar {#sec:CopiarColarEDeletar}
-----------------------

No modo normal, o ato de deletar ou eliminar o texto está associado à
letra “`d`”. No modo de inserção as teclas usuais também funcionam.

         dd .... deleta linha atual
         D ..... deleta restante da linha
         d$ .... deleta do ponto atual até o final da linha
         d^ .... deleta do cursor ao primeiro caractere não-nulo da 
                 linha
         d0 .... deleta do cursor ao início da linha

Pode-se combinar o comando de deleção “`d`” com o comando de movimento
(considere o modo normal) para apagar até a próxima vírgula use:
“`df,`”.

Copiar está associado à letra “`y`”.

         yy .... copia a linha atual
         Y ..... copia a linha atual
         ye .... copia do cursor ao fim da palavra
         yb .... copia do começo da palavra ao cursor

O que foi deletado ou copiado pode ser colado:

         p .... cola o que foi copiado ou deletado abaixo
         P .... cola o que foi copiado ou deletado acima
         [p ... cola o que foi copiado ou deletado antes do cursor
         ]p ... cola o que foi copiado ou deletado após o cursor

### Deletando uma parte do texto {#Deletando uma parte do texto}

O comando ‘<span>d</span>’ remove o conteúdo para a memória.

         x .... apaga o caractere sob o cursor
         xp ... troca letras de lugar
         ddp .. troca linhas de lugar
         d5x .. apaga os próximos 5 caracteres
         dd  .. apaga a linha atual
         5dd .. apaga 5 linhas (também pode ser: d5d)
         d5G .. apaga até a linha 5
         dw  .. apaga uma palavra
         5dw .. apaga 5 palavras (também pode ser: d5w)
         dl  .. apaga uma letra (sinônimo: x)
         5dl .. apaga 5 letras (também pode ser: d5l ou 5x)
         d0  .. apaga até o início da linha
         d^  .. apaga até o primeiro caractere da linha
         d$  .. apaga até o final da linha (sinônimo: D)
         dgg .. apaga até o início do arquivo
         dG  .. apaga até o final do arquivo
         D .... apaga o resto da linha
         d% ... deleta até o próximo (,[,{
         da" .. deleta aspas com conteúdo

Depois do texto ter sido colocado na memória, digite ‘<span>p</span>’
para ‘inserir’ o texto em uma outra posição. Outros comandos:

         diw .. apaga palavra mesmo que não esteja posicionado no 
                início
         dip .. apaga o parágrafo atual
         d4b .. apaga as quatro palavras anteriores
         dfx .. apaga até o próximo ``x''
         d/casa/+1 - deleta até a linha após a palavra casa

Trocando a letra ‘<span>d</span>’ nos comandos acima por
‘<span>c</span>’ de <span>*change*</span> “mudança” ao invés de deletar
será feita uma mudança de conteúdo. Por exemplo:

         ciw .............. modifica uma palavra
         cip .............. modifica um parágrafo
         cis .............. modifica uma sentença
         C ................ modifica até o final da linha

### Copiando sem deletar {#Copiando sem deletar}

O comando ‘<span>y</span>’ (<span>*yank*</span>) permite copiar uma
parte do texto para a memória sem deletar. Existe uma semelhança muito
grande entre os comandos ‘<span>y</span>’ e os comandos
‘<span>d</span>’, um ativa a ‘cópia’ e outro a ‘exclusão’ de conteúdo,
suportando ambos quantificadores:

         yy  .... copia a linha atual (sinônimo: Y)
         5yy .... copia 5 linhas (também pode ser: y5y ou 5Y)
         y/pat .. copia até `pat'
         yw  .... copia uma palavra
         5yw .... copia 5 palavras (também pode ser: y5w)
         yl  .... copia uma letra
         5yl .... copia 5 letras (também pode ser: y5l)
         y^  .... copia da posição atual até o início da linha
                  (sinônimo: y0)
         y$  .... copia da posição atual até o final da linha
         ygg .... copia da posição atual até o início do arquivo
         yG  .... copia da posição atual até o final do arquivo

Digite ‘<span>P</span>’ (p maiúsculo) para colar o texto recém copiado
na posição onde encontra-se o cursor, ou ‘<span>p</span>’ para colar o
texto na posição imediatamente após o cursor.

         yi" .... copia trecho entre aspas (atual - inner)
         vip .... seleção visual para parágrafo atual 
                  `inner paragraph'
         yip .... copia o parágrafo atual
         yit .... copia a tag agual `inner tag' útil para arquivos 
                  HTML, XML, etc.

### Usando a área de transferência <span>*Clipboard*</span>

Exemplos para o modo visual:

         Ctrl-insert .... copia área selecionada 
         Shift-insert ... cola o que está no clipboard
         Ctrl-del ....... recorta para o clipboard

Caso obtenhamos erro ao colar textos da área de transferência usando os
comandos acima citados podemos usar outra alternativa. Os comandos
abaixo preservam a indentação[^1].

         "+p ............ cola preservando indentação
         "+y ............ copia área selecionada

Para evitar erros ao colar usando <span>Shift-insert</span> use este
comando ‘<span>:set paste</span>’.

### Removendo linhas duplicadas

         :sort u

Forçando a edição de um novo arquivo {#sec:Forçando a edição de um novo arquivo}
------------------------------------

O Vim, como qualquer outro editor, é muito exigente no que se refere a
alterações de arquivo. Ao tentar abandonar um arquivo editado e não
salvo, o Vim irá se certificar da ação. Para abrir um novo arquivo sem
salvar o antigo:

         :enew!

O comando acima é uma abreviação de <span>*edit new*</span>. De modo
similar pode-se ignorar todas as alterações feitas desde a abertura do
arquivo:

         :e!

Ordenando
---------

O Vim, versão 7 ou superior, passa a ter um comando de ordenação que
também permite a retirada de linhas duplicadas, tal como foi
apresentado.

         :sort u ... ordena e retira linhas duplicadas
         :sort n ... ordena numericamente

Obs: a ordenação numérica é diferente da ordenação alfabética se em um
trecho contendo algo como:

         8
         9
         10
         11
         12

Você tentar fazer:

         :sort

O Vim colocará nas três primeiras linhas

         10
         11
         12

Portanto lembre-se que se a ordenação envolver números use:

         :sort n

Você pode fazer a ordenação em um intervalo assim:

         :1,15 sort n

O comando acima diz “<span>*Ordene numericamente da linha 1 até a linha
15*</span>”. Podemos ainda ordenar à partir de uma coluna:

         :sort /.*\%8v/   ..... ordena à partir do 8º caractere

Usando o `grep` interno do Vim {#sec:Usando o grep interno do Vim}
------------------------------

Para editar todos os arquivos que contenham a palavra “inusitada”:

        :vimgrep /\cinusitada/ *

a opção ‘`\c`’ torna a busca indiferente a letras maiúsculas e
minúsculas.

Obs: o Vim busca à partir do diretório atual, para se descobrir o
diretório atual ou mudá-lo:

        :pwd ........... exibe o diretório atual
        :cd /diretório   muda de diretório

Lista de alterações
-------------------

O Vim mantém uma lista de alterações, veremos agora como usar este
recurso.

         g, ................. avança na lista de alterações
         g; ................. recua na lista de alterações
         :changes ........... visualiza a lista de alterações

Substituindo tabulações por espaços {#sec:Substituindo tabulações por espaços}
-----------------------------------

Se houver necessidade[^2] de trocar tabulações por espaços fazemos
assim:

          :set tabstop=4 "tamanho da parada de tabulação
         :set expandtab
         :retab

Para fazer o contrário usamos algo como:

        :%s/\s\{4,}/<pressiona-se ctrl-i>/g

onde

        <Ctrl-i>...... insere uma tabulação

Explicando:

        : ............ comando
        % ............ em todo arquivo 
        s ............ substitua 
        / ............ padrão de busca
        \s ........... localiza espaço
        \{4,} ........ quatro vezes
        / ............ inicio da substituição
        <Ctrl-i> ..... pressione Ctrl-i para inserir <Tab>
        / ............ fim da substituição
        g ............ global

Convertendo para maiúsculas {#sec:Convertendo para maiúsculas}
---------------------------

         gUU ....... converte a linha para maiúsculo
         guu ....... converte a linha para minúsculo
         gUiw ...... converte a palavra atual para maiúsculo
         ~ ......... altera o case do caractere atual

Editando em modo de comando {#sec:Editando em modo de comando}
---------------------------

Para mover um trecho usando o modo de comandos faça:

         :10,20m $

O comando acima move ‘<span>m</span>’ da linha 10 até a linha 20 para o
final `$`.

         :g /palavra/ m 0

Move as linhas contendo ‘palavra’ para o começo (linha zero)

         :10,20y a

Copia da linha ‘10’ até a linha ‘20’ para o registro ‘a’

         :56pu a

Cola o registro ‘a’ na linha 56

         :g/padrão/d

O comando acima deleta todas as linhas contendo a palavra ‘padrão’.

Podemos inverter a lógica do comando global `g`:

         :g!/padrão/d

Não delete as linhas contendo padrão, ou seja, delete tudo menos as
linhas contendo a palavra ‘padrão’.

         :v/padrão/d ........ apaga linhas que não contenham "padrão"
         :v/\S/d ............ apaga linhas vazias
         \S ................. significa "string"

A opção acima equivale a “`:g!/padrão/d`”. Para ler mais sobre o comando
“global” utilizado nesta seção veja o capítulo [sec:O comando global
“g”].

         :7,10copy $

Da linha 7 até a linha 10 copie para o final. Veja mais sobre edição no
modo de comando na seção “[cha:Buscas e substituições] Buscas e
substituições na página ”.

#### Gerando sequências

Para inserir uma sequência de 1 a 10 à partir da linha inicial “zero”
fazemos:

         :0put =range(1,10)

Caso queira inserir sequências como esta:

         192.168.0.1
         192.168.0.2
         192.168.0.3
         192.168.0.4
         192.168.0.5

Usamos este comando:

         :for i in range(1,5) | .put ='192.168.0.'.i | endfor

O arquivo alternativo {#O arquivo alternativo}
---------------------

É muito comum um usuário concluir a edição em um arquivo no Vim e
inocentemente imaginar que não vai mais modificar qualquer coisa nele,
então este usuário abre um novo arquivo:

         :e novo-arquivo.txt

Mas de repente o usuário lembra que seria necessário adicionar uma linha
no arquivo recém editado, neste caso usa-se o atalho

         Ctrl-6

cuja função é alternar entre o arquivo atual e o último editado. Para
retornar ao outro arquivo basta portanto pressionar `Ctrl-6` novamente.
Pode-se abrir o arquivo alternativo em nova janela usando-se o atalho:

        Ctrl-w Ctrl-6

Mais informações sobre “janelas” leia a seção [cha:Trabalhando com
janelas] na página .

Lendo um arquivo para a linha atual {#sec:Lendo um arquivo para a linha atual}
-----------------------------------

Se desejamos inserir na linha atual um arquivo qualquer fazemos:

         :r /caminho/para/arquivo.txt .. insere o arquivo na linha atual
         :0r arquivo ................... insere o arquivo na primeira 
                                        linha

Incrementando números em modo normal {#Incrementando números em modo normal}
------------------------------------

Posicione o cursor sobre um número e pressione

         Ctrl-a ..... incrementa o número
         Ctrl-x ..... decrementa o número

Repetindo a digitação de linhas {#Repetindo a digitação de linhas}
-------------------------------

         " atalhos para o modo insert
         Ctrl-y ......... repete linha acima
         Ctrl-e ......... repete linha abaixo
         Ctrl-x Ctrl-l .. repete linhas inteiras
         Ctrl-a ......... repete a última inserção

Para saber mais sobre repetição de comandos veja o capítulo [Repetição
de comandos], na página .

Movendo um trecho de forma inusitada {#Movendo um trecho de forma inusitada}
------------------------------------

         :20,30m 0 ..... move da linha `20' até `30' para o começo
         :20,/pat/m 5 .. move da linha `20' até `pat' para a linha 5
         :m-5 .......... move a linha atual 5 posições acima
         :m0 ........... move a linha atual para o começo
         :m$ ........... move para o final do documento

Uma calculadora diferente {#Uma calculadora diferente}
-------------------------

Sempre que for necessário digitar o resultado de uma expressão
matemática (portanto no modo de inserção) pode-se usar o atalho
“<span>Ctrl-r =</span>”, ele ativa o registro de expressões, na linha de
comando do Vim aparece um sinal de igual, digita-se então uma expressão
matemática qualquer tipo “<span>35\*6</span>” e em seguida pressiona-se
“<span>Enter</span>”, o Vim coloca então o resultado da expressão no
lugar desejado. Portanto não precisa-se recorrer a nenhuma calculadora
para fazer cálculos. Pode-se fazer uso do “Registro de Expressões”
dentro de macros, ou seja, ao gravar ações pode-se fazer uso deste
recurso, aumentando assim sua complexidade e poder! Para ler sobre
“macros” acesse a seção [sec:Gravando comandos] na . Para saber mais
sobre o “registro de expressões” leia a seção [sec:Registro de
expressões "=] na página .

Na seção [sec:Calculadora Científica com o Vim] “Calculadora Científica
com o vim” página  há uma descrição sobre como fazer cálculos com maior
precisão e complexidade.

Se a intenção for apenas exibir um calculo na barra de comandos é
possível fazer algo assim:

        :echo 5.2 * 3

Desfazendo {#Desfazendo}
----------

Se você cometer um erro, não se preocupe! Use o comando
‘<span>u</span>’:

         u ............ desfazer
         U ............ desfaz mudanças na última linha editada
         Ctrl-r  ...... refazer

### <span>*Undo tree*</span> {#Undo tree}

Um novo recurso muito interessante foi adicionado ao Vim “a partir da
versão 7” é a chamada árvore do desfazer. Se você desfaz alguma coisa,
fez uma alteração um novo <span>*branch*</span> ou galho, derivação de
alteração é criado. Basicamente, os <span>*branches*</span> nos permitem
acessar quaisquer alterações ocorridas no arquivo.

#### Um exemplo didático {#Um exemplo didático}

Siga estes passos (para cada passo `<Esc>`, ou seja, saia do modo de
inserção)

Passo 1

:   - digite na linha 1 o seguinte texto

             # controle de fluxo <Esc>

Passo 2

:   - digite na linha 2 o seguinte texto

             # um laço for <Esc>

Passo 3

:   - Nas linhas 3 e 4 digite...

             for i in range(10):
                 print i  <Esc>

Passo 4

:   - pressione ‘<span>u</span>’ duas vezes (você voltará ao passo 1)

Passo 5

:   - Na linha 2 digite

             # operador ternário <Esc>

Passo 6

:   - na linha 3 digite

             var = (1 if teste == 0 else 2)  <Esc>

Obs: A necessidade do <span>Esc</span> é para demarcar as ações, pois o
Vim considera cada inserção uma ação. Agora usando o atalho de desfazer
tradicional “u” e de refazer <span>Ctrl-r</span> observe que não é mais
possível acessar todas as alterações efetuadas. Em resumo, se você fizer
uma nova alteração após um desfazer (alteração derivada) o comando
refazer não mais vai ser possível para aquele momento.

Agora volte até a alteração 1 e use seguidas vezes:

         g+

e/ou

         g-

Dessa forma você acessará todas as alterações ocorridas no texto.

### <span>*Máquina do tempo*</span> {#Máquina do tempo}

O Vim possui muitas formas para desfazer e refazer, e uma das mais
interessantes é a máquina do tempo! A máquina do tempo é extremamente
útil quando no meio de um texto se percebe que boa parte do que foi
adicionado é inútil e que nos ultimos 10 minutos não há nada que se
possa aproveitar. Utilizando a máquina do tempo é possível eliminar os
últimos 10 minutos de texto inútil do seu documento facilmente,
utilizando:

        :earlier 10m

Com esse comando o documento ficará exatamente como ele estava 10
minutos atrás! Caso após a exclusão perceba-se que foi excluído um
minuto a mais, é possível utilizar o mesmo padrão novamente para avançar
no tempo:

        :later 60s

Note que dessa vez foi utilizado <span>*later*</span> ao invés de
<span>*earlier*</span>, e passando segundos como argumento para viajar
no tempo. Portanto o comando acima avança 60 segundos no tempo.

Para uma melhor visão de quanto se deve voltar, pode ser usado o
comando:

        :undolist

O comando acima mostra a lista com as informações sobre Desfazer e
Refazer. E com essas informações pode-se voltar no tempo seguindo cada
modificação:

        :undo 3

Esse comando fará o documento regredir 3 modificações.

Salvando {#sec:Salvando}
--------

A maneira mais simples de salvar um arquivo, é usar o comando:

         :w

Para especificar um novo nome para o arquivo, simplesmente digite:

         :w! >> ``file''

O conteúdo será gravado no arquivo “<span>file</span>” e você continuará
no arquivo original.

Também existe o comando

         :sav[eas] nome

salva o arquivo com um novo nome e muda para esse novo arquivo (o
arquivo original não é apagado). Para sair do editor, salvando o arquivo
atual, digite <span>:x</span> (ou <span>:wq</span>).

         :w ............................ salva
         :wq  .......................... salva e sai
         :w nome ....................... salvar como
         :saveas nome .................. salvar como
         :sav nome ..................... mesmo que "saveas nome"
         :x ............................ salva se existirem 
                                         modificações
         :10,20 w! ~/Desktop/teste.txt . salva um trecho para outro 
                                         arquivo
         :w! ........................... salvamento forçado
         :e! ........................... reinicia a edição ignorando 
                                         alterações

Abrindo o último arquivo rapidamente
------------------------------------

O Vim guarda um registro para cada arquivo editado veja mais no capítulo
[Registros] na página .

         '0 ........ abre o último arquivo editado
         '1 ........ abre o penúltimo arquivo editado
         Ctrl-6 .... abre o arquivo alternativo (booleano)

Bom, já que abrimos o nosso último arquivo editado com o comando

         `0

podemos, e provavelmente o faremos, editar no mesmo ponto em que
estávamos editando da última vez:

         gi

Pode-se criar um ‘<span>alias</span>’[^3] para que ao abrir o vim o
mesmo abra o último arquivo editado:
‘`alias lvim="vim -c \"normal '0\""`’. No capítulo [cha:Buscas e
substituições] página você encontra mais dicas de edição.

Modelines {#sec:Modelines}
---------

São um modo de guardar preferências no próprio arquivo, suas
preferências viajam literalmente junto com o arquivo, basta usar em uma
das 5 primeiras linhas ou na última linha do arquivo algo como:

         # vim:ft=sh:

OBS: Você deve colocar um espaço entre a palavra ‘<span>vim</span>’ e a
primeira coluna, ou seja, a palavra ‘<span>vim</span>’ deve vir
precedida de um espaço, daí em diante cada opção fica assim:

         :opção:

Por exemplo: posso salvar um arquivo com extensão `.sh` e dentro do
mesmo indicar no <span>*modeline*</span> algo como:

         # vim:ft=txt:nu:

Apesar de usar a extensão ‘<span>sh</span>’ o Vim reconhecerá este
arquivo como ‘<span>txt</span>’, e caso eu não tenha habilitado a
numeração, ainda assim o Vim usará por causa da opção ‘<span>nu</span>’.
Portanto o uso de <span>*modelines*</span> pode ser um grande recurso
para o seu dia-a-dia pois você pode coloca-las dentro dos comentários!

Edição avançada de linhas
-------------------------

Seja o seguinte texto:

         1  este é um texto novo
         2  este é um texto novo
         3  este é um texto novo
         4  este é um texto novo
         5  este é um texto novo
         6  este é um texto novo
         7  este é um texto novo
         8  este é um texto novo
         9  este é um texto novo
         10 este é um texto novo

Suponha que queira-se apagar “<span>é um texto</span>” da linha 5 até o
fim (linha 10). Isto pode ser feito assim:

         :5,$ normal 0wd3w

Explicando o comando acima:

         :5,$ .... indica o intervalo que é da linha 5 até o fim `$'
         normal .. executa em modo normal
         0 ....... move o cursor para o começo da linha
         w ....... pula uma palavra
         d3w ..... apaga 3 palavras `w'

Obs: É claro que um comando de substituição simples

         :5,$s/é um texto//g

Resolveria neste caso, mas a vantagem do método anterior é que é válido
para três palavras, sejam quais forem. Também é possível empregar
comandos de inserção como ‘<span>i</span>’ ou ‘<span>a</span>’ e
retornar ao modo normal, bastando para isso usar o recurso `Ctrl-v Esc`,
de forma a simular o acionamento da tecla `Esc` (saída do modo de
inserção). Por exemplo, suponha agora que deseja-se mudar a frase
“<span>*este é um texto novo*</span>” para “<span>*este não é um texto
velho*</span>”; pode ser feito assim:

         :5,$ normal 02winão ^[$ciwvelho

Decompondo o comando acima temos:

         :5,$ .... indica o intervalo que é da linha 5 até o fim `$'
         normal .. executa em modo normal
         0 ....... move o cursor para o começo da linha
         2w ...... pula duas palavras (vai para a palavra "é")
         i ....... entra no modo de inserção
         não  .... insere a palavra "não" seguida de espaço " "
         ^[ ...... sai do modo de inserção (através de Ctrl-v seguido 
                   de Esc)
         $ ....... vai para o fim da linha
         ciw ..... apaga a última palavra ("novo") e entra em modo de 
                   inserção
         velho ... insere a palavra "velho" no lugar de "novo"

A combinação `Ctrl-v` é utilizada para inserir caracteres de controle na
sua forma literal, prevenindo-se assim a interpretação destes neste
exato momento.

Comentando rapidamente um trecho
--------------------------------

Tomando como exemplo um trecho de código como abaixo:

         1   input{capitulo1}
         2   input{capitulo2}
         3   input{capitulo3}
         4   input{capitulo4}
         5   input{capitulo5}
         6   input{capitulo6}
         7   input{capitulo7}
         8   input{capitulo8}
         9   input{capitulo9}

Se desejamos comentar da linha 4 até a linha 9 podemos fazer:

         posicionar o cursor no começo da linha 4
         Ctrl-v ........... inicia seleção por blocos
         5j ............... estende a seleção até o fim
         Shift-i .......... inicia inserção no começo da linha
         % ................ insere comentário (LaTeX)
         Esc .............. sai do modo de inserção

Comparando arquivos com o vimdiff {#sec:Comparando arquivos com o vimdiff}
---------------------------------

O vim possui um modo para checagem de diferenças entre arquivos, é
bastante útil especialmente para programadores, para saber quais são as
diferenças entre dois arquivos faz-se:

        vimdiff arquivo1.txt arquivo2.txt .. exibe as diferenças
        ]c ................................. mostra próxima diferença
        vim -d ............................. outro modo de abrir o 
                                             vimdiff mode

Para usuários do GNU/Linux é possível ainda checar diferenças
remotamente assim:

        vimdiff projeto scp://usuario@estacao//caminho/projeto

O comando acima irá exibir lado a lado o arquivo local chamado
‘<span>projeto</span>’ e o arquivo remoto contido no computador de nome
‘<span>estacao</span>’ de mesmo nome.

[^1]: Espaçamento entre o começo da linha e o início do texto

[^2]: Em códigos Python por exemplo não se pode misturar espaços e
    tabulações

[^3]: Abreviação para um comando do GNU/Linux
