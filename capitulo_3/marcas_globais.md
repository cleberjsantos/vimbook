Marcas Globais
--------------

Durante a edição de vários arquivos pode-se definir uma marca global com
o comando:

         mA

Onde ‘m’ cria a marca e ‘A’ (maiúsculo) define
uma marca ‘A’ acessível a qualquer momento com o comando:

         'A

Isto fará o Vim dar um salto até a marca ‘A’ mesmo que
esteja em outro arquivo, mesmo que você tenha acabado de fecha-lo. Para
abrir e editar vários arquivos do Vim fazemos:

         vim *.txt ......... abre todos os arquivos 'txt'
         :bn ............... vai para o próximo da lista
         :bp ............... volta para o arquivo anterior
         :ls ............... lista todos os arquivos abertos
         :wn ............... salva e vai para o próximo
         :wp ............... salva e vai para o anterior
