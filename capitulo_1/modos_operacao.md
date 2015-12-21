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


