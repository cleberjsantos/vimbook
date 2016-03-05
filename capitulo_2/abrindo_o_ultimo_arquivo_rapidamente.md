Abrindo o último arquivo rapidamente
------------------------------------

O Vim guarda um registro para cada arquivo editado veja mais no capítulo
[Registros] na página .

         '0 ........ abre o último arquivo editado
         '1 ........ abre o penúltimo arquivo editado
         Ctrl-6 .... abre o arquivo alternativo (booleano)

Bom, já que abrimos o nosso último arquivo editado com o comando

         `0

podemos, e provavelmente o faremos, editar no mesmo ponto em que
estávamos editando da última vez:

         gi

Pode-se criar um ‘`alias`’[^3] para que ao abrir o vim o
mesmo abra o último arquivo editado:
‘`alias lvim="vim -c \"normal '0\""`’. No capítulo [cha:Buscas e
substituições] página você encontra mais dicas de edição.


