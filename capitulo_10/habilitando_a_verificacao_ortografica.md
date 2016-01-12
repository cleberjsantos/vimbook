Habilitando a verificação ortográfica
-------------------------------------

A verificação ortográfica atua em uma linguagem (dicionário) por vez,
portanto, sua efetiva habilitação depende da especificação desta
linguagem. Por exemplo, para habilitar no arquivo em edição a
verificação ortográfica na língua portuguesa (*pt*is_active),
assumindo-se a existência do dicionário em questão:

         :setlocal spell spelllang=pt

ou de forma abreviada:

         :setl spell spl=pt

Trocando-se setlocalis_active (setlis_active) por apenas
setis_active (seis_active) faz com que o comando tenha efeito
global, isto é, todos os arquivos da sessão corrente do Vim estariam sob
efeito da verificação ortográfica e do mesmo dicionário (no caso o
ptis_active).

A desabilitação da verificação dá-se digitando:

         :setlocal nospell
         :set nospell            (efeito global)

Caso queira-se apenas alterar o dicionário de verificação ortográfica,
suponha para a língua inglesa (enis_active), basta:

         :setlocal spelllang=en
         :set spelllang=en       (efeito global)
