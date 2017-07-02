Trabalhando com Janelas {#cha:Trabalhando com janelas}
=======================

O Vim trabalha com o conceito de múltiplos buffers de arquivo. Cada
buffer é um arquivo carregado para edição. Um buffer pode estar visível
ou não, e é possível dividir a tela em janelas, de forma a visualizar
mais de um buffer simultaneamente.

Alternando entre Buffers de arquivo
-----------------------------------

Ao abrir um documento qualquer no Vim o mesmo fica em um buffer. Caso
seja decidido que outro arquivo seja aberto na mesma janela, o documento
inicial irá desaparecer da janela atual cedendo lugar ao mais novo, mas
permanecerá ativo no buffer para futuras modificações.

Para saber quantos documentos estão abertos no momento utiliza-se o
comando <span>*:ls*</span> ou <span>*:buffers*</span>. Esses comandos
listam todos os arquivos que estão referenciados no buffer com suas
respectivas “chaves” de referencia.

Para trocar a visualização do Buffer atual pode-se usar:

         :buffer# ...... Altera para o buffer anterior
         :b2 ........... Altera para o buffer cujo a chave é 2

Para os que preferem atalhos para alternar entre os buffers, é possível
utilizar ‘<span>Ctrl-6</span>’ que tem o mesmo funcionamento do comando
‘`:b#`’

Modos de divisão da janela
--------------------------

Como foi dito acima, é possível visualizar mais de um buffer ao mesmo
tempo, e isso pode ser feito utilizando <span>*tab*</span> ou
<span>*split*</span>.

### Utilizando abas <span>*tab*</span>

A partir do Vim 7 foi disponibilizada a função de abrir arquivos em
abas, portanto é possível ter vários buffers abertos em abas distintas e
alternar entre elas facilmente. Os comandos para utilização das abas
são:

         :tabnew ........... Abre uma nova tab
         :tabprevious ...... Vai para a tab anterior
         :tabnext .......... Vai para a próxima tab

### Utilizando split horizontal

Enquanto os comandos referentes a <span>*tab*</span> deixam a janela
inteira disponível para o texto e apenas cria uma pequena aba na parte
superior, o comando <span>*split*</span> literamente divide a tela atual
em duas para visualização simultânea dos “buffers” (seja ele o mesmo ou
outro diferente). Esse é o split padrão do Vim mas pode ser alterado
facilmente colocando a linha abaixo no seu `~/.vimrc`:

         :set splitright .... split padrão para vertical

### Utilizando split vertical

O split vertical funciona da mesma maneira que o split horizontal, sendo
a unica diferença o modo como a tela é dividida, pois nesse caso a tela
é dividida verticalmente.

Abrindo e fechando janelas 
---------------------------

         Ctrl-w-s ...... Divide a janela horizontalmente (:split)
         Ctrl-w-v ...... Divide a janela verticalmente (:vsplit)
         Ctrl-w-o ...... Faz a janela atual ser a única (:only)
         Ctrl-w-n ...... Abre nova janela (:new)
         Ctrl-w-q ...... Fecha a janela atual (:quit)
         Ctrl-w-c ...... Fecha a janela atual (:close)

Lembrando que o Vim considera todos os arquivos como “buffers” portanto
quando um arquivo é fechado, o que está sendo fechado é a visualização
do mesmo, pois ele continua aberto no “buffer”.

Salvando e saindo
-----------------

É possível salvar todas as janelas facilmente, assim como sair tambem:

         :wall ............. salva todos `write all'
         :qall ............. fecha todos `quit all'

Manipulando janelas 
--------------------

         Ctrl-w-w ......... Alterna entre janelas
         Ctrl-w-j ......... desce uma janela `j'
         Ctrl-w-k ......... sobe  uma janela `k'
         Ctrl-w-l ......... move para a janela da direta `l'
         Ctrl-w-h ......... move para a janela da direta `h'
         Ctrl-w-r ......... Rotaciona janelas na tela
         Ctrl-w-+ ......... Aumenta o espaço da janela atual
         Ctrl-w-- ......... Diminui o espaço da janela atual

Pode-se mapear um atalho para redimensionar janelas com as teclas ‘`+`’
e ‘`-`’.

        :map + <c-w>+
        :map - <c-w>-

File Explorer  {#File Explorer }
--------------

Para abrir o gerenciador de arquivos do Vim use:

         :Vex ............ abre o file explorer verticalmente
         :Sex ............ abre o file explorer em nova janela
         :Tex ............ abre o file explorer em nova aba
         :e .............. abre o file explorer na janela atual
         após abrir chame a ajuda <F1>

Para abrir o arquivo sob o cursor em nova janela coloque a linha abaixo
no seu `~/.vimrc`

         let g:netrw_altv = 1

É possível mapear um atalho “no caso abaixo F2” para abrir o File
Explorer.

         map <F2> <Esc>:Vex<cr>

Ao editar um arquivo no qual há referência a um outro arquivo, por
exemplo: ‘<span>/etc/hosts</span>’, pode-se usar o atalho ‘<span>Ctrl-w
f</span>’ para abri-lo em nova janela, ou ‘<span>gf</span>’ para abri-lo
na janela atual. Mas é importante posicionar o cursor sobre o nome do
arquivo. Veja também mapeamentos na seção [Mapeamentos] página .
