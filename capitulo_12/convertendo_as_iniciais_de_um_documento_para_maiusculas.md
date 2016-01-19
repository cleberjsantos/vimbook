### Convertendo as iniciais de um documento para maiúsculas 

         " MinusculasMaiusculas: converte a primeira letra de cada
         " frase para MAIÚSCULAS
         nmap ,mm :%s/\C\([.!?][])"']*\($\|[ ]\)\_s*\)\(\l\)/\1\U\3/g<CR>
         " Caso queira confirmação coloque uma letra ``c'' no final da 
         " linha acima:
         " (...) \3/gc<CR>


