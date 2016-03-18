### Função para gerar backup

A função abaixo é útil para ser usada quando você vai editar um arquivo
gerando modificações significativas, assim você poderá restaurar o
backup se necessário

         " A mapping to make a backup of the current file.
         fun! WriteBackup()
            let fname = expand("%:p") . "__" . strftime("%d-%m-%Y--%H.%M.%S")
            silent exe ":w " . fname
            echo "Wrote " . fname
         endfun
         nnoremap <Leader>ba :call WriteBackup()<CR>

O atalho “*<leader>*” em geral é a barra invertida
`\`, na dúvida “*:help <leader>*”.


