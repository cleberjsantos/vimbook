Um Wiki para o Vim {#cha:Um Wiki para o Vim}
==================

É inegável a facilidade que um Wiki nos traz, os documentos são
indexados e linkados de forma simples. Já pesquisei uma porção de Wikis
e, para uso pessoal recomendo o Potwiki. O “link” do Potwiki é
[este](http://www.vim.org/scripts/script.php?script_id=1018) @PluginPotWiki.
O Potwiki é um Wiki completo para o Vim, funciona localmente embora
possa ser aberto remotamente via ssh[^1]. Para criar um “link” no
Potwiki basta usar WikiNames, são nomes iniciados com letra maiúscula e
que contenham outra letra em maiúsculo no meio.\

Ao baixar o arquivo salve em `~/.vim/plugin`.\

Mais ou menos na linha 53 do Potwiki `~/.vim/plugin/potwiki.vim` você
define onde ele guardará os arquivos, no meu caso
`/home/docs/textos/wiki`. a linha ficou assim:

         call s:default('home',"~/.wiki/HomePage")

Outra forma de indicar a página inicial seria colocar no seu .virmc

         let potwiki_home = "$HOME/.wiki/HomePage"

Como usar {#Como usar}
---------

O Potwiki trabalha com WikiWords, ou seja, palavras iniciadas com letras
em maiúsculo e que tenham outra letra em maiúsculo no meio (sem
espaços). Para iniciar o Potwiki abra o Vim e pressione `\ww`.

         <Leader> é igual a \   - veja :help leader
         \ww  .... abra a sua HomePage
         \wi  .... abre o Wiki index
         \wf  .... segue uma WikiWords (can be used in any buffer!)
         \we  .... edite um arquivo Wiki
         \\   .... Fecha o arquivo
         <CR> .... segue WikiWords embaixo do cursor <CR> é igual a Enter
         <Tab>.... move para a próxima WikiWords
         <BS> .... move para os WikiWords anteriores (mesma página)
         \wr  .... recarrega WikiWords

Salvamento automático para o Wiki  {#Salvamento automático para o Wiki }
----------------------------------

Procure por uma seção <span>*autowrite*</span> no manual do Potwiki

         :help potwiki

O valor que está em zero deverá ficar em 1

         call s:default(`autowrite',0)

Como eu mantenho o meu Wiki oculto “.wiki” criei um “link” para a pasta
de textos

         ln -s ~/.wiki /home/sergio/docs/textos/wiki

Vez por outra entro na pasta `~/docs/textos/wiki` e crio um pacote
<span>tar.gz</span> e mando para “web” como forma de manter um “backup”.

Problemas com codificação de caracteres {#Problemas com codificação de caracteres}
---------------------------------------

Atualmente uso o Ubuntu em casa e ele já usa utf-8. Ao restaurar meu
“backup” do Wiki no Kurumin os caracteres ficaram meio estranhos, daí
fiz:

         baixei o pacote [recode]
         # apt-get install recode

para recodificar caracteres de ‘`utf-8`’ para ‘`iso`’ faça:

         recode -d u8..l1 arquivo

[^1]: Sistema de acesso remoto
