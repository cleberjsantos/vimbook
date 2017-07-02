Folders {#cha:Folders}
=======

<span>*Folders*</span> são como dobras nas quais o Vim esconde partes do
texto, algo assim:

         +-- 10 linhas ---------------------------

Deste ponto em diante chamaremos os <span>*folders*</span> descritos no
manual do Vim como dobras! Quando tiver que manipular grandes
quantidades de texto tente usar dobras, isto permite uma visualização
completa do texto. Um modo de entender rapidamente como funcionam as
dobras no Vim seria criando uma “dobra” para as próximas 10 (dez) linhas
com o comando abaixo:

         zf10j

Você pode ainda criar uma seleção visual

         Shift-v ............ seleção por linha
         j .................. desce linha
         zf ................. cria o folder
         zo ................. abre o folder

Métodos de dobras  {#Métodos de dobras }
------------------

O Vim tem seis modos <span>*fold*</span>, são eles:

-   Sintaxe (<span>*syntax*</span>)

-   Identação (<span>*indent*</span>)

-   Marcas (<span>*marker*</span>)

-   Manual (<span>*manual*</span>)

-   Diferenças (<span>*diff*</span>)

-   Expressões Regulares (<span>*expr*</span>)

Para determinar o tipo de dobra faça

         :set foldmethod=tipo

onde o tipo pode ser um dos tipos listados acima, exemplo:

         :set foldmethod=marker

Outro modo para determinar o método de dobra seria colocando na última
linha do seu arquivo algo assim:

         vim:fdm=marker:fdl=0:

Obs: `fdm` significa <span>*foldmethod*</span>, e `fdl` significa
<span>*foldlevel*</span>. Deve haver um espaço entre a palavra inicial
“vim” e o começo da linha este recurso chama-se <span>*modeline*</span>,
leia mais na seção “[sec:Modelines] modelines” na página .

Manipulando dobras  {#Manipulando dobras }
-------------------

Os principais comandos relativos ao uso de dobras são:

         zo ................ abre a dobra
         zO ................ abre a dobra, recursivamente
         za ................ abre/fecha (alterna) a dobra
         zA ................ abre/fecha (alterna) a dobra,
                             recursivamente
         zR ................ abre todas as dobras do arquivo atual
         zM ................ fecha todas as dobras do arquivo atual
         zc ................ fecha uma dobra
         zC ................ fecha a dobra abaixo do cursor, 
                             recursivamente
         zfap .............. cria uma dobra para o parágrafo `ap'
                             atual
         zf/casa ........... cria uma dobra até a palavra casa
         zf'a .............. cria uma dobra até a marca `a'
         zd ................ apaga a dobra (não o seu conteúdo)
         zj ................ move para o início da próxima dobra
         zk ................ move para o final da dobra anterior
         [z ................ move o cursor para início da dobra
                             aberta
         ]z ................ move o cursor para o fim da dobra aberta
         zi ................ desabilita ou habilita as dobras
         zm, zr ............ diminui/aumenta nível da dobra `fdl'
         :set fdl=0 ........ nível da dobra 0 (foldlevel)
         :set foldcolumn=4 . mostra uma coluna ao lado da numeração

Para abrir e fechar as dobras usando a barra de espaços coloque o trecho
abaixo no seu arquivo de configuração do Vim (`.vimrc`) - veja o
capítulo [cha:Como editar preferências no Vim], página .

         nnoremap <space> @=((foldclosed(line(".")) < 0) ?
                              \ 'zc' : 'zo')<CR>

A barra, `\`, nesse comando representa o particionamento do comando em
mais de uma linha.

Para abrir e fechar as dobras utilizando o clique do mouse no gvim,
basta acrescentar na configuração do seu `.vimrc`:

         set foldcolumn=2

o que adiciona uma coluna ao lado da coluna de enumeração das linhas.

Criando dobras usando o modo visual {#Criando folders usando o modo visual}
-----------------------------------

Para iniciar a seleção visual

         Esc ........ vai para o modo normal
         shift-v .... inicia seleção visual
         j .......... aumenta a seleção visual (desce)
         zf ......... cria a dobra na seleção ativa

Um modo inusitado de se criar dobras é:

         Shift-v ..... inicia seleção visual
         /chapter/-2 . extende a seleção até /chapter -2 linhas
         zf .......... cria a dobra
