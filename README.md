# Curso de SQLServer
SELECT:
-------------------------------------------------------------------------
    
    -SELECT *DISTINCT* coluna1                                             -> retorna dados únicos e não duplicados 
    -FROM tabela
    
    
    -SELECT *                                                              -> extrai alguns dados específicos da 
    -FROM tabela                                                           coluna dependendo da condição proposta.
    -*WHERE* coluna = ''


    -SELECT *COUNT*(coluna)                                                -> retorna o n° de linhas da coluna selecionada 
    -FROM tabela                                                           de acordo com a condição


    -SELECT *TOP 10* coluna                                                -> seleciona os top 10 ou a quantidade que quiser
    -FROM tabela                                                           da coluna selecionada


    -SELECT coluna                                                         -> ordena a coluna selecionada na condição do
    -FROM tabela                                                           WHERE em ordem crescente ou decrescente 
    -WHERE coluna = ''
    -*ORDER BY* coluna *ASC/DESC*


    -SELECT *                                                              -> encontra o valor entre o mínimo e o máximo
    -FROM tabela                                                           da coluna da tabela selecionada
    -WHERE coluna *between* MIN and MAX


-------------------------------------------------------------------------

