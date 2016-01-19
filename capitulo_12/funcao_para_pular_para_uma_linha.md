### Função para pular para uma linha 

         "ir para linha
         " ir para uma linha específica
         function! GoToLine()
         let ln = inputdialog("ir para a linha...")
         exe ``:'' . ln
         endfunction
         "no meu caso o mapeamento é com Ctrl-l
         "use o que melhor lhe convier
         imap <S-l> <C-o>:call GoToLine()<CR>
         nmap <S-l> :call GoToLine()<CR>


