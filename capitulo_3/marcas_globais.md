Marcas Globais
--------------

Durante a edição de vários arquivos pode-se definir uma marca global com
o comando:

         mA

Onde ‘<span>m</span>’ cria a marca e ‘<span>A</span>’ (maiúsculo) define
uma marca ‘<span>A</span>’ acessível a qualquer momento com o comando:

         'A

Isto fará o Vim dar um salto até a marca ‘<span>A</span>’ mesmo que
esteja em outro arquivo, mesmo que você tenha acabado de fecha-lo. Para
abrir e editar vários arquivos do Vim fazemos:

         vim *.txt ......... abre todos os arquivos `txt'
         :bn ............... vai para o próximo da lista
         :bp ............... volta para o arquivo anterior
         :ls ............... lista todos os arquivos abertos
         :wn ............... salva e vai para o próximo
         :wp ............... salva e vai para o prévio
