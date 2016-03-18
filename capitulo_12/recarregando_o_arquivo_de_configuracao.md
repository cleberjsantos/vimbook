### Recarregando o arquivo de configuração

Cada alteração no arquivo de configuração do Vim só terá efeito na
próxima vez que você abrir o Vim a menos que você coloque isto dentro do
mesmo

         " recarregar o vimrc
         " Source the .vimrc or _vimrc file, depending on system
         if &term == "win32" || "pcterm" || has("gui_win32")
            map ,v :e $HOME/_vimrc<CR>
            nmap <F12> :<C-u>source ~/_vimrc <BAR> echo "Vimrc recarregado!"<CR>
         else
            map ,v :e $HOME/.vimrc<CR>
            nmap <F12> :<C-u>source ~/.vimrc <BAR> echo "Vimrc recarregado!"<CR>
         endif

Agora basta pressionar “`<F12>`” em modo normal e as alterações passam a
valer instantaneamente, e para chamar o ‘`vimrc`’ basta usar.

         ,v

Os mapeamentos abaixo são úteis para quem escreve códigos HTML, permitem
inserir caracteres reservados do HTML usando uma barra invertida para
proteger os mesmos, o Vim substituirá os “barra alguma coisa” pelo
caractere correspondente.

         inoremap \&amp; &amp;amp;
         inoremap \&lt; &amp;lt;
         inoremap \&gt; &amp;gt;
         inoremap \. &amp;middot;

O termo **inoremap** significa: em modo de inserção não
remapear, ou seja ele mapeia o atalho e não permite que o mesmo seja
remapeado, e o mapeamento só funciona em modo de inserção, isso
significa que um atalho pode ser mapeado para diferentes modos de
operação.\

Veja este outro mapeamento:

         map <F11> <Esc>:set nu!<cr>

Permite habilitar ou desabilitar números de linha do arquivo corrente. A
exclamação ao final torna o comando booleano, ou seja, se a numeração
estiver ativa será desabilitada, caso contrário será ativada. O “`<cr>`”
ao final representa um *Enter*.


