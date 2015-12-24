Salvando Sessões de Trabalho {#cha:Salvando Sessões de Trabalho}
============================

Suponha a situação em que um usuário está trabalhando em um projeto no
qual vários arquivos são editados simultaneamente; quatro arquivos estão
abertos, algumas macros foram criadas e variáveis que não constam no
`vimrc` foram definidas. Em uma situação normal, se o Vim for fechado a
quase totalidade dessas informações se perde[^1]; para evitar isto uma
sessão pode ser criada, gerando-se um “retrato do estado atual”, e então
restaurada futuramente pelo usuário—na prática é como se o usuário não
tivesse saído do editor.

Uma sessão do Vim guarda, portanto, uma série de informações sobre a
edição corrente, de modo a permitir que o usuário possa restaurá-la
quando desejar. Sessões são bastante úteis, por exemplo, para se
alternar entre diferentes projetos, carregando-se rapidamente os
arquivos e definições relativas a cada projeto.

O que uma sessão armazena?
--------------------------

Uma sessão é composta das seguintes informações:

-   Mapeamentos globais

-   Variáveis globais

-   Arquivos abertos incluindo a lista de <span>*buffers*</span>

-   Diretório corrente (<span>:h curdir</span>)

-   Posição e tamanho das janelas (o <span>*layout*</span>)

Criando sessões {#sec:Criando sessões}
---------------

Sessões são criadas através do comando `:mksession`:

         :mks[ession] sessao.vim .... cria a sessão e armazena-a em sessao.vim
         :mks[ession]! sessao.vim ... salva a sessão e sobrescreve-a em sessao.vim

Restaurando sessões
-------------------

Após gravar sessões, elas podem ser carregadas ao iniciar o Vim:

         vim -S sessao.vim

ou então de dentro do próprio Vim (no modo de comando):

         :so sessao.vim

Após restaurar a sessão, o nome da sessão corrente é acessível através
de uma variável interna “`v:this_session`”; caso queira-se exibir na
linha de comando o nome da sessão ativa (incluindo o caminho), faz-se:

         :echo v:this_session

Podemos fazer mapeamentos para atualizar a sessão atual e exibir
detalhes da mesma:

         "mapeamento para gravar sessão
         nmap <F4> :wa<Bar>exe "mksession! " . v:this_session<CR>:so ~/sessions/

         "mapeamento para exibir a sessão ativa
         map <s-F4> <esc>:echo v:this_session<cr>

`Viminfo` {#sec:Viminfo}
---------

Se o Vim for fechado e iniciado novamente, normalmente perderá uma
porção considerável de informações. A diretiva <span>viminfo</span> pode
ser usada para memorizar estas informações.

-   Histórico da linha de comando

-   Histórico de buscas

-   Histórico de entradas <span>*input-line history*</span>

-   Conteúdo de registros não vazios

-   Marcas de vários arquivos

-   Último padrão de busca/substituição

-   A lista de <span>*buffers*</span>

-   Variáveis globais

Deve-se colocar no arquivo de configuração algo como:

    set viminfo=%,'50,\"100,/100,:100,n

Algumas opões da diretiva <span>viminfo</span>:

!

:   Quando incluído salva e restaura variáveis globais (variáveis com
    letra maiúscula) e que não contém letras em minúsculo como
    MANTENHAISTO.

"

:   Número máximo de linhas salvas para cada registro.

%

:   Quando incluído salva e restaura a lista de <span>*buffers*</span>.
    Caso o Vim seja iniciado com um nome como argumento, a lista de
    <span>*buffers*</span> não é restaurada. <span>*Buffers*</span> sem
    nome e <span>*buffers*</span> de ajuda não são armazenados no
    <span>viminfo</span>.

’

:   Número máximo de arquivos recém editados.

/

:   Máximo de itens do histórico de buscas.

:

:   Máximo de itens do histórico da linha de comando

\<

:   Número máximo de linhas salvas por cada registro, se zero os
    registros não serão salvos. Quando não incluído, todas as linhas são
    salvas.

Para ver mais opções sobre o arquivo ‘<span>viminfo</span>’ leia
‘<span>:h viminfo</span>’. Pode-se também usar um arquivo de “Sessão”. A
diferença é que ‘<span>viminfo</span>’ não depende do local de trabalho
(escopo). Quando o arquivo ‘<span>viminfo</span>’ existe e não está
vazio, as informações novas são combinadas com as existentes. A opção
‘<span>viminfo</span>’ é uma string contendo informações sobre o que
deve ser armazenado, e contém limites de o quanto vai ser armazenado
para cada item.

[^1]: Algumas informações, no entanto, são automaticamente armazenadas
    no arquivo <span>viminfo</span>; veja <span>:h viminfo</span>
