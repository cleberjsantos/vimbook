Registros de buscas "/"
-----------------------

Se desejar inserir em uma substituição uma busca prévia, você poderia
fazer assim em modo de comandos:

         :%s,<Ctrl-r>/,novo-texto,g

Observação: veja que estou trocando o delimitador da busca para deixar
claro o uso do registro de buscas "/". Pode-se usar um registro nomeado
de 'a-z' assim:

        let @a="new"
        :%s/old/\=@a/g ...... substitui 'old' por new
        \=@a ................ faz referência ao registro `a'
