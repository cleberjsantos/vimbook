Introdução
==========

A edição de texto é uma das tarefas mais frequentemente executadas por
seres humanos em ambientes computacionais, em qualquer nível. Usuários
finais, administradores de sistemas, programadores de software,
desenvolvedores <span>*web*</span>, e tantas outras categorias, todos
eles, constantemente, necessitam editar textos.

Usuários finais editam texto para criar documentos, enviar e-mails,
atualizar o blog, escrever recados ou simplesmente trocar mensagens
instantâneas pela internet. Administradores de sistemas editam arquivos
de configuração, criam regras de segurança, editam
<span>*scripts*</span> e manipulam saídas de comandos armazenados em
arquivos de texto. Programadores desenvolvem códigos-fonte e a
documentação de programas essencialmente em editores de texto.
Desenvolvedores <span>*web*</span> interagem com editores de texto para
criarem <span>*layout*</span> e dinâmica de sites.

Tamanha é a frequência e onipresença da tarefa de edição de texto que a
eficiência, flexibilidade e o repertório de ferramentas de editores de
texto tornam-se quesitos críticos para se atingir
<span>*produtividade*</span> e <span>*conforto*</span> na edição de
textos.

Qualquer tarefa de aprendizado requer um certo esforço. Todo programa
introduz novos conceitos, opções e configurações que transformam o
*modus operanti* do usuário. Em princípio, quanto maior o esforço, maior
o benefício. Quem quer apenas escrever textos, pode-se contentar com um
editor básico, cuja as únicas opções são digitar o texto, abrir e salvar
o documento ou pode utilizar um editor que permita pré-configurar ações,
formatar o conteúdo, revisar a ortografia, etc, além da ação básica que
é escrever textos.

Qualquer usuário de computador pode abrir o primeiro tipo de editor e
imediatamente começar a escrever, a curto prazo, sua ação terá
consequências imediatas e não requer conhecimentos adicionais. Por outro
lado, esse usuário terá que fazer esforço para digitar o mesmos
cabeçalho todos os dias.

O outro tipo de editor permite que o usuário pré-configure o cabeçalho
do documento e todos os dias esse trecho já estará digitado. Em
contrapartida, o usuário deve aprender como pré-configurar o editor. O
que requer esforço para aprender a utilizar o programa escolhido. O
benefício somente será observado a médio/longo prazo, quando o tempo
ganho ao utilizar a configuração será superior ao tempo consumido
aprendendo sobre o programa. O “[Vim](http://www.vim.org)”[^1] é um
editor de texto extremamente configurável, criado para permitir a edição
de forma eficiente, tornando-a produtiva e confortável. Também é uma
aprimoração do editor “Vi”, um tradicional programa dos sistemas Unix.
Possui uma série de mudanças em relação a este último. O próprio slogan
do Vim é <span>*Vi IMproved*</span>, ou seja, <span>*Vi
Melhorado*</span>. O Vim é tão conhecido e respeitado entre
programadores, e tão útil para programação, que muitos o consideram uma
verdadeira “IDE (*Integrated Development Environment*, em português,
Ambiente Integrado de Desenvolvimento)”.

Ele é capaz de reconhecer mais de 500 sintaxes de linguagens de
programação e marcação, possui mapeamento para teclas, macros,
abreviações, busca por <span>*<span>Expressões
Regulares</span>*</span>[^2], entre outras facilidades.

A figura [fig:vimedittex] mostra o vim sendo usando para editar o
arquivo o desse livro sobre vim.

![Usando o vim para editar o código em LaTeX](img/vimedittex)

[fig:vimedittex]

O Vim conta com uma comunidade bastante atuante e é, ao lado do
Emacs[^3], um dos editores mais usados nos sistemas GNU/Linux[^4],
embora esteja também disponível em outros sistemas, como o Windows e o
Macintosh.

Instalação do Vim
-----------------

### Instalação no Windows

Há uma versão gráfica do Vim disponível para vários sistemas
operacionais, incluindo o Windows; esta versão pode ser encontrada no
[site oficial](http://www.vim.org/download.php) @SiteOficialDownloads.
Para instalá-lo basta baixar o instalador no link indicado e dispará-lo
com um duplo clique (este procedimento requer privilégios de
administrador).

### Instalação no GNU/Linux

A maioria das distribuições GNU/Linux traz o Vim em seus repositórios,
sendo que é bastante comum o Vim já vir incluído na instalação típica da
distribuição. A forma de instalação preferível depende do Vim:

-   Já vir instalado por <span>*default*</span> – neste caso nada
    precisa ser feito.

-   Estar disponível no repositório, mas não instalado – em
    distribuições derivadas da Debian GNU/Linux[^5], a instalação do Vim
    através dos repositórios é usualmente executada digitando-se
    <span>‘apt-get install vim’</span>[^6] em um <span>*terminal*</span>
    (este procedimento requer privilégios de administrador e,
    tipicamente, conexão com a internet).

    Algumas distribuições GNU/Linux dividem o programa vim em vários
    pacotes. Pacotes adicionais como `gvim`, `vim-enhanced`,
    `vim-phython`[^7], entre outros, representam diferentes versões do
    mesmo aplicativo. O `gvim` é a versão gráfica do Vim e o
    `vim-enhanced` é uma versão do vim compilada com um suporte interno
    ao Python[^8]. A alternativa para resolver esse problema é buscar na
    documentação da distribuição o que significa cada pacote.

-   Não estar disponível no repositório da distribuição – cenário
    <span>*muito*</span> improvável, mas nas sua ocorrência o Vim pode
    ser instalado através da compilação do código-fonte; basta seguir as
    instruções do [site
    oficial](http://www.vim.org/download.php) @SiteOficialDownloads.

Dicas iniciais {#Dicas iniciais}
--------------

Ao longo do livro alguns comandos ou dicas podem estar duplicados, o que
é útil devido ao contexto e também porque o aprendizado por saturação é
um ótimo recurso. Ao perceber uma dica duplicada, antes de reclamar veja
se já sabe o que está sendo passado. Contudo dicas e sugestões serão bem
vindas!

Para abrir um arquivo com Vim digite num terminal:

         vim texto.txt

onde <span>texto.txt</span> é o nome do arquivo que deseja-se criar ou
editar.

Em algumas distribuições, pode-se usar o comando <span>vi</span> ao
invés de <span>vim</span>.

Ajuda integrada
---------------

O Vim possui uma ajuda integrada muito completa, são mais de 100
arquivos somando milhares de linhas. O único inconveniente é não haver
ainda tradução para o português, sendo o inglês seu idioma oficial;
entretanto, as explicações costumam ser sintéticas e diretas, de forma
que noções em inglês seriam suficientes para a compreensão de grande
parte do conteúdo da ajuda integrada.

Obs: No Vim quase todos os comandos podem ser abreviados, no caso
“`help`” pode ser chamado por “`h`” e assim por diante. Um comando só
pode ser abreviado até o ponto em que este nome mais curto não coincida
com o nome de algum outro comando existente. Para chamar a ajuda do Vim
pressione ‘`Esc`’ e em seguida:

         :help .... versão longa, ou
         :h ....... versão abreviada

ou simplesmente ‘`F1`’.

Siga os links usando o atalho ‘`ctrl+]`’, em modo gráfico o clique com o
mouse também funciona, e para voltar use ‘`ctrl+o`’ ou ‘`ctrl+t`’ Para
as situações de desespero pode-se digitar:

         :help!

Quando um comando puder ser abreviado poderá aparecer desta forma:
‘`:so[urce]`’. Deste modo se está indicando que o comando ‘`:source`’
pode ser usado de forma abreviada, no caso ‘`:so`’.

Em caso de erros  {#Em caso de erros }
-----------------

Recarregue o arquivo que está sendo editado pressionando ‘`Esc`’ e em
seguida usando o comando ‘`:e`’. ou simplesmente inicie outro arquivo
ignorando o atual, com o comando ‘`:enew!`’, ou saia do arquivo sem
modifica-lo, com ‘`:q!`’. Pode-se ainda tentar gravar forçado com o
comando ‘`:wq!`’

Como interpretar atalhos e comandos {#Como interpretar atalhos e comandos}
-----------------------------------

A tecla “`<Ctrl>`” é representada na maioria dos manuais e na ajuda pelo
caractere “`^`” circunflexo, ou seja, o atalho `Ctrl-L` aparecerá assim:

         ^L

No arquivo de configuração do Vim, um “`<Enter>`” pode aparecer como:

         <cr>

Para saber mais sobre como usar atalhos no Vim veja a seção
[Mapeamentos] na página  e para ler sobre o arquivo de configuração veja
o capítulo [cha:Como editar preferências no Vim] na página .

Modos de operação {#Modos de operação}
-----------------

A tabela abaixo mostra uma referência rápida para os modos de operação
do Vim, a seguir mais detalhes sobre cada um dos modos.

<span>|l|l|l|</span> **Modo** & **Descrição** & **Atalho** Normal & Para
deletar, copiar, formatar, etc & <span>\<Esc\></span>Inserção &
Prioritariamente, digitação de texto & <span>i,a,I,A,o,O</span>Visual &
Seleção de blocos verticais e linhas inteiras & <span>V, v,
Ctrl-v</span> Comando & Uma verdadeira linguagem de programação &
<span>\<Esc\>:</span>

Em oposição à esmagadora maioria dos editores o Vim é um editor que
trabalha com “modos de operação (modo de inserção, modo normal, modo
visual e etc)”, o que a princípio dificulta a vida do iniciante, mas
abre um universo de possibilidades, pois ao trabalhar com modos
distintos uma tecla de atalho pode ter vários significados,
exemplificando: Em modo normal pressionar ‘<span>dd</span>’ apaga a
linha atual, já em modo de inserção ele irá se comportar como se você
estivesse usando qualquer outro editor, ou seja, irá inserir duas vezes
a letra ‘<span>d</span>’. Em modo normal pressionar a tecla
‘<span>v</span>’ inicia uma seleção visual (use as setas de direção).
Para sair do novo visual `<Esc>`. Como um dos princípios do vim é
agilidade pode-se usar ao invés de setas (em modo normal) as letras
<span>h,l,k,j</span> como se fossem setas:

             k
         h       l
             j

Imagine as letras acima como teclas de direção, a letra ‘<span>k</span>’
é uma seta acima a letra ‘<span>j</span>’ é uma seta abaixo e assim por
diante.

Entrando em modo de edição {#Entrando em modo de edição}
--------------------------

Estando no modo normal, digita-se:

         a .... inicia inserção de texto após o caractere atual
         i .... inicia inserção de texto antes do caractere atual
         A .... inicia inserção de texto no final da linha
         I .... inicia inserção de texto no começo da linha
         o .... inicia inserção de texto na linha abaixo
         O .... inicia inserção de texto na linha acima

Outra possibilidade é utilizar a tecla `<Insert>` para entrar no modo de
inserção de texto antes do caractere atual, ou seja, o mesmo que a tecla
`i`. Uma vez no modo de inserção, a tecla `<Insert>` permite alternar o
modo de digitação de inserção de simples de caracteres para substituição
de caracteres.

Agora começamos a sentir o gostinho de usar o Vim, uma tecla seja
maiúscula ou minúscula, faz muita diferença se você não estiver em modo
de inserção, e para sair do modo de inserção e voltar ao modo normal
sempre use `<Esc>`.

Erros comuns {#sec:Erros comuns}
------------

-   Estando em <span>*<span>modo de inserção</span>*</span> pressionar
    ‘<span>j</span>’ na intenção de rolar o documento, neste caso
    estaremos inserindo simplesmente a letra ‘<span>j</span>’.

-   Estando em <span>*<span>modo normal</span>*</span> acionar
    acidentalmente o “`<Caps Lock>`” e tentar rolar o documento usando a
    letra “`J`”, o efeito é a junção das linhas, aliás um ótimo recurso
    quando a intenção é de fato esta.

-   Em <span>*<span>modo normal</span>*</span> tentar digitar
    <span>*<span>um número seguido de uma palavra</span>*</span> e ao
    perceber que nada está sendo digitado, iniciar o modo de inserção,
    digitando por fim o que se queria, o resultado é que o número que
    foi digitado inicialmente vira um quantificador para o que se
    digitou ao entrar no modo de inserção. A palavra aparecerá repetida
    na quantidade do número digitado. Assim, se você quiser digitar 10
    vezes “`isto é um teste`” faça assim:

             <Esc> ........... se assegure de estar em modo normal
             10 .............. quantificador
             i ............... entra no modo de inserção
             isto é um teste <Enter> <Esc>  

Alguns atalhos úteis…

         Ctrl-O ..... comando do modo normal no modo insert
         i Ctrl-a ... repetir a última inserção
         @: ......... repetir o último comando
         Shift-insert colar texto da área de transferência
         gi ......... modo de inserção no mesmo ponto da última vez
         gv ......... repete seleção visual

Para saber mais sobre repetição de comandos veja o capítulo [Repetição
de comandos], na página .

No Vim, cada arquivo aberto é chamado de `buffer`, ou seja, dados
carregados na memória. Você pode acessar o mesmo <span>*buffer*</span>
em mais de uma janela, bem como dividir a janela em vários
<span>*buffers*</span> distintos o que veremos mais adiante.

[^1]: Vim - <http://www.vim.org>

[^2]: Expressões Regulares -
    <http://guia-er.sourceforge.net/guia-er.html>

[^3]: Emacs - <http://www.gnu.org/software/emacs/>

[^4]: O kernel Linux sem os programas GNU não serviria para muita coisa.

[^5]: Debian GNU/Linux - <http://www.debian.org/index.pt.html>

[^6]: Recomenda-se também instalar a documentação em HTML do Vim:
    <span>‘apt-get install vim-doc’</span>

[^7]: Para ubuntu e Debian

[^8]: O Python (<http://www.python.org>) é uma linguagem de programação
    orientada a objetos muito comum no meio profissional e acadêmico
