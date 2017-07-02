Verificação Ortográfica {#cha:vero}
=======================

O Vim possui um recurso nativo de verificação ortográfica
(<span>*spell*</span>) em tempo de edição, apontando palavras e
expressões desconhecidas—usualmente erros de grafia—enquanto o usuário
as digita.

Basicamente, para cada palavra digitada o Vim procura por sua grafia em
um dicionário. Não encontrando-a, a palavra é marcada como desconhecida
(sublinhando-a ou alterando sua cor), e fornece ao usuário mecanismos
para <span>*corrigi-la*</span> (através de sugestões) ou
<span>*cadastrá-la*</span> no dicionário caso esteja de fato grafada
corretamente.

Habilitando a verificação ortográfica
-------------------------------------

A verificação ortográfica atua em uma linguagem (dicionário) por vez,
portanto, sua efetiva habilitação depende da especificação desta
linguagem. Por exemplo, para habilitar no arquivo em edição a
verificação ortográfica na língua portuguesa (<span>*pt*</span>),
assumindo-se a existência do dicionário em questão:

         :setlocal spell spelllang=pt

ou de forma abreviada:

         :setl spell spl=pt

Trocando-se <span>setlocal</span> (<span>setl</span>) por apenas
<span>set</span> (<span>se</span>) faz com que o comando tenha efeito
global, isto é, todos os arquivos da sessão corrente do Vim estariam sob
efeito da verificação ortográfica e do mesmo dicionário (no caso o
<span>pt</span>).

A desabilitação da verificação dá-se digitando:

         :setlocal nospell
         :set nospell            (efeito global)

Caso queira-se apenas alterar o dicionário de verificação ortográfica,
suponha para a língua inglesa (<span>en</span>), basta:

         :setlocal spelllang=en
         :set spelllang=en       (efeito global)

### Habilitação automática na inicialização

Às vezes torna-se cansativo a digitação explícita do comando de
habilitação da verificação ortográfica sempre quando desejada. Seria
conveniente se o Vim habilitasse automaticamente a verificação para
aqueles tipos de arquivos que comumente fazem uso da verificação
ortográfica, como por exemplo arquivos “texto”. Isto é possível
editando-se o arquivo de configuração do Vim <span>.vimrc</span> (veja
Cap. [cha:Como editar preferências no Vim]) e incluindo as seguintes
linhas:

         autocmd Filetype text setl spell spl=pt
         autocmd BufNewFile,BufRead *.txt setl spell spl=pt

Assim habilita-se automaticamente a verificação ortográfica usando o
dicionário da língua portuguesa (<span>pt</span>) para arquivos do tipo
<span>texto</span> e os terminados com a extensão <span>.txt</span>.
Mais tecnicamente, diz-se ao Vim para executar o comando
`setl spell spl=pt` sempre quando o tipo do arquivo
(<span>Filetype</span>) for <span>text</span> (texto) ou quando um
arquivo com extensão <span>.txt</span> for carregado
(<span>BufRead</span>) ou criado (<span>BufNewFile</span>).

O dicionário de termos
----------------------

A qualidade da verificação ortográfica do Vim está diretamente ligada à
completude e corretude do dicionário da linguagem em questão.
Dicionários pouco completos são inconvenientes à medida que acusam falso
positivos em demasia; pior, dicionários contendo palavras grafadas
incorretamente, além de acusarem falso positivos, induzem o usuário ao
erro ao sugerirem grafias erradas.

É razoavelmente comum o Vim já vir instalado com dicionários de relativa
qualidade para algumas linguagens (ao menos inglês, habitualmente).
Entretanto, ainda é raro para a maioria das instalações do Vim trazer
por <span>*default*</span> um dicionário realmente completo e atualizado
da língua portuguesa. A próxima seção sintetiza, pois, os passos para a
instalação de um excelente—e disponível livremente—dicionário de
palavras para a língua portuguesa.

### Dicionário português segundo o acordo ortográfico

A equipe do projeto <span>BrOffice.org</span> e seus colaboradores
mantêm e disponibilizam livremente um grandioso dicionário de palavras
da língua portuguesa. Além do expressivo número de termos, o dicionário
contempla as mudanças ortográficas definidas pelo <span>*Acordo
Ortográfico*</span> @wiki:acordo_ortografico que entraram em vigor no
início de 2009.

A instalação envolve três passos, são eles:

1.  obtenção do dicionário através do site <span>BrOffice.org</span>;

2.  conversão para o formato interno de dicionário do Vim; e

3.  instalação dos arquivos resultantes.

#### Obtenção do dicionário

O dicionário pode ser obtido no [site do
br.office.org](http://www.broffice.org/verortografico/baixar) @DicionarioBroffice.
O arquivo baixado encontra-se compactado no formato <span>Zip</span>,
bastando portanto descompactá-lo com qualquer utilitário compatível com
este formato, por exemplo, o comando <span>unzip</span>.

#### Conversão do dicionário

Após a descompactação, os arquivos `pt_BR.aff` e `pt_BR.dic`, extraídos
no diretório corrente[^1], serão usados para a criação dos dicionários
no formato interno do Vim[^2]. A conversão propriamente dita é feita
pelo próprio Vim através do comando <span>mkspell</span>:

1.  Carrega-se o Vim a partir do diretório onde foram extraídos
    `pt_BR.aff` e `pt_BR.dic`

2.  O comando <span>mkspell</span> é então executado como:

             :mkspell pt pt_BR

O Vim então gera um arquivo de dicionário da forma
`pt.<codificação>.spl`, onde `<codificação>` é a codificação de
caracteres do sistema, normalmente `utf-8` ou `latin1`; caso queira-se
um dicionário em uma codificação diferente da padrão será preciso
ajustar a variável <span>encoding</span> antes da invocação do comando
<span>mkspell</span>:

         :set encoding=<codificação>
         :mkspell pt pt_BR

#### Instalação do(s) dicionário(s) gerado(s)

Finalmente, o dicionário gerado—ou os dicionários, dependendo do uso ou
não de codificações diferentes—deve ser copiado para o subdiretório
<span>spell/</span> dentro de qualquer caminho (diretório) que o Vim
“enxergue”. A lista de caminhos lidos pelo Vim encontra-se na variável
<span>runtimepath</span>, que pode ser inspecionada através de:

         :set runtimepath

É suficiente então copiar o dicionário `pt.<codificação>.spl` para o
subdiretório <span>spell/</span> em qualquer um dos caminhos listados
através do comando mostrado.

Comandos relativos à verificação ortográfica
--------------------------------------------

### Encontrando palavras desconhecidas

Muito embora o verificador ortográfico cheque imediatamente cada palavra
digitada, sinalizando-a ao usuário caso não a reconheça, às vezes é mais
apropriado realizar a verificação ortográfica do documento por inteiro.
O Vim dispõe de comandos específicos para busca e movimentação em
palavras grafadas incorretamente (desconhecidas) no escopo do documento,
dentre eles:

         ]s ..... vai para a próxima palavra desconhecida
         [s ..... como o ]s, mas procura no sentido oposto

Ambos os comandos aceitam um prefixo numérico, que indica a quantidade
de movimentações (buscas). Por exemplo, o comando <span>3]s</span> vai
para a <span>*terceira*</span> palavra desconhecida a partir da posição
atual.

### Tratamento de palavras desconhecidas

Há basicamente duas operações possíveis no tratamento de uma palavra
apontada pelo verificador ortográfico do Vim como desconhecida:

1.  <span>**corrigi-la**</span> – identificando o erro com ou sem o
    auxílio das sugestões do Vim.

2.  <span>**cadastrá-la no dicionário**</span> – ensinando o Vim a
    reconhecer sua grafia.

Assume-se nos comandos descritos nas seções a seguir que o cursor do
editor encontra-se sobre a palavra marcada como desconhecida.

#### Correção de palavras grafadas incorretamente

É possível que na maioria das vezes o usuário perceba qual foi o erro
cometido na grafia, de forma que o próprio possa corrigi-la sem auxílio
externo. No entanto, algumas vezes o erro não é evidente, e sugestões
fornecidas pelo Vim podem ser bastante convenientes. Para listar as
sugestões para a palavra em questão executa-se:

         z= ..... solicita sugestões ao verificador ortográfico

Se alguma das sugestões é válida – as mais prováveis estão nas primeiras
posições – então basta digitar seu prefixo numérico e pressionar
`<Enter>`. Se nenhuma sugestão for adequada, basta simplesmente
pressionar `<Enter>` e ignorar a correção.

#### Cadastramento de novas palavras no dicionário

Por mais completo que um dicionário seja, eventualmente palavras,
especialmente as de menor abrangência, terão que ser cadastradas a fim
de aprimorar a exatidão da verificação ortográfica. A manutenção do
dicionário dá-se pelo cadastramento e retirada de palavras:

         zg ..... adiciona a palavra no dicionário
         zw ..... retira a palavra no dicionário, marcando-a como 
                  `desconhecida'

[^1]: Eventualmente, dependendo da versão do pacote de correção
    ortográfica, os arquivos de dicionário podem ser extraídos no
    subdiretório <span>dictionaries</span> ou outro qualquer.

[^2]: O formato interno de dicionário do Vim assegura melhor desempenho,
    em termos de agilidade e consumo de memória, quando a verificação
    ortográfica do editor encontra-se em operação.
