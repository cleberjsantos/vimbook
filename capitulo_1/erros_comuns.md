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


