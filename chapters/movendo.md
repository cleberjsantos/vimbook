Movendo-se no Documento {#cha:Movendo-se no Documento}
=======================

A fim de facilitar o entendimento acerca das teclas e atalhos de
movimentação, faz-se útil uma breve recapitulação de conceitos
relacionados. Para se entrar em modo de inserção, estando em modo
normal, pode-se pressionar qualquer uma das teclas abaixo:

         i ..... entra no modo de inserção antes do caractere atual
         I ..... entra no modo de inserção no começo da linha
         a ..... entra no modo de inserção após o caractere atual
         A ..... entra no modo de inserção no final da linha
         o ..... entra no modo de inserção uma linha abaixo
         O ..... entra em modo de inserção uma linha cima
         <Esc> . sai do modo de inserção

Uma vez no modo de inserção todas as teclas são exatamente como nos
outros editores simples, caracteres que constituem o conteúdo do texto
sendo digitado. Para sair do modo de inserção e retornar ao modo normal
digita-se `<Esc>` ou `Ctrl-[`. As letras <span>h</span>, <span>k</span>,
<span>l</span>, <span>j</span> funcionam como setas:

            k
         h     l
            j

ou seja, a letra ‘<span>k</span>’ é usada para subir no texto, a letra
‘<span>j</span>’ para descer, a letra ‘<span>h</span>’ para mover-se
para a esquerda e a letra ‘<span>l</span>’ para mover-se para a direita.
A ideia é que se consiga ir para qualquer lugar do texto sem tirar as
mãos do teclado, sendo portanto alternativas para as setas de
movimentação usuais do teclado. Ao invés de manter os quatro dedos sobre
H, J, K e L, é aconselhável manter o padrão de digitação com o indicador
da mão esquerda sobre a tecla F e o da mão direita sobre a letra J,
sendo que seu indicador da mão direita vai alternar entre a tecla J e H
para a movimentação.

Para ir para linhas específicas ‘<span>*em modo normal*</span>’ digite:

         :n<Enter>  ..... vai para linha `n'
         ngg ............ vai para linha `n'
         nG ............. vai para linha `n'

onde “`n`” corresponde ao número da linha. Para retornar ao modo normal
pressione `<Esc>` ou use `Ctrl-[` (`^[`).

No vim é possível realizar diversos tipos de movimentos, também
conhecidos como saltos no documento. A lista abaixo aponta o comandos de
salto típicos.

         gg .... vai para o início do arquivo
         G ..... vai para o final do arquivo
         0 ..... vai para o início da linha
         ^ ..... vai para o primeiro caractere da linha (ignora 
                 espaços)
         $ ..... vai para o final da linha
         25gg .. salta para a linha 25
         '' .... salta para a linha da última posição em que o cursor
                 estava
         fx .... para primeira ocorrência de x
         tx .... Para ir para uma letra antes de x
         Fx .... Para ir para ocorrência anterior de x
         Tx .... Para ir para uma letra após o último x
         * ..... Próxima ocorrência de palavra sob o cursor
         `' .... salta exatamente para a posição em que o cursor
                 estava
         gd .... salta para declaração de variável sob o cursor
         gD .... salta para declaração (global) de variável sob o 
                 cursor
         w ..... move para o início da próxima palavra
         W ..... pula para próxima palavra (desconsidera hífens)
         E ..... pula para o final da próxima palavra (desconsidera 
                 hifens)
         e ..... move o cursor para o final da próxima palavra
         zt .... movo o cursor para o topo da página
         zm .... move o cursor para o meio da página
         zz .... move a página de modo com que o cursor fique no 
                 centro
         n ..... move o cursor para a próxima ocorrência da busca
         N ..... move o cursor para a ocorrência anterior da busca

Também é possível efetuar saltos e fazer algo mais ao mesmo tempo, a
lista abaixo aponta algumas dessas possibilidades.

         gv .... repete a última seleção visual e posiciona o cursor
                 neste local
         % ..... localiza parênteses correspondente
         o ..... letra `o', alterna extremos de seleção visual
         yG .... copia da linha atual até o final do arquivo
         d$ .... deleta do ponto atual até o final da linha
         gi .... entra em modo de inserção no ponto da última edição
         gf .... abre o arquivo sob o cursor

Para o Vim “<span>*<span>palavras-separadas-por-hífen</span>*</span>”
são consideradas em separado, portanto se você usar, em modo normal
“`w`” para avançar entre as palavras ele pulará uma de cada vez, no
entanto se usar “`W`” em maiúsculo (como visto) ele pulará a
“a-palavra-inteira” :)

         E .... pula para o final de palavras com hifen
         B .... pula palavras com hifen (retrocede)
         W .... pula palavras hifenizadas (começo)

Podemos pular sentenças:

         ) .... pula uma sentença para frente
         ( .... pula uma sentença para trás
         } .... pula um parágrafo para frente
         { .... pula um parágrafo para trás
         y) ... copia uma sentença para frente
         d} ... deleta um parágrafo para frente

Caso tenha uma estrutura como abaixo:

         def pot(x):
            return x**2

E tiver uma referência qualquer para a função `pot` e desejar mover o
cursor até sua definição basta posicionar o cursor sobre a palavra `pot`
e pressionar (em modo normal):

         gd

Se a variável for global, ou seja, estiver fora do documento
(provavelmente em outro) use:

         gD

Quando definimos uma variável tipo

         var = `teste'

e em algum ponto do documento houver referência a esta variável e se
desejar ver seu conteúdo fazemos

         [i

Na verdade o atalho acima lhe mostrará o último ponto onde foi feita a
atribuição àquela variável que está sob o cursor, uma mão na roda para
os programadores de plantão! Observe a barra de status do Vim se o tipo
de arquivo está certo, tipo. Para detalhes sobre como personalizar a
barra de status na seção [Função para barra de status].

         ft=python

a busca por definições de função só funciona se o tipo de arquivo
estiver correto

         :set ft=python

Um mapeamento interessante que facilita a movimentação até linahas que
contenham determinada palavra de um modo bem simples, bastando
pressionar `,f` pode ser feito assim:

    map ,f [I:let nr = input("Which one: ")<Bar>exe "normal " . nr ."[\t"<CR>

Uma vez definido o mapeamento acima e pressionando-se o atalho
associado, que neste caso é `,f` o vim exibirá as uma oppção para pular
para as ocorrências da palavra assim:

        1:  trecho contendo a palavra
        2:  outro trecho contendo a palavra
        Which one: 

outro detalhe para voltar ao último ponto em que você estava

         ''

A maioria dos comandos do Vim pode ser precedida por um quantificador:

         5j ..... desce 5 linhas
         d5j .... deleta as próximas 5 linhas
         k ...... em modo normal sobe uma linha
         5k ..... sobe 5 linhas
         y5k .... copia 5 linhas (para cima)
         w ...... pula uma palavra para frente
         5w ..... pula 5 palavras
         d5w .... deleta 5 palavras
         b ...... retrocede uma palavra
         5b ..... retrocede 5 palavras
         fx ..... posiciona o cursor em ``x''
         dfx .... deleta até o próximo ``x''
         dgg .... deleta da linha atual até o começo do arquivo
         dG ..... deleta até o final do arquivo
         yG ..... copia até o final do arquivo
         yfx .... copia até o próximo ``x''
         y5j .... copia 5 linhas

Paginando {#Paginando}
---------

Para rolar uma página de cada vez (em modo normal)

         Ctrl-f
         Ctrl-b

         :h jumps . ajuda sobre a lista de saltos
         :jumps ... exibe a lista de saltos
         Ctrl-i ... salta para a posição mais recente
         Ctrl-o ... salta para a posição mais antiga
         '0 ....... abre o último arquivo editado
         '1 ....... abre o penúltimo arquivo editado
         gd ....... pula para a definição de uma variável
         } ........ pula para o fim do parágrafo
         10| ...... pula para a coluna 10
         [i ....... pula para definição de variável sob o cursor

Observação: lembre-se

         ^ .... equivale a Ctrl
         ^I ... equivale a Ctrl-I

É possível abrir vários arquivos tipo `vim *.txt`. Editar algum arquivo,
salvar e ir para o próximo arquivo com o comando à seguir:

         :wn

Ou voltar ao arquivo anterior

         :wp

É possível ainda “rebobinar” sua lista de arquivos.

         :rew[wind]

Ir para o primeiro

         :fir[st]

Ou para o último

         :la[st]

Usando marcas {#sec:UsandoMarcas}
-------------

As marcas são um meio eficiente de se pular para um local no arquivo.
Para criar uma, estando em modo normal faz-se:

         ma

Onde ‘<span>m</span>’ indica a criação de uma marca e ‘<span>a</span>’ é
o nome da marca. Para pular para a marca ‘<span>a</span>’:

         `a

Para voltar ao ponto do último salto:

         ''

Para deletar de até a marca ‘<span>a</span>’ (em modo normal):

         d'a

### Marcas globais

Durante a edição de vários arquivos pode-se definir uma marca global com
o comando:

         mA

Onde ‘<span>m</span>’ cria a marca e ‘<span>A</span>’ (maiúsculo) define
uma marca ‘<span>A</span>’ acessível a qualquer momento com o comando:

         'A

Isto fará o Vim dar um salto até a marca ‘<span>A</span>’ mesmo que
esteja em outro arquivo, mesmo que você tenha acabado de fecha-lo. Para
abrir e editar vários arquivos do Vim fazemos:

         vim *.txt ......... abre todos os arquivos `txt'
         :bn ............... vai para o próximo da lista
         :bp ............... volta para o arquivo anterior
         :ls ............... lista todos os arquivos abertos
         :wn ............... salva e vai para o próximo
         :wp ............... salva e vai para o prévio
