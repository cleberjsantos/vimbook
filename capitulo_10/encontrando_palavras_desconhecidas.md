Comandos relativos à verificação ortográfica
--------------------------------------------

### Encontrando palavras desconhecidas

Muito embora o verificador ortográfico cheque imediatamente cada palavra
digitada, sinalizando-a ao usuário caso não a reconheça, às vezes é mais
apropriado realizar a verificação ortográfica do documento por inteiro.
O Vim dispõe de comandos específicos para busca e movimentação em
palavras grafadas incorretamente (desconhecidas) no escopo do documento,
dentre eles:
```
]s ..... vai para a próxima palavra desconhecida
[s ..... como o ]s, mas procura no sentido oposto
```
Ambos os comandos aceitam um prefixo numérico, que indica a quantidade
de movimentações (buscas). Por exemplo, o comando 3]s vai
para a *terceira* palavra desconhecida a partir da posição
atual.
