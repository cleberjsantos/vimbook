Transcrição de capítulos
========================

* Clone o repositório

`git clone https://github.com/cassiobotaro/vimbook.git`

* Crie seu feature-branch

`git checkout -b capitulo-x`

* Atribua a issue correspondente ao capítulo escolhido a seu usuário.

[Issues](https://github.com/cassiobotaro/vimbook/issues)

* Crie um diretório para o capítulo na raiz do projeto no formato `capitulo_n` (exemplo `capitulo_15`).

* Adicione o capítulo ao sumário.

[SUMMARY](SUMMARY.md)

* Envie PR do capítulo.

Os [capítulos](https://github.com/cassiobotaro/vimbook/tree/master/chapters) originais se encontram em formato markdown, com alguns problemas de formatação pois foram diretamente gerados à partir do .tex.

*Por favor remova as tags span encontradas.*

Para auxiliar a transcrição, a última versão pdf gerada à partir do .tex está disponível para [download](https://github.com/cassiobotaro/vimbook/blob/master/vimbook-31-08-2009.pdf).


Outros
======

É muito bem vindo correções de ortografia, erros de digitação e outras coisas.

Quando aceito o PR, uma nova versão do livro é gerada automaticamente.


Dicas
-----

* Substituir padrão *LaTex* de itálico (`{\em Texto}`) pelo padrão markdown (`*Texto*`)
```
:%s/{\\em \([^}]*\)}/*\1*/g
```
* Substituir o padrão *LaTex* de título (`\section{Título}`) pelo título normal (`Título`)
```
:%s/\\section{\([^}]*\)}/\1/g
```
* Substituir o padrão *LaTeX* de subtítulo (`\subsection{SubTítulo}`) pelo padrão markdown (`### SubTítulo`)
```
:%s/\\subsection{\([^}]*\)}/### \1/g
```
* Substituir o padrão *LaTeX* de link (`\href{link}{texto}`) pelo padrão markdown (`[texto](link)`)
```
:%s/\\href{\([^}]*\)}{\([^}]*\)}/[\2](\1)/g
```
* Substituir o padrão *LaText* de fonte diferenciada (`{\tt texto}`) pelo padrão markdown de highlighting (``texto``)
```
:%s/{\\tt \([^}]*\)}/`\1`/g
```
